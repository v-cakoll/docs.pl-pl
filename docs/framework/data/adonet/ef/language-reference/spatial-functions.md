---
title: Funkcje przestrzenne
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 90cb177d-88a0-45be-97e8-3b306283c6e0
caps.latest.revision: "3"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 935708457c3ebc8257b2495da36886468be1c706
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="spatial-functions"></a>Funkcje przestrzenne
Brak ma literału formatu dla typów przestrzennych. Można jednak użyć kanonicznej funkcji programu Entity Framework wywołać przy użyciu ciągów w formacie Well-Known Text. Na przykład następujące wywołanie funkcji tworzy punkt geometrii:  
  
```  
GeometryFromText('POINT (43 -73)')  
```  
  
 [Metody SpatialEdmFunctions](http://msdn.microsoft.com/library/hh749531.aspx) strona zawiera listę przestrzennych canonical metody Entity Framework. Kliknij metodę zainteresowań, aby zobaczyć, jakie parametry powinien zostać przekazany do funkcji.
