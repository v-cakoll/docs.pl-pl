---
title: IMetaDataEmit::SetPermissionSetProps — Metoda
ms.date: 03/30/2017
api_name:
- IMetaDataEmit.SetPermissionSetProps
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit::SetPermissionSetProps
helpviewer_keywords:
- SetPermissionSetProps method [.NET Framework metadata]
- IMetaDataEmit::SetPermissionSetProps method [.NET Framework metadata]
ms.assetid: 8eaee971-40bf-45e2-a3d8-6e57674213b6
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: f77e6e9711f05262e494f2814750af8ef7cd9f64
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/10/2019
ms.locfileid: "67750904"
---
# <a name="imetadataemitsetpermissionsetprops-method"></a>IMetaDataEmit::SetPermissionSetProps — Metoda
Ustawia lub aktualizuje funkcji podpisu metadanych zestawu uprawnień, zdefiniowane przez wcześniejsze wywołanie [IMetaDataEmit::DefinePermissionSet](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definepermissionset-method.md).  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT SetPermissionSetProps (   
    [in]  mdToken         tk,   
    [in]  DWORD           dwAction,   
    [in]  void const      *pvPermission,   
    [in]  ULONG           cbPermission,   
    [out] mdPermission    *ppm   
);  
```  
  
## <a name="parameters"></a>Parametry  
 `tk`  
 [in] Token metadanych, który reprezentuje obiekt umożliwiający posiadać.  
  
 `dwAction`  
 [in] A [cordeclsecurity —](../../../../docs/framework/unmanaged-api/metadata/cordeclsecurity-enumeration.md) wartość, która określa typ zabezpieczenia deklaratywne ma być używany.  
  
 `pvPermission`  
 [in] Uprawnienie obiektu BLOB.  
  
 `cbPermission`  
 [in] Rozmiar w bajtach z `pvPermission`.  
  
 `ppm`  
 [out] `mdPermission` Token metadanych, który reprezentuje zaktualizowanymi uprawnieniami.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** COR.h  
  
 **Biblioteka:** Używany jako zasób w MSCorEE.dll  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [IMetaDataEmit, interfejs](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [IMetaDataEmit2, interfejs](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
