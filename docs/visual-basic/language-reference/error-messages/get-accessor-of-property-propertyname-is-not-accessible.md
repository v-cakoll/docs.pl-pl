---
title: Metoda dostępu „Get” właściwości „<propertyname>” jest niedostępna
ms.date: 07/20/2015
f1_keywords:
- vbc31103
- bc31103
helpviewer_keywords:
- BC31103
ms.assetid: 3c346c32-7669-4b04-841d-7a9df9cb703e
ms.openlocfilehash: 8fb78f3c14708c79f1910e202287c25a3b2213b7
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/02/2019
ms.locfileid: "58814409"
---
# <a name="get-accessor-of-property-propertyname-is-not-accessible"></a>Metoda dostępu właściwości "get" "\<propertyname >" jest niedostępny
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
