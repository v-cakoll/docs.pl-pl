---
title: Nieobsługiwanych funkcji
ms.date: 03/30/2017
ms.assetid: e480cfb5-697e-42c8-bed5-9264c945c4f9
ms.openlocfilehash: c4ed52a43fe9cf04c8015aad9247e9f2eb2481e4
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33364493"
---
# <a name="unsupported-functionality"></a>Nieobsługiwanych funkcji
W składniku LINQ to SQL nie są dostępne następujące funkcje SQL tłumaczenia istniejące środowisko uruchomieniowe języka wspólnego (CLR) i tworzy .NET Framework:  
  
-   `STDDEV`  
  
-   `LIKE`  
  
     Mimo że `LIKE` nie jest obsługiwana przez bezpośrednie tłumaczenia podobne funkcje istnieje w <xref:System.Data.Linq.SqlClient.SqlMethods> klasy. Aby uzyskać więcej informacji, zobacz <xref:System.Data.Linq.SqlClient.SqlMethods.Like%2A?displayProperty=nameWithType>.  
  
-   `DATEDIFF`  
  
     LINQ do SQL ma ograniczoną obsługę `DATEDIFF`. Istnieje podobne funkcje w <xref:System.Data.Linq.SqlClient.SqlMethods> klasy.  
  
-   `ROUND`  
  
     LINQ do SQL ma ograniczoną obsługę `ROUND`. Aby uzyskać więcej informacji, zobacz [metody System.Math](system-math-methods.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Typy danych i funkcje](data-types-and-functions.md)
