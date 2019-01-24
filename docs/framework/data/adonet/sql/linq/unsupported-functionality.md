---
title: Nieobsługiwana funkcja
ms.date: 03/30/2017
ms.assetid: e480cfb5-697e-42c8-bed5-9264c945c4f9
ms.openlocfilehash: 5022c9011c2aac5b3272e359f991c40236a5673f
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54686706"
---
# <a name="unsupported-functionality"></a>Nieobsługiwana funkcja
W składniku LINQ to SQL tłumaczenie istniejące środowisko uruchomieniowe języka wspólnego (CLR) nie są dostępne następujące funkcje programu SQL i .NET Framework tworzy:  
  
-   `STDDEV`  
  
-   `LIKE`  
  
     Mimo że `LIKE` nie jest obsługiwany za pośrednictwem bezpośredniego tłumaczenia podobne funkcje istnieje w <xref:System.Data.Linq.SqlClient.SqlMethods> klasy. Aby uzyskać więcej informacji, zobacz <xref:System.Data.Linq.SqlClient.SqlMethods.Like%2A?displayProperty=nameWithType>.  
  
-   `DATEDIFF`  
  
     LINQ to SQL ma ograniczoną obsługę `DATEDIFF`. Podobne funkcje istnieje w <xref:System.Data.Linq.SqlClient.SqlMethods> klasy.  
  
-   `ROUND`  
  
     LINQ to SQL ma ograniczoną obsługę `ROUND`. Aby uzyskać więcej informacji, zobacz [metody System.Math](system-math-methods.md).  
  
## <a name="see-also"></a>Zobacz także
- [Typy danych i funkcje](data-types-and-functions.md)
