---
title: Do składowej wystąpienia klasy nie można odwołać się z obrębu udostępnionej metody lub udostępnionego inicjatora składowej bez jawnego wystąpienia klasy
ms.date: 07/20/2015
f1_keywords:
- vbc30369
- bc30369
helpviewer_keywords:
- Shared
- BC30369
ms.assetid: 39d9466b-c1f3-4406-91a5-3d6c52d23a3d
ms.openlocfilehash: a2a5ab99ff68e6dce783a2fd986ee6e8c15ae858
ms.sourcegitcommit: 3094dcd17141b32a570a82ae3f62a331616e2c9c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/01/2019
ms.locfileid: "71701175"
---
# <a name="cannot-refer-to-an-instance-member-of-a-class-from-within-a-shared-method-or-shared-member-initializer-without-an-explicit-instance-of-the-class"></a>Do składowej wystąpienia klasy nie można odwołać się z obrębu udostępnionej metody lub udostępnionego inicjatora składowej bez jawnego wystąpienia klasy
Podjęto próbę odwołania się do nieudostępnionego elementu członkowskiego klasy z procedury wspólnej. Poniższy przykład demonstruje takie sytuacje.  
  
```vb  
Class sample  
    Public x as Integer  
    Public Shared Sub setX()  
        x = 10  
    End Sub  
End Class  
```  
  
 W poprzednim przykładzie instrukcja przypisania `x = 10` generuje ten komunikat o błędzie. Wynika to z faktu, że wspólna procedura próbuje uzyskać dostęp do zmiennej wystąpienia.  
  
 Zmienna `x` jest członkiem wystąpienia, ponieważ nie jest zadeklarowana jako [udostępniona](../../../visual-basic/language-reference/modifiers/shared.md). Każde wystąpienie klasy `sample` zawiera własną indywidualną zmienną `x`. Gdy jedno wystąpienie ustawia lub zmienia wartość `x`, nie ma wpływu na wartość `x` w żadnym innym wystąpieniu.  
  
 Jednak procedura `setX` jest `Shared` między wszystkimi wystąpieniami klasy `sample`. Oznacza to, że nie jest on skojarzony z jednym wystąpieniem klasy, ale raczej działa niezależnie od poszczególnych wystąpień. Ponieważ nie ma połączenia z określonym wystąpieniem, `setX` nie może uzyskać dostępu do zmiennej wystąpienia. Musi działać tylko w przypadku zmiennych `Shared`. Gdy `setX` ustawia lub zmienia wartość zmiennej udostępnionej, Nowa wartość jest dostępna dla wszystkich wystąpień klasy.  
  
 **Identyfikator błędu:** BC30369  
  
## <a name="to-correct-this-error"></a>Aby poprawić ten błąd  
  
1. Zdecyduj, czy element członkowski ma być współużytkowany między wszystkimi wystąpieniami klasy, czy dla każdego wystąpienia.  
  
2. Jeśli chcesz, aby jedna kopia elementu członkowskiego była współdzielona między wszystkimi wystąpieniami, Dodaj słowo kluczowe `Shared` do deklaracji elementu członkowskiego. Zachowaj słowo kluczowe `Shared` w deklaracji procedury.  
  
3. Jeśli każde wystąpienie ma mieć własną indywidualną kopię elementu członkowskiego, nie należy określać `Shared` dla deklaracji elementu członkowskiego. Usuń słowo kluczowe `Shared` z deklaracji procedury.  
  
## <a name="see-also"></a>Zobacz także

- [Shared](../../../visual-basic/language-reference/modifiers/shared.md)
