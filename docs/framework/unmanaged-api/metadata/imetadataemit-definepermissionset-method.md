---
title: IMetaDataEmit::DefinePermissionSet — Metoda
ms.date: 03/30/2017
api_name:
- IMetaDataEmit.DefinePermissionSet
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit::DefinePermissionSet
helpviewer_keywords:
- DefinePermissionSet method [.NET Framework metadata]
- IMetaDataEmit::DefinePermissionSet method [.NET Framework metadata]
ms.assetid: 36cffbf7-82ca-4cf9-bf60-50ab491ac2d9
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 33eadccf691b14289a46ff460f3cef8ae636b129
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62043982"
---
# <a name="imetadataemitdefinepermissionset-method"></a>IMetaDataEmit::DefinePermissionSet — Metoda
Tworzy definicję zestawu uprawnień o podpisu określonych metadanych, a następnie pobiera token do tej definicji zestaw uprawnień.  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT DefinePermissionSet (  
    [in]  mdToken        tk,   
    [in]  DWORD          dwAction,   
    [in]  void const     *pvPermission,   
    [in]  ULONG          cbPermission,   
    [out] mdPermission   *ppm   
);  
```  
  
## <a name="parameters"></a>Parametry  
 `tk`  
 [in] Obiekt do posiadać.  
  
 `dwAction`  
 [in] A [cordeclsecurity —](../../../../docs/framework/unmanaged-api/metadata/cordeclsecurity-enumeration.md) wartość, która określa typ zabezpieczenia deklaratywne ma być używany.  
  
 `pvPermission`  
 [in] Uprawnienie obiektu BLOB.  
  
 `cbPermission`  
 [in] Rozmiar w bajtach z `pvPermission`.  
  
 `ppm`  
 [out] Token zwracany uprawnień.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** COR.h  
  
 **Biblioteka:** Używany jako zasób w MSCorEE.dll  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [IMetaDataEmit, interfejs](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [IMetaDataEmit2, interfejs](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
