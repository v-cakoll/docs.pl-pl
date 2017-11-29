---
title: "IAssemblyCache — Interfejs"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IAssemblyCache
api_location: fusion.dll
api_type: COM
f1_keywords: IAssemblyCache
helpviewer_keywords: IAssemblyCache interface [.NET Framework fusion]
ms.assetid: 71ea170f-872d-4fc5-81b6-27da1dec9b19
topic_type: apiref
caps.latest.revision: "9"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 6244e6c3b0cc88c50cda050a480f5af5b3996b47
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="iassemblycache-interface"></a>IAssemblyCache — Interfejs
Reprezentuje Globalna pamięć podręczna zestawów do użycia przez technologię fusion.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Opis|  
|------------|-----------------|  
|[CreateAssemblyCacheItem — metoda](../../../../docs/framework/unmanaged-api/fusion/iassemblycache-createassemblycacheitem-method.md)|Pobiera odwołanie do nowego [IAssemblyCacheItem](../../../../docs/framework/unmanaged-api/fusion/iassemblycacheitem-interface.md).|  
|[CreateAssemblyScavenger — metoda](../../../../docs/framework/unmanaged-api/fusion/iassemblycache-createassemblyscavenger-method.md)|Zarezerwowany do użytku wewnętrznego przez technologię fusion.|  
|[InstallAssembly — metoda](../../../../docs/framework/unmanaged-api/fusion/iassemblycache-installassembly-method.md)|Instaluje określonego zestawu w globalnej pamięci podręcznej zestawów.|  
|[QueryAssemblyInfo — metoda](../../../../docs/framework/unmanaged-api/fusion/iassemblycache-queryassemblyinfo-method.md)|Pobiera żądane dane dotyczące określonego zestawu.|  
|[UninstallAssembly — metoda](../../../../docs/framework/unmanaged-api/fusion/iassemblycache-uninstallassembly-method.md)|Odinstalowuje określony zestaw z globalnej pamięci podręcznej zestawów.|  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** Fusion.h  
  
 **Wersje programu .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Zobacz też  
 [Interfejsy łączenia](../../../../docs/framework/unmanaged-api/fusion/fusion-interfaces.md)  
 [Globalna pamięć podręczna zestawów](../../../../docs/framework/app-domains/gac.md)
