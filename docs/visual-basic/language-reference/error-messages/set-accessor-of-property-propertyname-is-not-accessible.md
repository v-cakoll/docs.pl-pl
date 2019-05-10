---
title: Metoda dostępu „Set” właściwości „<propertyname>” jest niedostępna
ms.date: 07/20/2015
f1_keywords:
- vbc31102
- bc31102
helpviewer_keywords:
- BC31102
ms.assetid: 6f7b31b7-3656-4ae1-8851-90f5f4c6950a
ms.openlocfilehash: cf0158692c1154a8a903c893ba287e51c1e34ac8
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/28/2019
ms.locfileid: "64593270"
---
# <a name="set-accessor-of-property-propertyname-is-not-accessible"></a>Ustaw metody dostępu właściwości "\<propertyname >" jest niedostępny
Instrukcję próbuje zapisać wartość właściwości, gdy nie ma dostępu do właściwości `Set` procedury.  
  
 Jeśli [instrukcji Set](../../../visual-basic/language-reference/statements/set-statement.md) jest oznaczony przy użyciu bardziej restrykcyjne poziomu niż jego [Property — instrukcja](../../../visual-basic/language-reference/statements/property-statement.md), ustawić wartość właściwości może się nie powieść w następujących przypadkach:  
  
- `Set` Oznaczonej instrukcji [prywatnej](../../../visual-basic/language-reference/modifiers/private.md) i kod wywołujący znajduje się poza klasy lub struktury, w którym właściwość jest zdefiniowana.  
  
- `Set` Oznaczonej instrukcji [chronione](../../../visual-basic/language-reference/modifiers/protected.md) i kod wywołujący nie ma w klasy lub struktury, w którym zdefiniowano właściwość ani w klasie pochodnej.  
  
- `Set` Oznaczonej instrukcji [Friend](../../../visual-basic/language-reference/modifiers/friend.md) i kod wywołujący nie jest w tym samym zestawie, w którym właściwość jest zdefiniowana.  
  
 **Identyfikator błędu:** BC31102  
  
## <a name="to-correct-this-error"></a>Aby poprawić ten błąd  
  
- Jeśli masz kontroli kodu źródłowego, definiując właściwość, należy rozważyć deklarowanie `Set` procedury na tym samym poziomie dostępu jako samej właściwości.  
  
- Jeśli nie masz kontroli kodu źródłowego, definiując właściwość lub należy ograniczyć `Set` procedury więcej niż właściwość, spróbuj przenieść instrukcję, która ustawia wartości właściwości w regionie kodu, który ma lepszy dostęp do poziomu dostępu Właściwość.  
  
## <a name="see-also"></a>Zobacz także

- [Procedury właściwości](../../../visual-basic/programming-guide/language-features/procedures/property-procedures.md)
- [Instrukcje: Deklarowanie właściwości z mieszanymi poziomami dostępu](../../../visual-basic/programming-guide/language-features/procedures/how-to-declare-a-property-with-mixed-access-levels.md)
