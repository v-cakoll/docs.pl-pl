---
title: IAssemblyCache — Interfejs
ms.date: 03/30/2017
api_name:
- IAssemblyCache
api_location:
- fusion.dll
api_type:
- COM
f1_keywords:
- IAssemblyCache
helpviewer_keywords:
- IAssemblyCache interface [.NET Framework fusion]
ms.assetid: 71ea170f-872d-4fc5-81b6-27da1dec9b19
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 4302a73f9f077c2e1bf4f66c2b80ab025ae4a62c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33430586"
---
# <a name="iassemblycache-interface"></a>IAssemblyCache — Interfejs
Reprezentuje Globalna pamięć podręczna zestawów do użycia przez technologię fusion.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Opis|  
|------------|-----------------|  
|[CreateAssemblyCacheItem, metoda](../../../../docs/framework/unmanaged-api/fusion/iassemblycache-createassemblycacheitem-method.md)|Pobiera odwołanie do nowego [IAssemblyCacheItem](../../../../docs/framework/unmanaged-api/fusion/iassemblycacheitem-interface.md).|  
|[CreateAssemblyScavenger, metoda](../../../../docs/framework/unmanaged-api/fusion/iassemblycache-createassemblyscavenger-method.md)|Zarezerwowany do użytku wewnętrznego przez technologię fusion.|  
|[InstallAssembly, metoda](../../../../docs/framework/unmanaged-api/fusion/iassemblycache-installassembly-method.md)|Instaluje określonego zestawu w globalnej pamięci podręcznej zestawów.|  
|[QueryAssemblyInfo, metoda](../../../../docs/framework/unmanaged-api/fusion/iassemblycache-queryassemblyinfo-method.md)|Pobiera żądane dane dotyczące określonego zestawu.|  
|[UninstallAssembly, metoda](../../../../docs/framework/unmanaged-api/fusion/iassemblycache-uninstallassembly-method.md)|Odinstalowuje określony zestaw z globalnej pamięci podręcznej zestawów.|  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** Fusion.h  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Zobacz też  
 [Interfejsy łączenia](../../../../docs/framework/unmanaged-api/fusion/fusion-interfaces.md)  
 [Global Assembly Cache](../../../../docs/framework/app-domains/gac.md)
