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
ms.openlocfilehash: 3653194c7e48533e664ac7513ca7f4f48d1c69f7
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "58819518"
---
# <a name="return-values-for-the-cstr-function-visual-basic"></a>Zwracane wartości dla funkcji CStr (Visual Basic)
W poniższej tabeli opisano wartości zwracane dla `CStr` dla różnych typów danych z `expression`.  
  
|Jeśli `expression` jest typu|`CStr` Zwraca|  
|-----------------------------|--------------------|  
|[Boolean, typ danych](../../../visual-basic/language-reference/data-types/boolean-data-type.md)|Ciąg zawierający "True" lub "False".|  
|[Date, typ danych](../../../visual-basic/language-reference/data-types/date-data-type.md)|Ciąg zawierający `Date` wartość (Data i godzina) w formacie daty krótkiej systemu.|  
|[Typy danych liczbowych](../../../visual-basic/programming-guide/language-features/data-types/numeric-data-types.md)|Ciąg reprezentujący liczbę.|  
  
## <a name="cstr-and-date"></a>CStr Data i godzina  
 `Date` Typ zawsze zawiera informacje o daty i godziny. W celu konwersji typu, Visual Basic traktuje 1/1/0001 (1 stycznia 1 rok) jako *neutralne wartość* dla daty i 00:00:00 (północ) jako neutralne wartość po raz. `CStr` nie ma wartości neutralne w ciągu wynikowym. Na przykład, jeśli można przekonwertować `#January 1, 0001 9:30:00#` na ciąg wyniku "9:30:00 AM"; informacje o dacie jest pomijane. Informacje o dacie jest jednak nadal znajdują się w oryginalnym `Date` wartości i można odzyskać za pomocą funkcji takich jak <xref:Microsoft.VisualBasic.DateAndTime.DatePart%2A>.  
  
> [!NOTE]
>  `CStr` Funkcja wykonuje jego konwersji, w oparciu o bieżące ustawienia kultury w aplikacji. Aby uzyskać ciąg reprezentujący numer w danej kultury, należy użyć numeru `ToString(IFormatProvider)` metody. Na przykład użyć <xref:System.Double.ToString%2A?displayProperty=nameWithType> podczas konwertowania wartości typu `Double` do `String`.  
  
## <a name="see-also"></a>Zobacz także

- <xref:Microsoft.VisualBasic.DateAndTime.DatePart%2A>
- [Funkcje konwersji typu](../../../visual-basic/language-reference/functions/type-conversion-functions.md)
- [Boolean, typ danych](../../../visual-basic/language-reference/data-types/boolean-data-type.md)
- [Date, typ danych](../../../visual-basic/language-reference/data-types/date-data-type.md)
