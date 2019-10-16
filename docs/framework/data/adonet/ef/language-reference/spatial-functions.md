---
title: Funkcje przestrzenne
ms.date: 03/30/2017
ms.assetid: 90cb177d-88a0-45be-97e8-3b306283c6e0
ms.openlocfilehash: eba384e77389f82006479f165178e80fcac244b1
ms.sourcegitcommit: 628e8147ca10187488e6407dab4c4e6ebe0cac47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/15/2019
ms.locfileid: "72319301"
---
# <a name="spatial-functions"></a>Funkcje przestrzenne
Nie ma formatu literału dla typów przestrzennych. Można jednak używać kanonicznych funkcji Entity Framework, które są wywoływane za pomocą ciągów w formacie dobrze znanego tekstu. Na przykład następujące wywołanie funkcji tworzy punkt geometrii:  
  
```sql  
GeometryFromText('POINT (43 -73)')  
```  
  
 Metody <xref:System.Data.Common.CommandTrees.ExpressionBuilder.Spatial.SpatialEdmFunctions> mają wszystkie jednoEntity Frameworkowe metody kanoniczne. Kliknij metodę zainteresowania, aby zobaczyć, jakie parametry mają być przenoszone do funkcji.
