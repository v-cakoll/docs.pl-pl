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
ms.openlocfilehash: 5312734633eea12aacd7e61afba616d31e06cd71
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33598527"
---
# <a name="return-values-for-the-cstr-function-visual-basic"></a>Zwracane wartości dla funkcji CStr (Visual Basic)
W poniższej tabeli opisano wartości zwracanych przez `CStr` dla różnych typów danych z `expression`.  
  
|Jeśli `expression` jest typu|`CStr` Zwraca|  
|-----------------------------|--------------------|  
|[Boolean, typ danych](../../../visual-basic/language-reference/data-types/boolean-data-type.md)|Ciąg zawierający "wartość True" lub "False".|  
|[Date, typ danych](../../../visual-basic/language-reference/data-types/date-data-type.md)|Ciąg zawierający `Date` wartość (Data i godzina) w formacie daty krótkiej systemu.|  
|[Typy danych liczbowych](../../../visual-basic/programming-guide/language-features/data-types/numeric-data-types.md)|Ciąg reprezentujący liczbę.|  
  
## <a name="cstr-and-date"></a>Data i CStr  
 `Date` Typu zawsze zawiera informacje zarówno datę i godzinę. W celu konwersji typu, Visual Basic uważa 1/1/0001 (1 stycznia 1 roku) *neutralne wartość* daty i 00:00:00 (północ) jako neutralny wartość po raz. `CStr` nie ma wartości neutralne w ciągu wynikowym. Na przykład, jeśli przekonwertujesz `#January 1, 0001 9:30:00#` na ciąg, wynikiem jest "9:30:00 AM"; informacje o dacie jest pomijane. Jednak informacje o dacie jest nadal znajdują się w oryginalnym `Date` wartości i może zostać przywrócona z funkcji takich jak <xref:Microsoft.VisualBasic.DateAndTime.DatePart%2A>.  
  
> [!NOTE]
>  `CStr` Funkcja wykonuje jego konwersja na podstawie ustawień bieżącej kultury aplikacji. Aby uzyskać reprezentację liczby w określonej kultury, użyj numeru `ToString(IFormatProvider)` metody. Na przykład użyć <xref:System.Double.ToString%2A?displayProperty=nameWithType> podczas konwertowania wartości typu `Double` do `String`.  
  
## <a name="see-also"></a>Zobacz też  
 <xref:Microsoft.VisualBasic.DateAndTime.DatePart%2A>  
 [Funkcje konwersji typu](../../../visual-basic/language-reference/functions/type-conversion-functions.md)  
 [Boolean, typ danych](../../../visual-basic/language-reference/data-types/boolean-data-type.md)  
 [Date, typ danych](../../../visual-basic/language-reference/data-types/date-data-type.md)
