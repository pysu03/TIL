### 예제를 통한 상속 [실습]
- Unit (Marine, Medic, DropShip)
- Marine   - 4기 생성
- Medic    - 2기 생성
- DropShip 생성
- 6명을 태워서 특정 지점을 공격하러 가는 시나리오
```python
class Unit(object):
    def __init__(self, damage, life):
        self.utype  = self.__class__.__name__
        self.damage = damage
        self.life   = life
    def unitInfo(self):
        print('타입 {}'.format(self.utype))
        print('공격력 {}'.format(self.damage))
        print('생명력 {}'.format(self.life))
    def attack(self):
        pass


class Marine(Unit):
    def __init__(self, damage, life, offenseUpgrade, defenseUpgrade):
        super().__init__(damage, life)
        self.offenseUpgrade = offenseUpgrade
        self.defenseUpgrade = defenseUpgrade
    def unitInfo(self):
        super().unitInfo()
        print('공격력 업그레이드 {}'.format(self.offenseUpgrade))
        print('방어력 업그레이드 {}'.format(self.defenseUpgrade))
    def attack(self):
        print('마린 공격개시.... 땅땅')
    def stimpack(self):
        if self.life > 50:
            self.damage *= 1.5
            self.life   -= 10
            print('마린 stimpack 사용')
        else:
            print('생명력이 낮아 stimpack 사용 불가!!')


class Medic(Unit):
    def __init__(self, damage, life, defenseUpgrade):
        super().__init__(damage, life)
        self.defenseUpgrade = defenseUpgrade
    def unitInfo(self):
        super().unitInfo()
        print('방어력 업그레이드 {}'.format(self.defenseUpgrade))
    def attack(self):
        print('메딕이 마린을 치료합니다.')


class DropShip(Unit):
    def __init__(self, damage, life, defenseUpgrade):
        super().__init__(damage, life)
        self.dedenseUpgrade = defenseUpgrade
    def unitInfo(self):
        super().unitInfo()
        print('방어력 업그레이드 {}'.format(self.defenseUpgrade))
    def attack(self):
        print('목표지점으로 이동합니다.')
    def board(self, unitType):
        self.unitType = unitType
        print('부대원을 태웠습니다.')
    def drop(self):
        print('모든 부대원(Unit)이 DropShip에서 내립니다.')
        return self.unitType
```