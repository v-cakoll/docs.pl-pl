---
title: System.Object, metody
ms.date: 03/30/2017
ms.assetid: 5397fca0-689e-443e-802f-e1cbdc866427
ms.openlocfilehash: d1a36798ef789bbc44f581dfc631feee19e1f66b
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/07/2019
ms.locfileid: "70781074"
---
# <a name="systemobject-methods"></a>System.Object, metody
[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]obsługuje następujące <xref:System.Object> metody.  
  
|||  
|-|-|  
|<xref:System.Object.Equals%28System.Object%29?displayProperty=nameWithType>|<xref:System.Object.Equals%28System.Object%2CSystem.Object%29?displayProperty=nameWithType>|  
|<xref:System.Object.ToString?displayProperty=nameWithType>||  
  
 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]Program nie obsługuje następujących <xref:System.Object> metod.  
  
|||  
|-|-|  
|<xref:System.Object.GetHashCode?displayProperty=nameWithType>|<xref:System.Object.ReferenceEquals%28System.Object%2CSystem.Object%29?displayProperty=nameWithType>|  
|<xref:System.Object.MemberwiseClone?displayProperty=nameWithType>|<xref:System.Object.GetType?displayProperty=nameWithType>|  
|<xref:System.Object.ToString?displayProperty=nameWithType>w przypadku typów binarnych `BINARY`, `VARBINARY`takich `IMAGE`jak, `TIMESTAMP`, i.||  
  
## <a name="differences-from-net"></a>Różnice od platformy .NET  
 Dane wyjściowe <xref:System.Object.ToString?displayProperty=nameWithType> dla elementu Double używają języka `CONVERT`SQL (nvarchar (30) @x,, 2) na serwerze SQL. W tym przypadku SQL zawsze używa 16 cyfr i notacji wykładniczej (na przykład "0.000000000000000 e + 000" dla 0). W związku <xref:System.Object.ToString?displayProperty=nameWithType> z tym konwersja nie produkuje tego samego ciągu co <xref:System.Convert.ToString%2A?displayProperty=nameWithType> w .NET Framework.  
  
## <a name="see-also"></a>Zobacz także

- [Typy danych i funkcje](data-types-and-functions.md)
