---
title: Metoda dostępu „Set” właściwości „<propertyname>” jest niedostępna
ms.date: 07/20/2015
f1_keywords:
- vbc31102
- bc31102
helpviewer_keywords:
- BC31102
ms.assetid: 6f7b31b7-3656-4ae1-8851-90f5f4c6950a
ms.openlocfilehash: 077533a5b1fe241b61ded9516ad8f450d7dbbf5e
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2020
ms.locfileid: "84400347"
---
# <a name="set-accessor-of-property-propertyname-is-not-accessible"></a>Metoda dostępu „Set” właściwości „\<propertyname>” jest niedostępna
Instrukcja próbuje zapisać wartość właściwości, gdy nie ma dostępu do `Set` procedury właściwości.  
  
 Jeśli [instrukcja set](../statements/set-statement.md) jest oznaczona przy użyciu bardziej restrykcyjnego poziomu dostępu niż jego [instrukcja Property](../statements/property-statement.md), próba ustawienia wartości właściwości może zakończyć się niepowodzeniem w następujących przypadkach:  
  
- `Set`Instrukcja jest oznaczona jako [Private](../modifiers/private.md) , a kod wywołujący znajduje się poza klasą lub strukturą, w której właściwość jest zdefiniowana.  
  
- `Set`Instrukcja jest oznaczona jako [Protected](../modifiers/protected.md) , a wywoływany kod nie znajduje się w klasie lub strukturze, w której właściwość jest zdefiniowana, ani w klasie pochodnej.  
  
- `Set`Instrukcja jest oznaczona jako [Friend](../modifiers/friend.md) i kod wywołujący nie znajduje się w tym samym zestawie, w którym jest zdefiniowana właściwość.  
  
 **Identyfikator błędu:** BC31102  
  
## <a name="to-correct-this-error"></a>Aby poprawić ten błąd  
  
- Jeśli masz kontrolę nad kodem źródłowym definiującym właściwość, rozważ zadeklarowanie `Set` procedury z takim samym poziomem dostępu jak sama właściwość.  
  
- Jeśli nie masz kontroli nad kodem źródłowym definiującym właściwość lub musisz ograniczyć `Set` poziom dostępu do procedury więcej niż sama właściwość, spróbuj przenieść instrukcję, która ustawia wartość właściwości na region kodu, który ma lepszy dostęp do właściwości.  
  
## <a name="see-also"></a>Zobacz też

- [Procedury własności](../../programming-guide/language-features/procedures/property-procedures.md)
- [Porady: deklarowanie właściwości z mieszanymi poziomami dostępu](../../programming-guide/language-features/procedures/how-to-declare-a-property-with-mixed-access-levels.md)
