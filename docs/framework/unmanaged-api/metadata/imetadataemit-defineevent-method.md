---
title: "IMetaDataEmit::DefineEvent — Metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- IMetaDataEmit.DefineEvent
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit::DefineEvent
helpviewer_keywords:
- IMetaDataEmit::DefineEvent method [.NET Framework metadata]
- DefineEvent method [.NET Framework metadata]
ms.assetid: cf064bac-9a9f-41c5-9e1d-108ff7af3afe
topic_type:
- apiref
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 8f27c0a01dd795cfcc5399c4115cd6d905629fd7
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="imetadataemitdefineevent-method"></a>IMetaDataEmit::DefineEvent — Metoda
Tworzy definicję zdarzenie o sygnaturze określonych metadanych, a następnie pobiera token do tej definicji zdarzeń.  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT DefineEvent (   
    [in]  mdTypeDef    td,   
    [in]  LPCWSTR      szEvent,   
    [in]  DWORD        dwEventFlags,   
    [in]  mdToken      tkEventType,   
    [in]  mdMethodDef  mdAddOn,   
    [in]  mdMethodDef  mdRemoveOn,   
    [in]  mdMethodDef  mdFire,   
    [in]  mdMethodDef  rmdOtherMethods[],   
    [out] mdEvent      *pmdEvent   
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `td`  
 [in] Token dla klasy docelowej lub interfejsu. Jest to `mdTypeDef` lub `mdTypeDefNil` tokenu.  
  
 `szEvent`  
 [in] Nazwa zdarzenia.  
  
 `dwEventFlags`  
 [in] Flagi zdarzeń.  
  
 `tkEventType`  
 [in] Token dla klasy zdarzeń. Jest to `mdTypeDef`, `mdTypeRef`, lub `mdTokenNil` tokenu.  
  
 `mdAddOn`  
 [in] Metoda użyta do subskrybowania zdarzenia lub wartość null.  
  
 `mdRemoveOn`  
 [in] Metoda używana do anulowania subskrypcji zdarzeń lub wartość null.  
  
 `mdFire`  
 [in] Metoda używana (przez klasę pochodną), aby wywołać zdarzenie.  
  
 `rmdOtherMethods[]`  
 [in] Tablica dla innych metod, skojarzone ze zdarzeniem. Tablica kończy się znakiem `mdMethodDefNil` tokenu.  
  
 `pmdEvent`  
 [out] Token metadanych przypisany do zdarzenia.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** Cor.h  
  
 **Biblioteka:** używany jako zasób w MSCorEE.dll  
  
 **Wersje programu .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Zobacz też  
 [IMetaDataEmit, interfejs](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)  
 [IMetaDataEmit2, interfejs](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
