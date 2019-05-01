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
ms.openlocfilehash: aad068b5857eb956ded63fa2a57cb163d3cf5c58
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62013845"
---
# <a name="cannot-refer-to-an-instance-member-of-a-class-from-within-a-shared-method-or-shared-member-initializer-without-an-explicit-instance-of-the-class"></a>Do składowej wystąpienia klasy nie można odwołać się z obrębu udostępnionej metody lub udostępnionego inicjatora składowej bez jawnego wystąpienia klasy
Wykonano do odwoływania się do elementu członkowskiego klasy z w ramach procedury udostępnianej nieudostępnione. W poniższym przykładzie pokazano takiej sytuacji.  
  
```  
Class sample  
    Public x as Integer  
    Public Shared Sub setX()  
        x = 10  
    End Sub  
End Class  
```  
  
 W powyższym przykładzie instrukcja przypisania `x = 10` generuje ten komunikat o błędzie. Jest to spowodowane procedury udostępnianej próbuje uzyskać dostęp do zmiennej wystąpienia.  
  
 Zmienna `x` jest członkiem wystąpienia, ponieważ nie jest zadeklarowany jako [Shared](../../../visual-basic/language-reference/modifiers/shared.md). Każde wystąpienie klasy `sample` zawiera poszczególne zmienna `x`. Jeśli jedno wystąpienie, ustawia lub zmienia wartość `x`, nie ma wpływu na wartość `x` w innym wystąpieniu.  
  
 Jednak procedura `setX` jest `Shared` wśród wszystkich wystąpień klasy `sample`. Oznacza to, nie jest skojarzony z dowolnego jedno wystąpienie tej klasy, ale raczej działa niezależnie od poszczególnych wystąpień. Ponieważ ma ona nie połączenia z konkretnego wystąpienia `setX` nie może uzyskać dostępu do zmiennej wystąpienia. Musi działać tylko na `Shared` zmiennych. Gdy `setX` Ustawia lub zmienia wartość zmiennej udostępnionego, nowa wartość jest dostępna dla wszystkich wystąpień klasy.  
  
 **Identyfikator błędu:** BC30369  
  
## <a name="to-correct-this-error"></a>Aby poprawić ten błąd  
  
1. Zdecyduj, czy chcesz, aby element członkowski współużytkowane przez wszystkie wystąpienia klasy lub przechowywać poszczególne dla każdego wystąpienia.  
  
2. Pojedyncza kopia elementu członkowskiego do współdzielenia pośród wszystkich wystąpień, dodać `Shared` — słowo kluczowe do deklaracji elementu członkowskiego. Zachowaj `Shared` słowa kluczowego w zgłoszeniu procedury.  
  
3. Jeśli chcesz, aby każde wystąpienie ma swój własny pojedyncza kopia elementu członkowskiego, nie należy określać `Shared` deklaracji elementu członkowskiego. Usuń `Shared` słowo kluczowe z deklaracja procedury.  
  
## <a name="see-also"></a>Zobacz także

- [Shared](../../../visual-basic/language-reference/modifiers/shared.md)
