---
title: AssemblyAttributesGoHereSM
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: AssemblyAttributesGoHereSM
api_location: alink.dll
api_type: COM
f1_keywords: AssemblyAttributesGoHereSM
helpviewer_keywords:
- AssemblyAttributesGoHereSM type
- Alink API, AssemblyAttributesGoHereSM type
ms.assetid: 4cf9bf39-1527-49e0-a0e9-55e7a018bf66
topic_type: apiref
caps.latest.revision: "4"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 912bd97b0b907f9edb27254bbf3419a684e6d697
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="assemblyattributesgoheresm"></a>AssemblyAttributesGoHereSM
Używane przez ALink jako symbol zastępczy do przechowywania informacji na temat atrybutów niestandardowych.  
  
## <a name="syntax"></a>Składnia  
  
```  
AssemblyAttributeGoHereSM  
```  
  
## <a name="remarks"></a>Uwagi  
 Odwołania do tego typu może być osadzony wewnątrz netmodules, których źródła zawierają niestandardowe atrybuty zestawu. Podczas tworzenia manifestu zestawu z co najmniej jeden netmodules, które zawierają odwołania do tych typów, ALink używa informacji dołączonych do tych odwołań do emisji rzeczywistym niestandardowych atrybutów. W związku tego typu nigdy nie zostanie uruchomiony, a odwołania do niego są używane tylko jako część procesu kompilacji oraz udostępni bezcelowe w zestawie końcowym.  
  
 Odwołania do tego typu wskazuje atrybutów niestandardowych, które są powiązane i wielokrotnego użytku zabezpieczeń.  
  
 Te typy są oznaczone jako "wewnętrzne" w programie .NET Framework i znajdują się w <xref:System.Runtime.CompilerServices>.  
  
## <a name="requirements"></a>Wymagania  
 mscorlib.dll  
  
## <a name="see-also"></a>Zobacz też  
 [Assemblyattributesgohere —](../../../../docs/framework/unmanaged-api/alink/assemblyattributesgohere.md)  
 [Assemblyattributesgoherem —](../../../../docs/framework/unmanaged-api/alink/assemblyattributesgoherem.md)  
 [Assemblyattributesgoheres —](../../../../docs/framework/unmanaged-api/alink/assemblyattributesgoheres.md)
