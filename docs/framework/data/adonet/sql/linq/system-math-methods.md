---
title: Metody System.Math
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 0f299521-6f41-4720-bd70-67c93fc50948
caps.latest.revision: "2"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: af5e18b9c4334cfab26c9a84ac647bb433391ef1
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="systemmath-methods"></a>Metody System.Math
[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]nie obsługuje następujących <xref:System.Math> metody.  
  
-   <xref:System.Math.DivRem%28System.Int32%2CSystem.Int32%2CSystem.Int32%40%29?displayProperty=nameWithType>  
  
-   <xref:System.Math.DivRem%28System.Int64%2CSystem.Int64%2CSystem.Int64%40%29?displayProperty=nameWithType>  
  
-   <xref:System.Math.IEEERemainder%28System.Double%2CSystem.Double%29?displayProperty=nameWithType>  
  
## <a name="differences-from-net"></a>Różnice z platformy .NET  
 .NET Framework ma semantykę różną zaokrąglania z programu SQL Server. <xref:System.Math.Round%2A> Wykonuje metodę w programie .NET Framework *zaokrąglenie do zaokrąglania*, gdzie numery, które kończy się.5 zaokrąglona do najbliższej nawet cyfr zamiast z następnym wyższym cyfry. Na przykład 2.5 powoduje zaokrąglenie do 2, podczas gdy 3.5 powoduje zaokrąglenie do 4. (Ta technika pomaga uniknąć systematyczne odchylenia kierunku wyższe wartości w transakcji dużej ilości danych).  
  
 W programie SQL `ROUND` funkcja zamiast zawsze zaokrągla wartość w kierunku od 0. W związku z tym 2.5 powoduje zaokrąglenie do 3 odróżniające z zaokrąglania 2 w programie .NET Framework.  
  
 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]Przechodzi do SQL `ROUND` semantykę i nie próbuje zaimplementować zaokrąglenie kwot.  
  
## <a name="see-also"></a>Zobacz też  
 [Typy danych i funkcje](../../../../../../docs/framework/data/adonet/sql/linq/data-types-and-functions.md)
