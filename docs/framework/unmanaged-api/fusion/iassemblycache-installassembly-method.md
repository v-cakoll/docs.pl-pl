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
ms.openlocfilehash: cd420f0f166b0b17e5fbaf08d6bedd6651188b1c
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/10/2019
ms.locfileid: "67778745"
---
# <a name="iassemblycacheinstallassembly-method"></a>IAssemblyCache::InstallAssembly — Metoda
Instaluje określony zestaw w globalnej pamięci podręcznej.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT InstallAssembly (  
    [in] DWORD dwFlags,  
    [in] LPCWSTR pszManifestFilePath,  
    [in] LPCFUSION_INSTALL_REFERENCE pRefData  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `dwFlags`  
 [in] Flagi zdefiniowane w Fusion.idl. Obsługiwane są następujące wartości:  
  
- IASSEMBLYCACHE_INSTALL_FLAG_REFRESH (0X00000001)  
  
- IASSEMBLYCACHE_INSTALL_FLAG_FORCE_REFRESH (0X00000002)  
  
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
