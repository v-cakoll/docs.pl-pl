---
title: System.Object, metody
ms.date: 03/30/2017
ms.assetid: 5397fca0-689e-443e-802f-e1cbdc866427
ms.openlocfilehash: 3a52f081f1c0c6e6c5218550009c736d0ed60514
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61917666"
---
# <a name="systemobject-methods"></a>System.Object, metody
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
|<xref:System.Object.ToString?displayProperty=nameWithType> dla pliku binarnego typy takie jak `BINARY`, `VARBINARY`, `IMAGE`, i `TIMESTAMP`.||  
  
## <a name="differences-from-net"></a>Różnice z platformy .NET  
 Dane wyjściowe <xref:System.Object.ToString?displayProperty=nameWithType> dla podwójnej precyzji SQL `CONVERT`(NVARCHAR(30), @x, 2) w języku SQL. SQL zawsze używa 16 cyfr i notacji wykładniczej w tym przypadku (na przykład "0.000000000000000e + 000" 0). W rezultacie <xref:System.Object.ToString?displayProperty=nameWithType> konwersji nie daje ten sam ciąg jako <xref:System.Convert.ToString%2A?displayProperty=nameWithType> w .NET Framework.  
  
## <a name="see-also"></a>Zobacz także

- [Typy danych i funkcje](../../../../../../docs/framework/data/adonet/sql/linq/data-types-and-functions.md)
