---
title: IMetaDataEmit2::SaveDelta — Metoda
ms.date: 03/30/2017
api_name:
- IMetaDataEmit2.SaveDelta
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit2::SaveDelta
helpviewer_keywords:
- IMetaDataEmit2::SaveDelta method [.NET Framework metadata]
- SaveDelta method [.NET Framework metadata]
ms.assetid: b95739fe-d2fa-4776-ae0d-31d9707ef799
topic_type:
- apiref
ms.openlocfilehash: afb0c09c09236267be2a999ce5c130feebb52b6f
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/23/2019
ms.locfileid: "74447905"
---
# <a name="imetadataemit2savedelta-method"></a>IMetaDataEmit2::SaveDelta — Metoda
Zapisuje zmiany z bieżącej sesji Edit-and-Continue do określonego pliku.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT SaveDelta (  
    [in] LPCWSTR     szFile,   
    [in] DWORD       dwSaveFlags  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `szFile`  
 podczas Nazwa pliku, w którym mają zostać zapisane zmiany.  
  
 `dwSaveFlags`  
 podczas Rezerwacj. Musi być równa zero.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** Cor. h  
  
 **Biblioteka:** Używany jako zasób w bibliotece MsCorEE. dll  
  
 **Wersje .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [IMetaDataEmit2, interfejs](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
- [IMetaDataEmit, interfejs](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
