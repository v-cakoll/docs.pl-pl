---
title: "IMetaDataEmit::SetEventProps — Metoda"
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
- IMetaDataEmit.SetEventProps
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit::SetEventProps
helpviewer_keywords:
- IMetaDataEmit::SetEventProps method [.NET Framework metadata]
- SetEventProps method [.NET Framework metadata]
ms.assetid: 3b039e50-63ec-4730-99ff-2327408de477
topic_type:
- apiref
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: f8e2089c3f4b4e7677c2ddb9eabc8ee08cfd3695
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="imetadataemitseteventprops-method"></a>IMetaDataEmit::SetEventProps — Metoda
Ustawia lub aktualizuje określoną funkcję wynika z wcześniejszym wywołaniu zdarzenia [IMetaDataEmit::DefineEvent](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-defineevent-method.md).  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT SetEventProps (  
    [in]  mdEvent     ev,   
    [in]  DWORD       dwEventFlags,   
    [in]  mdToken     tkEventType,   
    [in]  mdMethodDef mdAddOn,   
    [in]  mdMethodDef mdRemoveOn,   
    [in]  mdMethodDef mdFire,   
    [in]  mdMethodDef rmdOtherMethods[]   
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `ev`  
 [in] Token zdarzeń.  
  
 `dwEventFlags`  
 [in] Flagi zdarzeń. To jest maską bitów z `CorEventAttr` wartości.  
  
 `tkEventType`  
 [in] Token dla klasy zdarzeń. Jest to `mdTypeDef` lub `mdTypeRef` tokenu.  
  
 `mdAddOn`  
 [in] Metoda użyta do subskrybowania zdarzenia lub wartość null.  
  
 `mdRemoveOn`  
 [in] Metoda używana do anulowania subskrypcji zdarzeń lub wartość null.  
  
 `mdFire`  
 [in] Metoda używana (przez klasę pochodną), aby wywołać zdarzenie.  
  
 `rmdOtherMethods[]`  
 [in] Tablica dla innych metod, skojarzone ze zdarzeniem. Musi być ostatnim elementem tablicy `mdMethodDefNil`.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** Cor.h  
  
 **Biblioteka:** używany jako zasób w MSCorEE.dll  
  
 **Wersje programu .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Zobacz też  
 [IMetaDataEmit, interfejs](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)  
 [IMetaDataEmit2, interfejs](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
