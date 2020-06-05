---
title: Metoda dostępu „Get” właściwości „<propertyname>” jest niedostępna
ms.date: 07/20/2015
f1_keywords:
- vbc31103
- bc31103
helpviewer_keywords:
- BC31103
ms.assetid: 3c346c32-7669-4b04-841d-7a9df9cb703e
ms.openlocfilehash: cb953671e624d5b9170aa0b3a9dd80c7ba8337e3
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2020
ms.locfileid: "84402917"
---
# <a name="get-accessor-of-property-propertyname-is-not-accessible"></a>Metoda dostępu „Get” właściwości „\<propertyname>” jest niedostępna
Instrukcja próbuje pobrać wartość właściwości, gdy nie ma dostępu do `Get` procedury właściwości.  
  
 Jeśli [instrukcja GET](../statements/get-statement.md) jest oznaczona przy użyciu bardziej restrykcyjnego poziomu dostępu niż jego [instrukcja Property](../statements/property-statement.md), próba odczytu wartości właściwości może zakończyć się niepowodzeniem w następujących przypadkach:  
  
- `Get`Instrukcja jest oznaczona jako [Private](../modifiers/private.md) , a kod wywołujący znajduje się poza klasą lub strukturą, w której właściwość jest zdefiniowana.  
  
- `Get`Instrukcja jest oznaczona jako [Protected](../modifiers/protected.md) , a wywoływany kod nie znajduje się w klasie lub strukturze, w której właściwość jest zdefiniowana, ani w klasie pochodnej.  
  
- `Get`Instrukcja jest oznaczona jako [Friend](../modifiers/friend.md) i kod wywołujący nie znajduje się w tym samym zestawie, w którym jest zdefiniowana właściwość.  
  
 **Identyfikator błędu:** BC31103  
  
## <a name="to-correct-this-error"></a>Aby poprawić ten błąd  
  
- Jeśli masz kontrolę nad kodem źródłowym definiującym właściwość, rozważ zadeklarowanie `Get` procedury z takim samym poziomem dostępu jak sama właściwość.  
  
- Jeśli nie masz kontroli nad kodem źródłowym definiującym właściwość lub musisz ograniczyć `Get` poziom dostępu do procedury więcej niż sama właściwość, spróbuj przenieść instrukcję, która odczytuje wartość właściwości do regionu kodu, który ma lepszy dostęp do właściwości.  
  
## <a name="see-also"></a>Zobacz też

- [Procedury własności](../../programming-guide/language-features/procedures/property-procedures.md)
- [Porady: deklarowanie właściwości z mieszanymi poziomami dostępu](../../programming-guide/language-features/procedures/how-to-declare-a-property-with-mixed-access-levels.md)
