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
ms.openlocfilehash: 6039ba3f6bd1c364db818807604ee0851bc23d50
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2020
ms.locfileid: "84406390"
---
# <a name="return-values-for-the-cstr-function-visual-basic"></a>Zwracane wartości dla funkcji CStr (Visual Basic)
W poniższej tabeli opisano wartości zwracane dla `CStr` różnych typów danych `expression` .  
  
|Jeśli `expression` Typ jest|`CStr`typu|  
|-----------------------------|--------------------|  
|[Boolean, typ danych](../data-types/boolean-data-type.md)|Ciąg zawierający wartość "true" lub "false".|  
|[Date, typ danych](../data-types/date-data-type.md)|Ciąg zawierający `Date` wartość (Data i godzina) w formacie daty krótkiej systemu.|  
|[Typy danych liczbowych](../../programming-guide/language-features/data-types/numeric-data-types.md)|Ciąg reprezentujący liczbę.|  
  
## <a name="cstr-and-date"></a>CStr i Data  
 `Date`Typ zawsze zawiera informacje o dacie i godzinie. Na potrzeby konwersji typów Visual Basic uznaje, że 1/1/0001 (1 stycznia roku 1) jest *wartością neutralną* dla daty oraz 00:00:00 (północy) jako wartość neutralną czasu. `CStr`nie uwzględnia neutralnych wartości w ciągu będącym wynikiem. Na przykład w przypadku konwersji `#January 1, 0001 9:30:00#` na ciąg, wynikiem jest "9:30:00 am"; informacje o dacie są pomijane. Jednak informacje o dacie są nadal obecne w pierwotnej `Date` wartości i mogą być odzyskiwane za pomocą funkcji, takich jak <xref:Microsoft.VisualBasic.DateAndTime.DatePart%2A> .  
  
> [!NOTE]
> `CStr`Funkcja wykonuje konwersję w oparciu o bieżące ustawienia kultury dla aplikacji. Aby uzyskać ciąg reprezentujący liczbę w określonej kulturze, użyj `ToString(IFormatProvider)` metody Number. Na przykład, użyj <xref:System.Double.ToString%2A?displayProperty=nameWithType> podczas konwertowania wartości typu `Double` na `String` .  
  
## <a name="see-also"></a>Zobacz też

- <xref:Microsoft.VisualBasic.DateAndTime.DatePart%2A>
- [Funkcje konwersji typu](type-conversion-functions.md)
- [Boolean, typ danych](../data-types/boolean-data-type.md)
- [Date, typ danych](../data-types/date-data-type.md)
