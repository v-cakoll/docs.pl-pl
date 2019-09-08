---
title: System.Math, metody
ms.date: 03/30/2017
ms.assetid: 0f299521-6f41-4720-bd70-67c93fc50948
ms.openlocfilehash: 0b113cefa6be040924134f9d2d0cb0c9d334feef
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/07/2019
ms.locfileid: "70792390"
---
# <a name="systemmath-methods"></a>System.Math, metody
[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]Program nie obsługuje następujących <xref:System.Math> metod.  
  
- <xref:System.Math.DivRem%28System.Int32%2CSystem.Int32%2CSystem.Int32%40%29?displayProperty=nameWithType>  
  
- <xref:System.Math.DivRem%28System.Int64%2CSystem.Int64%2CSystem.Int64%40%29?displayProperty=nameWithType>  
  
- <xref:System.Math.IEEERemainder%28System.Double%2CSystem.Double%29?displayProperty=nameWithType>  
  
## <a name="differences-from-net"></a>Różnice od platformy .NET  
 .NET Framework ma inną semantykę zaokrąglania z SQL Server. Metoda w .NET Framework wykonuje *Zaokrąglenie w banku*, gdzie liczby kończące się w .5 zaokrąglają do najbliższej parzystej cyfry zamiast do kolejnej wyższej cyfry. <xref:System.Math.Round%2A> Na przykład 2,5 zaokrągla do 2, a 3,5 zaokrągla do 4. (Ta technika pozwala uniknąć regularnego obciążenia w kierunku wyższych wartości w dużych transakcjach danych).  
  
 W języku SQL funkcja `ROUND` zamiast tego jest zawsze zaokrąglana w kierunku od zera. W związku z tym 2,5 Zaokrąglaj do 3, kontrastowo z zaokrągleniem do 2 w .NET Framework.  
  
 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]przekazuje do semantyki SQL `ROUND` i nie próbuje zaimplementować zaokrąglenia banku.  
  
## <a name="see-also"></a>Zobacz także

- [Typy danych i funkcje](data-types-and-functions.md)
