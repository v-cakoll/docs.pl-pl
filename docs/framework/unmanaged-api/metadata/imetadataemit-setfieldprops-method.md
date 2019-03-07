---
title: IMetaDataEmit::SetFieldProps — Metoda
ms.date: 03/30/2017
api_name:
- IMetaDataEmit.SetFieldProps
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit::SetFieldProps
helpviewer_keywords:
- IMetaDataEmit::SetFieldProps method [.NET Framework metadata]
- SetFieldProps method [.NET Framework metadata]
ms.assetid: 47132dda-fa92-4bd1-ae4b-24cd9a60665a
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: ace278e0031d3e673418f50356f173c473a4832d
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/06/2019
ms.locfileid: "57494327"
---
# <a name="imetadataemitsetfieldprops-method"></a>IMetaDataEmit::SetFieldProps — Metoda
Ustawia lub aktualizuje wartość domyślną dla pola przywoływane przez token określonego pola.  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT SetFieldProps (  
    [in]  mdFieldDef  fd,   
    [in]  DWORD       dwFieldFlags,   
    [in]  DWORD       dwCPlusTypeFlag,   
    [in]  void const  *pValue,   
    [in]  ULONG       cchValue   
);  
```  
  
## <a name="parameters"></a>Parametry  
 `fd`  
 [in] Token do pola docelowego.  
  
 `dwFieldFlags`  
 [in] Atrybuty pól. Jest to z `CorFieldAttr` wartości.  
  
 `dwCPlusTypeFlag`  
 [in] `ELEMENT_TYPE_` *\** Wartości stałej. Jest to `CorElementType` wartość. Jeśli nie zdefiniowano jest stałą, ustaw tę wartość na `ELEMENT_TYPE_END`.  
  
 `pValue`  
 [in] Stała wartość dla pola.  
  
 `cchValue`  
 [in] Rozmiar w znaki Unicode z `pValue`.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** COR.h  
  
 **Biblioteka:** Używany jako zasób w MSCorEE.dll  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także
- [IMetaDataEmit, interfejs](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [IMetaDataEmit2, interfejs](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
