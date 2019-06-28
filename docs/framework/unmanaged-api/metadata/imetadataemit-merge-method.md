---
title: IMetaDataEmit::Merge — Metoda
ms.date: 03/30/2017
api_name:
- IMetaDataEmit.Merge
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit::Merge
helpviewer_keywords:
- IMetaDataEmit::Merge method [.NET Framework metadata]
- Merge method [.NET Framework metadata]
ms.assetid: 7596220c-f699-4b6c-8ae7-c83220610650
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 65dbfd526110be5b9b3348fb677fbde7301e4038
ms.sourcegitcommit: 9b1ac36b6c80176fd4e20eb5bfcbd9d56c3264cf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/28/2019
ms.locfileid: "67424650"
---
# <a name="imetadataemitmerge-method"></a>IMetaDataEmit::Merge — Metoda
Dodaje określony zakres zaimportowane do listy zakresów do scalenia.  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT Merge (   
    [in]  IMetaDataImport  *pImport,   
    [in]  IMapToken        *pHostMapToken,   
    [in]  IUnknown         *pHandler   
);  
```  
  
## <a name="parameters"></a>Parametry  
 `pImport`  
 [in] Wskaźnik do [imetadataimport —](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md) obiekt, który identyfikuje zakres zaimportowane do scalenia.  
  
 `pIMap`  
 [in] Wskaźnik do [imaptoken —](../../../../docs/framework/unmanaged-api/metadata/imaptoken-interface.md) obiekt, który określa tokenu mapowane ponownie.  
  
 `pHandler`  
 [in] Wskaźnik do [IUnknown](/cpp/atl/iunknown) obiektu, który określa błędy.  
  
## <a name="remarks"></a>Uwagi  
 Wywołaj [IMetaDataEmit::MergeEnd](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-mergeend-method.md) wyzwolić połączenia metadanych do jednego zakresu.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** COR.h  
  
 **Biblioteka:** Używany jako zasób w MSCorEE.dll  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [IMetaDataEmit, interfejs](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [IMetaDataEmit2, interfejs](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
