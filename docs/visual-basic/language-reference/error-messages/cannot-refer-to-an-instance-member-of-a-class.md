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
ms.openlocfilehash: 368539ed24d9819c8d1ddbbb9e3e0dff21d27c32
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="cannot-refer-to-an-instance-member-of-a-class-from-within-a-shared-method-or-shared-member-initializer-without-an-explicit-instance-of-the-class"></a>Do składowej wystąpienia klasy nie można odwołać się z obrębu udostępnionej metody lub udostępnionego inicjatora składowej bez jawnego wystąpienia klasy
Próbowano odwołać się do nieudostępnionego członka klasy z wnętrza współdzielonej procedury. W poniższym przykładzie pokazano takiej sytuacji.  
  
```  
Class sample  
    Public x as Integer  
    Public Shared Sub setX()  
        x = 10  
    End Sub  
End Class  
```  
  
 W powyższym przykładzie w instrukcji przypisania `x = 10` generuje ten komunikat o błędzie. Jest to spowodowane współdzielonej procedury próbuje uzyskać dostęp do zmiennej wystąpienia.  
  
 Zmienna `x` jest elementem członkowskim wystąpienia, ponieważ nie jest zadeklarowany jako [Shared](../../../visual-basic/language-reference/modifiers/shared.md). Każde wystąpienie klasy `sample` zawiera poszczególnych zmienna `x`. Jeśli jedno wystąpienie Ustawia lub zmienia wartość `x`, nie ma wpływu na wartość `x` w innym wystąpieniu.  
  
 Jednak procedura `setX` jest `Shared` wśród wszystkich wystąpień klasy `sample`. Oznacza to, nie jest skojarzony z dowolnego jednego wystąpienia klasy, ale raczej działa niezależnie od poszczególnych wystąpień. Ponieważ nie jest on żadne połączenie z określonym wystąpieniem `setX` nie może uzyskać dostępu do zmiennej wystąpienia. Musi działać tylko na `Shared` zmiennych. Gdy `setX` Ustawia lub zmienia wartość zmiennej udostępnionego, że nowa wartość jest dostępna dla wszystkich wystąpień klasy.  
  
 **Identyfikator błędu:** BC30369  
  
## <a name="to-correct-this-error"></a>Aby poprawić ten błąd  
  
1.  Zdecyduj, czy ma element członkowski współdzielona przez wszystkie wystąpienia klasy lub przechowywane poszczególnych dla każdego wystąpienia.  
  
2.  Pojedynczej kopii elementu członkowskiego do współdzielona przez wszystkie wystąpienia, należy dodać `Shared` — słowo kluczowe do deklaracji elementu członkowskiego. Zachowaj `Shared` — słowo kluczowe w deklaracji procedury.  
  
3.  Jeśli chcesz, aby każde wystąpienie ma własną pojedynczych kopii elementu członkowskiego, nie należy określać `Shared` dla deklaracji elementu członkowskiego. Usuń `Shared` — słowo kluczowe z deklaracji procedury.  
  
## <a name="see-also"></a>Zobacz też  
 [Shared](../../../visual-basic/language-reference/modifiers/shared.md)
