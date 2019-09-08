---
title: System.String, metody
ms.date: 03/30/2017
ms.assetid: ce307f14-87e6-4816-8694-8a4147f6b784
ms.openlocfilehash: 583c0d58562c1605f24b61489d481e19248ebed4
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/07/2019
ms.locfileid: "70792491"
---
# <a name="systemstring-methods"></a>System.String, metody
[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]Program nie obsługuje następujących <xref:System.String> metod.  
  
## <a name="unsupported-systemstring-methods-in-general"></a>Ogólnie nieobsługiwane metody System. String  
 Ogólnie <xref:System.String> nieobsługiwane metody:  
  
- Przeciążenia z uwzględnieniem kultury (metody, które `CultureInfo`przyjmują `StringComparison`  /   /  `IFormatProvider`).  
  
- Metody, które pobierają lub `char` tworzą tablicę.  
  
## <a name="unsupported-systemstring-static-methods"></a>Nieobsługiwana metoda statyczna system. String  
  
|Nieobsługiwana metoda statyczna system. String|  
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
  
## <a name="unsupported-systemstring-non-static-methods"></a>Nieobsługiwana Metoda niestatyczna system. String  
  
|Nieobsługiwana Metoda niestatyczna system. String|  
|---------------------------------------------------|  
|<xref:System.String.IndexOfAny%28System.Char%5B%5D%29?displayProperty=nameWithType>|  
|<xref:System.String.Split%2A?displayProperty=nameWithType>|  
|<xref:System.String.ToCharArray?displayProperty=nameWithType>|  
|<xref:System.String.ToUpper%28System.Globalization.CultureInfo%29?displayProperty=nameWithType>|  
|<xref:System.String.TrimEnd%28System.Char%5B%5D%29?displayProperty=nameWithType>|  
|<xref:System.String.TrimStart%28System.Char%5B%5D%29?displayProperty=nameWithType>|  
  
## <a name="differences-from-net"></a>Różnice od platformy .NET  
  
- Zapytania nie uwzględniają sortowania SQL Server, które mogą być stosowane na serwerze i w związku z tym domyślnie udostępniają niezależne od wielkości liter porównania. To zachowanie różni się od domyślnej, zależnej od wielkości liter semantyki .NET Framework.  
  
- Gdy `LastIndexOf` zwraca wartość 0, ciąg jest `NULL` lub pozycja znaleziona ma wartość 0.  
  
- Nieoczekiwane wyniki mogą zostać zwrócone z łączenia lub innych operacji na ciągach o stałej`CHAR`długości `NCHAR`(,), ponieważ te typy automatycznie mają uzupełnienie zastosowane w bazie danych.  
  
- Ze względu na to, `Replace`że `ToLower`wiele `ToUpper`metod, takich jak,, i indeksator znaku, nie ma `TEXT` prawidłowych tłumaczeń dla `SqlExceptions` `NTEXT` kolumn i XML, występuje w przypadku przetłumaczenia normalnego. Takie zachowanie jest uznawane za akceptowalne dla tych typów. Jednak wszystkie operacje na ciągach muszą być zgodne z semantyką środowiska uruchomieniowego języka `VARCHAR`wspólnego `NVARCHAR`(CLR) `NVARCHAR(max)`dla,, `VARCHAR(max)`i.  
  
## <a name="see-also"></a>Zobacz także

- [Typy danych i funkcje](data-types-and-functions.md)
