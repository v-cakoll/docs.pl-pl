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
ms.openlocfilehash: 08b9fdee1138becd4cd5a933f96021c470aadf1f
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/07/2019
ms.locfileid: "70796787"
---
# <a name="iassemblycachequeryassemblyinfo-method"></a>IAssemblyCache::QueryAssemblyInfo — Metoda
Pobiera żądane dane dotyczące określonego zestawu.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT QueryAssemblyInfo (  
    [in] DWORD dwFlags,  
    [in] LPCWSTR pszAssemblyName,  
    [in, out] ASSEMBLY_INFO *pAsmInfo  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `dwFlags`  
 podczas Flagi zdefiniowane w pliku Fusion. idl. Obsługiwane są następujące wartości:  
  
- QUERYASMINFO_FLAG_VALIDATE (0x00000001)  
  
- QUERYASMINFO_FLAG_GETSIZE (0x00000002)  
  
 `pszAssemblyName`  
 podczas Nazwa zestawu, dla którego zostaną pobrane dane.  
  
 `pAsmInfo`  
 [in. out] Struktura [ASSEMBLY_INFO](assembly-info-structure.md) , która zawiera dane dotyczące zestawu.  
  
## <a name="requirements"></a>Wymagania  
 **Poszczególnych** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).  
  
 **Nagłówki** Fusion. h  
  
 **.NET Framework wersje:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [IAssemblyCache, interfejs](iassemblycache-interface.md)
