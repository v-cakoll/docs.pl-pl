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
ms.openlocfilehash: 98997bfbb7d3c9343f78438b1195222565c5b9ad
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33444554"
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
  
#### <a name="parameters"></a>Parametry  
 `pImport`  
 [in] Wskaźnik do [IMetaDataImport](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md) obiekt, który identyfikuje zakres zaimportowane do scalenia.  
  
 `pIMap`  
 [in] Wskaźnik do [IMapToken](../../../../docs/framework/unmanaged-api/metadata/imaptoken-interface.md) obiekt, który określa token mapowane ponownie.  
  
 `pHandleer`  
 [in] Wskaźnik do <!--<<!--zzxref:IUnknown --> `IUnknown` >-->  `IUnknown` obiekt, który określa błędy.  
  
## <a name="remarks"></a>Uwagi  
 Wywołanie [IMetaDataEmit::MergeEnd](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-mergeend-method.md) aby wyzwolić połączenia metadanych w pojedynczy zakres.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** Cor.h  
  
 **Biblioteka:** używany jako zasób w MSCorEE.dll  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Zobacz też  
 [IMetaDataEmit, interfejs](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)  
 [IMetaDataEmit2, interfejs](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
