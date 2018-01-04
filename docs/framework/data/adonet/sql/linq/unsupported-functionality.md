---
title: "Nieobsługiwanych funkcji"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: e480cfb5-697e-42c8-bed5-9264c945c4f9
caps.latest.revision: "2"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: 244d9ee7accd3686729542d0f0a15966bcde7b78
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
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
