---
title: Zwracane wartości dla funkcji CStr
ms.date: 07/20/2015
helpviewer_keywords:
- times [Visual Basic], CStr Function return values
- type conversion [Visual Basic]
- dates [Visual Basic], CStr Function return values
- CStr function
- strings [Visual Basic], return value
- Date data type [Visual Basic], converting
- dates [Visual Basic]
- String data type [Visual Basic], converting
ms.assetid: 3aa744e7-1419-45d5-85e3-e5abc2953673
ms.openlocfilehash: 4a40777c7290ec6d8c0d032f2edca5d889e20f04
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/22/2019
ms.locfileid: "74349989"
---
# <a name="return-values-for-the-cstr-function-visual-basic"></a>Zwracane wartości dla funkcji CStr (Visual Basic)
W poniższej tabeli opisano wartości zwracane dla `CStr` dla różnych typów danych `expression`.  
  
|Jeśli typ `expression` to|`CStr` zwraca|  
|-----------------------------|--------------------|  
|[Boolean, typ danych](../../../visual-basic/language-reference/data-types/boolean-data-type.md)|Ciąg zawierający wartość "true" lub "false".|  
|[Date, typ danych](../../../visual-basic/language-reference/data-types/date-data-type.md)|Ciąg zawierający `Date` wartość (Data i godzina) w formacie daty krótkiej systemu.|  
|[Typy danych liczbowych](../../../visual-basic/programming-guide/language-features/data-types/numeric-data-types.md)|Ciąg reprezentujący liczbę.|  
  
## <a name="cstr-and-date"></a>CStr i Data  
 Typ `Date` zawsze zawiera informacje o dacie i godzinie. Na potrzeby konwersji typów Visual Basic uznaje, że 1/1/0001 (1 stycznia roku 1) jest *wartością neutralną* dla daty oraz 00:00:00 (północy) jako wartość neutralną czasu. `CStr` nie zawiera neutralnych wartości w ciągu będącym wynikiem. Na przykład w przypadku konwersji `#January 1, 0001 9:30:00#` na ciąg, wynikiem jest "9:30:00 AM"; Informacje o dacie są pomijane. Jednak informacje o dacie są nadal obecne w oryginalnej wartości `Date` i mogą być odzyskiwane za pomocą funkcji, takich jak <xref:Microsoft.VisualBasic.DateAndTime.DatePart%2A>.  
  
> [!NOTE]
> Funkcja `CStr` wykonuje konwersję na podstawie bieżących ustawień kultury aplikacji. Aby uzyskać ciąg reprezentujący liczbę w określonej kulturze, użyj metody `ToString(IFormatProvider)`. Na przykład użyj <xref:System.Double.ToString%2A?displayProperty=nameWithType> podczas konwertowania wartości typu `Double` na `String`.  
  
## <a name="see-also"></a>Zobacz także

- <xref:Microsoft.VisualBasic.DateAndTime.DatePart%2A>
- [Funkcje konwersji typu](../../../visual-basic/language-reference/functions/type-conversion-functions.md)
- [Boolean, typ danych](../../../visual-basic/language-reference/data-types/boolean-data-type.md)
- [Date, typ danych](../../../visual-basic/language-reference/data-types/date-data-type.md)
