---
title: IAssemblyCache::QueryAssemblyInfo — Metoda
ms.date: 03/30/2017
api_name:
- IAssemblyCache.QueryAssemblyInfo
api_location:
- fusion.dll
api_type:
- COM
f1_keywords:
- IAssemblyCache::QueryAssemblyInfo
helpviewer_keywords:
- IAssemblyCache::QueryAssemblyInfo method [.NET Framework fusion]
- QueryAssemblyInfo method [.NET Framework fusion]
ms.assetid: 09313cb5-06f6-43bd-94f4-1055c6b0c99a
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 6935a72bb99e636b3732958ee88ad224b401513b
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33430723"
---
# <a name="iassemblycachequeryassemblyinfo-method"></a>IAssemblyCache::QueryAssemblyInfo — Metoda
Pobiera żądane dane dotyczące określonego zestawu.  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT QueryAssemblyInfo (  
    [in] DWORD dwFlags,  
    [in] LPCWSTR pszAssemblyName,  
    [in, out] ASSEMBLY_INFO *pAsmInfo  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `dwFlags`  
 [in] Flagi zdefiniowane w Fusion.idl. Obsługiwane są następujące wartości:  
  
-   QUERYASMINFO_FLAG_VALIDATE (0X00000001)  
  
-   QUERYASMINFO_FLAG_GETSIZE (0X00000002)  
  
 `pszAssemblyName`  
 [in] Nazwa zestawu, dla którego będzie można pobrać danych.  
  
 `pAsmInfo`  
 [w, out] [Assembly_info —](../../../../docs/framework/unmanaged-api/fusion/assembly-info-structure.md) strukturę, która zawiera dane dotyczące zestawu.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** Fusion.h  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Zobacz też  
 [IAssemblyCache, interfejs](../../../../docs/framework/unmanaged-api/fusion/iassemblycache-interface.md)
