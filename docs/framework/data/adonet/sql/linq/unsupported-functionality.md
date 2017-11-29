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
ms.openlocfilehash: 6dd8ccebd278fdc36c536c49f7f1d4262b2de8c1
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
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
