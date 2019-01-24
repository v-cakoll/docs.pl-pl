---
title: '&#39;Pobierz&#39; metody dostępu właściwości &#39; &lt;propertyname&gt; &#39; jest niedostępny'
ms.date: 07/20/2015
f1_keywords:
- vbc31103
- bc31103
helpviewer_keywords:
- BC31103
ms.assetid: 3c346c32-7669-4b04-841d-7a9df9cb703e
ms.openlocfilehash: 10b7168ac40ca7c7d696cd63cd823454f404bb94
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54582217"
---
# <a name="39get39-accessor-of-property-39ltpropertynamegt39-is-not-accessible"></a>&#39;Pobierz&#39; metody dostępu właściwości &#39; &lt;propertyname&gt; &#39; jest niedostępny
Próbuje pobrać wartość właściwości, gdy nie ma dostępu do właściwości instrukcji `Get` procedury.  
  
 Jeśli [instrukcja Get](../../../visual-basic/language-reference/statements/get-statement.md) jest oznaczony przy użyciu bardziej restrykcyjne poziomu niż jego [Property — instrukcja](../../../visual-basic/language-reference/statements/property-statement.md), próba odczytu wartość właściwości może się nie powieść w następujących przypadkach:  
  
-   `Get` Oznaczonej instrukcji [prywatnej](../../../visual-basic/language-reference/modifiers/private.md) i kod wywołujący znajduje się poza klasy lub struktury, w którym właściwość jest zdefiniowana.  
  
-   `Get` Oznaczonej instrukcji [chronione](../../../visual-basic/language-reference/modifiers/protected.md) i kod wywołujący nie ma w klasy lub struktury, w którym zdefiniowano właściwość ani w klasie pochodnej.  
  
-   `Get` Oznaczonej instrukcji [Friend](../../../visual-basic/language-reference/modifiers/friend.md) i kod wywołujący nie jest w tym samym zestawie, w którym właściwość jest zdefiniowana.  
  
 **Identyfikator błędu:** BC31103  
  
## <a name="to-correct-this-error"></a>Aby poprawić ten błąd  
  
-   Jeśli masz kontroli kodu źródłowego, definiując właściwość, należy rozważyć deklarowanie `Get` procedury na tym samym poziomie dostępu jako samej właściwości.  
  
-   Jeśli nie masz kontroli kodu źródłowego, definiując właściwość lub należy ograniczyć `Get` procedury więcej niż właściwość, spróbuj przenieść instrukcję, która odczytuje wartości właściwości do regionu kod, który ma lepszy dostęp do poziomu dostępu Właściwość.  
  
## <a name="see-also"></a>Zobacz także
- [Procedury właściwości](../../../visual-basic/programming-guide/language-features/procedures/property-procedures.md)
- [Instrukcje: Deklarowanie właściwości z mieszanymi poziomami dostępu](../../../visual-basic/programming-guide/language-features/procedures/how-to-declare-a-property-with-mixed-access-levels.md)
