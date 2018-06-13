---
title: Metody System.Object
ms.date: 03/30/2017
ms.assetid: 5397fca0-689e-443e-802f-e1cbdc866427
ms.openlocfilehash: bd4b30a65e7ad9391d9b867884d1c909491344bc
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33355178"
---
# <a name="systemobject-methods"></a>Metody System.Object
[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] obsługuje następujące <xref:System.Object> metody.  
  
|||  
|-|-|  
|<xref:System.Object.Equals%28System.Object%29?displayProperty=nameWithType>|<xref:System.Object.Equals%28System.Object%2CSystem.Object%29?displayProperty=nameWithType>|  
|<xref:System.Object.ToString?displayProperty=nameWithType>||  
  
 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] nie obsługuje następujących <xref:System.Object> metody.  
  
|||  
|-|-|  
|<xref:System.Object.GetHashCode?displayProperty=nameWithType>|<xref:System.Object.ReferenceEquals%28System.Object%2CSystem.Object%29?displayProperty=nameWithType>|  
|<xref:System.Object.MemberwiseClone?displayProperty=nameWithType>|<xref:System.Object.GetType?displayProperty=nameWithType>|  
|<xref:System.Object.ToString?displayProperty=nameWithType> dla pliku binarnego takich jak typy `BINARY`, `VARBINARY`, `IMAGE`, i `TIMESTAMP`.||  
  
## <a name="differences-from-net"></a>Różnice z platformy .NET  
 Dane wyjściowe <xref:System.Object.ToString?displayProperty=nameWithType> dla typu double używa SQL `CONVERT`(NVARCHAR(30), @x, 2) na SQL. SQL zawsze używa 16 cyfr i notacja naukowa w tym przypadku (na przykład "0.000000000000000e + 000" 0). W związku z tym <xref:System.Object.ToString?displayProperty=nameWithType> konwersji nie tworzy tych samych parametrach jako <xref:System.Convert.ToString%2A?displayProperty=nameWithType> w programie .NET Framework.  
  
## <a name="see-also"></a>Zobacz też  
 [Typy danych i funkcje](../../../../../../docs/framework/data/adonet/sql/linq/data-types-and-functions.md)
