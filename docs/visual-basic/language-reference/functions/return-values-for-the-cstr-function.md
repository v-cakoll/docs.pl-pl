---
title: Zwracane wartości dla funkcji CStr (Visual Basic)
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
ms.openlocfilehash: cd525ea5a295411e509f3bc37285675d15a8c4f4
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69930047"
---
# <a name="return-values-for-the-cstr-function-visual-basic"></a>Zwracane wartości dla funkcji CStr (Visual Basic)
W poniższej tabeli opisano wartości zwracane dla `CStr` różnych `expression`typów danych.  
  
|Jeśli `expression` typ jest|`CStr`typu|  
|-----------------------------|--------------------|  
|[Boolean, typ danych](../../../visual-basic/language-reference/data-types/boolean-data-type.md)|Ciąg zawierający wartość "true" lub "false".|  
|[Date, typ danych](../../../visual-basic/language-reference/data-types/date-data-type.md)|Ciąg zawierający `Date` wartość (Data i godzina) w formacie daty krótkiej systemu.|  
|[Typy danych liczbowych](../../../visual-basic/programming-guide/language-features/data-types/numeric-data-types.md)|Ciąg reprezentujący liczbę.|  
  
## <a name="cstr-and-date"></a>CStr i Data  
 `Date` Typ zawsze zawiera informacje o dacie i godzinie. Na potrzeby konwersji typów Visual Basic uznaje, że 1/1/0001 (1 stycznia roku 1) jest *wartością neutralną* dla daty oraz 00:00:00 (północy) jako wartość neutralną czasu. `CStr`nie uwzględnia neutralnych wartości w ciągu będącym wynikiem. Na przykład w przypadku konwersji `#January 1, 0001 9:30:00#` na ciąg, wynikiem jest "9:30:00 am"; informacje o dacie są pomijane. Jednak informacje o dacie są nadal obecne w pierwotnej `Date` wartości i mogą być odzyskiwane za pomocą funkcji, takich jak. <xref:Microsoft.VisualBasic.DateAndTime.DatePart%2A>  
  
> [!NOTE]
> `CStr` Funkcja wykonuje konwersję w oparciu o bieżące ustawienia kultury dla aplikacji. Aby uzyskać ciąg reprezentujący liczbę w określonej kulturze, użyj `ToString(IFormatProvider)` metody Number. Na przykład, użyj <xref:System.Double.ToString%2A?displayProperty=nameWithType> podczas konwertowania wartości typu `Double` na `String`.  
  
## <a name="see-also"></a>Zobacz także

- <xref:Microsoft.VisualBasic.DateAndTime.DatePart%2A>
- [Funkcje konwersji typu](../../../visual-basic/language-reference/functions/type-conversion-functions.md)
- [Boolean, typ danych](../../../visual-basic/language-reference/data-types/boolean-data-type.md)
- [Date, typ danych](../../../visual-basic/language-reference/data-types/date-data-type.md)
