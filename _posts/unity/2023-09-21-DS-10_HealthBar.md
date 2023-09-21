---
layout: single
title:  "유니티 다크소울 따라만들기 ch_10 체력바"
categories: 
    - Unity
tag: [Unity, DarkSouls]
published: true

author_profile: true # 옆에뜨는 프로파일

search: true #검색해도 안뜨게함

date: 2023-09-21
last_modified_at: 2023-09-21

---

## 체력바 추가

canvus에 Slider 컴포넌트를 통해 체력바를 추가함.

![image](https://github.com/novicehog/comments/assets/131991619/9e3031db-60e0-4fd7-934a-b279e5451d1f)

![image](https://github.com/novicehog/comments/assets/131991619/c785f932-3db7-403b-b6a1-f347ade06d77)

![image](https://github.com/novicehog/comments/assets/131991619/d535a78d-1626-4369-b7c4-93b0f64bbf49)

<br>

## HealthBar 스크립트 추가

slider의 수치를 조정하는 HealthBar스크립트를 추가해준다.

```c#
using UnityEngine.UI;

public class HealthBar : MonoBehaviour
{
    public Slider slider;
    private void Start()
    {
        slider = GetComponent<Slider>();
    }
    public void SetMaxHealth(int maxHealth)
    {
        slider.maxValue = maxHealth;
        slider.value = maxHealth;
    }

    public void SetCurrentHealth(int health)
    {
        slider.value = health;
    }
}
```

<br>

Health Bar에 스크립트를 추가해준다.

![image](https://github.com/novicehog/comments/assets/131991619/9c8fb289-7846-41ca-b541-6b702517ac57)

<br>

## PlayerStats 스크립트 추가

플레이어 능력치와, 데미지 처리를 구현하는 PlayerStats스크립트를 추가한다.

```c#
public class PlayerStats : MonoBehaviour
{
    public int healthLevel = 10;
    public int maxHealth;
    public int currentHealth;

    public HealthBar healthbar;

    AnimatorHandler animatorHandler;

    private void Awake()
    {
        animatorHandler = GetComponentInChildren<AnimatorHandler>();
    }

    private void Start()
    {
        maxHealth = SetMaxHealthFromHealthLevel();
        currentHealth = maxHealth;
        healthbar.SetMaxHealth(maxHealth);
    }

    private int SetMaxHealthFromHealthLevel()
    {
        maxHealth = healthLevel * 10;
        return maxHealth;
    }

    public void TakeDamage(int damage)
    {
        currentHealth = currentHealth - damage;

        healthbar.SetCurrentHealth(currentHealth);

        animatorHandler.PlayTargetAnimation("Damage_01", true);

        if(currentHealth <= 0)
        {
            currentHealth = 0;
            animatorHandler.PlayTargetAnimation("Dead_01", true);
        }
    }
}
```


## PlayerDamage 스크립트

플레이어에게 데미지를 가하는 간단한 스크립트를 만든다.

```c#
public class PlayerDamage : MonoBehaviour
{
    public int damage = 25;
    private void OnTriggerEnter(Collider other)
    {
        PlayerStats playerStats = other.GetComponent<PlayerStats>();

        if(playerStats != null )
        {
            playerStats.TakeDamage(damage);
        }
    }
}
```

<br>

이 스크립트를 아무 오브젝트에 넣고 isTrigger를 활성화해준다.

