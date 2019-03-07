---
title: IAssemblyCache::InstallAssembly — Metoda
ms.date: 03/30/2017
api_name:
- IAssemblyCache.InstallAssembly
api_location:
- fusion.dll
api_type:
- COM
f1_keywords:
- IAssemblyCache::InstallAssembly
helpviewer_keywords:
- InstallAssembly method [.NET Framework fusion]
- IAssemblyCache::InstallAssembly method [.NET Framework fusion]
ms.assetid: 33c1d269-c85e-4cb1-b0e6-1c510c8fb5fa
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 50152b72cade763a5b890c0c9d45109d88ce65a7
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/06/2019
ms.locfileid: "57469212"
---
# <a name="iassemblycacheinstallassembly-method"></a>IAssemblyCache::InstallAssembly — Metoda
Instaluje określony zestaw w globalnej pamięci podręcznej.  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT InstallAssembly (  
    [in] DWORD dwFlags,  
    [in] LPCWSTR pszManifestFilePath,  
    [in] LPCFUSION_INSTALL_REFERENCE pRefData  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `dwFlags`  
 [in] Flagi zdefiniowane w Fusion.idl. Obsługiwane są następujące wartości:  
  
-   IASSEMBLYCACHE_INSTALL_FLAG_REFRESH (0X00000001)  
  
-   IASSEMBLYCACHE_INSTALL_FLAG_FORCE_REFRESH (0X00000002)  
  
 `pszManifestFilePath`  
 [in] Ścieżka do manifestu zestawu do zainstalowania.  
  
 `pRefData`  
 [in] A [fusion_install_reference —](../../../../docs/framework/unmanaged-api/fusion/fusion-install-reference-structure.md) strukturę, która zawiera dane dotyczące instalacji.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** Fusion.h  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także
- [IAssemblyCache, interfejs](../../../../docs/framework/unmanaged-api/fusion/iassemblycache-interface.md)
