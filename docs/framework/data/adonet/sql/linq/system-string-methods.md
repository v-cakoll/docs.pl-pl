---
title: Metody System.String
ms.date: 03/30/2017
ms.assetid: ce307f14-87e6-4816-8694-8a4147f6b784
ms.openlocfilehash: 569010c36296e18487eb52527d3df0cc0b97cf06
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54618134"
---
# <a name="systemstring-methods"></a>Metody System.String
[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] nie obsługuje następujących <xref:System.String> metody.  
  
## <a name="unsupported-systemstring-methods-in-general"></a>Ogólnie rzecz biorąc nieobsługiwany metody System.String  
 Nieobsługiwana <xref:System.String> metody ogólne:  
  
-   Przeciążenia kultury (metody, które przyjmują `CultureInfo`  /  `StringComparison`  /  `IFormatProvider`).  
  
-   Metody, które dopiero po lub utworzyć `char` tablicy.  
  
## <a name="unsupported-systemstring-static-methods"></a>Nieobsługiwany System.String statyczne metody  
  
|Nieobsługiwany System.String statyczne metody|  
|----------------------------------------------|  
|<xref:System.String.Copy%28System.String%29?displayProperty=nameWithType>|  
|<xref:System.String.Compare%28System.String%2CSystem.String%2CSystem.Boolean%29?displayProperty=nameWithType>|  
|<xref:System.String.Compare%28System.String%2CSystem.String%2CSystem.Boolean%2CSystem.Globalization.CultureInfo%29?displayProperty=nameWithType>|  
|<xref:System.String.Compare%28System.String%2CSystem.Int32%2CSystem.String%2CSystem.Int32%2CSystem.Int32%29?displayProperty=nameWithType>|  
|<xref:System.String.Compare%28System.String%2CSystem.Int32%2CSystem.String%2CSystem.Int32%2CSystem.Int32%2CSystem.Boolean%29?displayProperty=nameWithType>|  
|<xref:System.String.Compare%28System.String%2CSystem.Int32%2CSystem.String%2CSystem.Int32%2CSystem.Int32%2CSystem.Boolean%2CSystem.Globalization.CultureInfo%29?displayProperty=nameWithType>|  
|<xref:System.String.CompareOrdinal%28System.String%2CSystem.String%29?displayProperty=nameWithType>|  
|<xref:System.String.CompareOrdinal%28System.String%2CSystem.Int32%2CSystem.String%2CSystem.Int32%2CSystem.Int32%29?displayProperty=nameWithType>|  
|<xref:System.String.Format%2A?displayProperty=nameWithType>|  
|<xref:System.String.Join%2A?displayProperty=nameWithType>|  
  
## <a name="unsupported-systemstring-non-static-methods"></a>Nieobsługiwana System.String metod niestatycznych  
  
|Nieobsługiwana System.String metod niestatycznych|  
|---------------------------------------------------|  
|<xref:System.String.IndexOfAny%28System.Char%5B%5D%29?displayProperty=nameWithType>|  
|<xref:System.String.Split%2A?displayProperty=nameWithType>|  
|<xref:System.String.ToCharArray?displayProperty=nameWithType>|  
|<xref:System.String.ToUpper%28System.Globalization.CultureInfo%29?displayProperty=nameWithType>|  
|<xref:System.String.TrimEnd%28System.Char%5B%5D%29?displayProperty=nameWithType>|  
|<xref:System.String.TrimStart%28System.Char%5B%5D%29?displayProperty=nameWithType>|  
  
## <a name="differences-from-net"></a>Różnice z platformy .NET  
  
-   Zapytania nie uwzględniać sortowania programu SQL Server, które mogą obowiązywać na serwerze i będzie stanowić porównania wrażliwość na ustawienia kulturowe, bez uwzględniania wielkości liter domyślnie. To zachowanie różni się od domyślnej, semantyka liter programu .NET Framework.  
  
-   Gdy `LastIndexOf` jest zwraca wartość 0, ciągiem `NULL` lub znaleziono pozycji to 0.  
  
-   Nieoczekiwane wyniki mogą być zwracane z łączenia lub inne operacje na ciągi o stałej długości (`CHAR`, `NCHAR`), ponieważ te typy mają automatycznie dopełnienie stosowane w bazie danych.  
  
-   Ponieważ wiele metod, takich jak `Replace`, `ToLower`, `ToUpper`i indeksatora znaków, ma nie prawidłowe tłumaczenia `TEXT` lub `NTEXT` kolumn i XML, `SqlExceptions` wystąpić, jeśli zwykle translacji. To zachowanie jest uważany za akceptowalne dla tych typów. Jednak wszystkie operacje na ciągach musi odpowiadać wspólnego języka środowiska uruchomieniowego (języka wspólnego CLR) semantyki dla `VARCHAR`, `NVARCHAR`, `VARCHAR(max)`, i `NVARCHAR(max)`.  
  
## <a name="see-also"></a>Zobacz także
- [Typy danych i funkcje](../../../../../../docs/framework/data/adonet/sql/linq/data-types-and-functions.md)
