---
title: Nie można odwołać się do elementu członkowskiego wystąpienia klasy z poziomu wspólnej metody lub udostępnionego inicjatora składowej bez jawnego wystąpienia klasy
ms.date: 07/20/2015
f1_keywords:
- vbc30369
- bc30369
helpviewer_keywords:
- Shared
- BC30369
ms.assetid: 39d9466b-c1f3-4406-91a5-3d6c52d23a3d
ms.openlocfilehash: 9b388685299469d5865d57b698e3a66de912fa84
ms.sourcegitcommit: d7c298f6c2e3aab0c7498bfafc0a0a94ea1fe23e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/10/2019
ms.locfileid: "72250205"
---
# <a name="cannot-refer-to-an-instance-member-of-a-class-from-within-a-shared-method-or-shared-member-initializer-without-an-explicit-instance-of-the-class"></a>Nie można odwołać się do elementu członkowskiego wystąpienia klasy z poziomu wspólnej metody lub udostępnionego inicjatora składowej bez jawnego wystąpienia klasy

Podjęto próbę odwołania się do nieudostępnionego elementu członkowskiego klasy z procedury wspólnej. Poniższy przykład ilustruje taką sytuację:
  
```vb  
Class Sample
    Public x as Integer  
    Public Shared Sub SetX()
        x = 10  
    End Sub  
End Class  
```  
  
 W poprzednim przykładzie instrukcja przypisania `x = 10` generuje ten komunikat o błędzie. Wynika to z faktu, że wspólna procedura próbuje uzyskać dostęp do zmiennej wystąpienia.  
  
 Zmienna `x` jest członkiem wystąpienia, ponieważ nie jest zadeklarowana jako [udostępniona](../modifiers/shared.md). Każde wystąpienie klasy `Sample` zawiera własną indywidualną zmienną `x`. Gdy jedno wystąpienie ustawia lub zmienia wartość `x`, nie ma wpływu na wartość `x` w żadnym innym wystąpieniu.
  
 Jednak procedura `SetX` jest `Shared` między wszystkimi wystąpieniami klasy `Sample`. Oznacza to, że nie jest on skojarzony z jednym wystąpieniem klasy, ale raczej działa niezależnie od poszczególnych wystąpień. Ponieważ nie ma połączenia z określonym wystąpieniem, `setX` nie może uzyskać dostępu do zmiennej wystąpienia. Musi działać tylko w przypadku zmiennych `Shared`. Gdy `SetX` ustawia lub zmienia wartość zmiennej udostępnionej, Nowa wartość jest dostępna dla wszystkich wystąpień klasy.
  
 **Identyfikator błędu:** BC30369
  
## <a name="to-correct-this-error"></a>Aby poprawić ten błąd
  
1. Zdecyduj, czy element członkowski ma być współużytkowany między wszystkimi wystąpieniami klasy, czy dla każdego wystąpienia.

2. Jeśli chcesz, aby jedna kopia elementu członkowskiego była współdzielona między wszystkimi wystąpieniami, Dodaj słowo kluczowe `Shared` do deklaracji elementu członkowskiego. Zachowaj słowo kluczowe `Shared` w deklaracji procedury.

3. Jeśli każde wystąpienie ma mieć własną indywidualną kopię elementu członkowskiego, nie należy określać `Shared` dla deklaracji elementu członkowskiego. Usuń słowo kluczowe `Shared` z deklaracji procedury.
  
## <a name="see-also"></a>Zobacz także

- [Udostępniać](../modifiers/shared.md)
