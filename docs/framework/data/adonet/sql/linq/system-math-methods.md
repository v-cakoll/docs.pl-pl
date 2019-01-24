---
title: Metody System.Math
ms.date: 03/30/2017
ms.assetid: 0f299521-6f41-4720-bd70-67c93fc50948
ms.openlocfilehash: 45a674c86fc2f19f3e273834b8cb9d6adee5b3ab
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54576866"
---
# <a name="systemmath-methods"></a>Metody System.Math
[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] nie obsługuje następujących <xref:System.Math> metody.  
  
-   <xref:System.Math.DivRem%28System.Int32%2CSystem.Int32%2CSystem.Int32%40%29?displayProperty=nameWithType>  
  
-   <xref:System.Math.DivRem%28System.Int64%2CSystem.Int64%2CSystem.Int64%40%29?displayProperty=nameWithType>  
  
-   <xref:System.Math.IEEERemainder%28System.Double%2CSystem.Double%29?displayProperty=nameWithType>  
  
## <a name="differences-from-net"></a>Różnice z platformy .NET  
 .NET Framework ma semantykę różną zaokrąglania, z programu SQL Server. <xref:System.Math.Round%2A> Wykonuje metodę w programie .NET Framework *Banker przez zaokrąglenie*, gdzie liczb, które kończy się.5 zaokrąglona do najbliższej cyfry nawet zamiast kolejną cyfrą wyższy. Na przykład 2.5 Zaokrągla 2, podczas gdy 3.5 powoduje zaokrąglenie do 4. (Ta technika pomaga uniknąć systematyczne odchylenie kierunku wyższe wartości w transakcjach dużych ilości danych).  
  
 W programie SQL `ROUND` zamiast zawsze zaokrągla liczbę od 0. W związku z tym 2.5 zaokrągla do 3, porównanie z zaokrąglaniem do 2 w programie .NET Framework.  
  
 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] Przechodzi do bazy danych SQL `ROUND` semantyki i nie podejmuje próby wykonania zaokrąglenie kwot.  
  
## <a name="see-also"></a>Zobacz także
- [Typy danych i funkcje](../../../../../../docs/framework/data/adonet/sql/linq/data-types-and-functions.md)
