---
title: IMetaDataEmit::SetEventProps — Metoda
ms.date: 03/30/2017
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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: abfa8a3f58d3e9f7c80762c1faf2bc51514d71b2
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59113818"
---
# <a name="imetadataemitseteventprops-method"></a>IMetaDataEmit::SetEventProps — Metoda
Ustawia lub aktualizuje określoną funkcję zdarzenie zdefiniowane przez wcześniejsze wywołanie [IMetaDataEmit::DefineEvent](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-defineevent-method.md).  
  
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
  
## <a name="parameters"></a>Parametry  
 `ev`  
 [in] Token zdarzeń.  
  
 `dwEventFlags`  
 [in] Flagi zdarzenia. Jest to z `CorEventAttr` wartości.  
  
 `tkEventType`  
 [in] Token dla klasy zdarzeń. Jest to `mdTypeDef` lub `mdTypeRef` tokenu.  
  
 `mdAddOn`  
 [in] Metoda używana do subskrybowania zdarzenia lub wartość null.  
  
 `mdRemoveOn`  
 [in] Metoda użyta Aby anulować subskrypcję zdarzenia lub wartość null.  
  
 `mdFire`  
 [in] Metoda używana (przez klasę pochodną), aby zgłosić zdarzenie.  
  
 `rmdOtherMethods[]`  
 [in] Tablica do innych metod, skojarzone ze zdarzeniem. Ostatni element tablicy muszą być `mdMethodDefNil`.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** COR.h  
  
 **Biblioteka:** Używany jako zasób w MSCorEE.dll  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [IMetaDataEmit, interfejs](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [IMetaDataEmit2, interfejs](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
