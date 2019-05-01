---
title: IMetaDataEmit::DefineEvent — Metoda
ms.date: 03/30/2017
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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 48055103b49b4c61bb7561f2d4aa6c8daae07ae2
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62044216"
---
# <a name="imetadataemitdefineevent-method"></a>IMetaDataEmit::DefineEvent — Metoda
Tworzy definicję na zdarzenie o sygnaturze określonych metadanych, a następnie pobiera token do tej definicji zdarzeń.  
  
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
  
## <a name="parameters"></a>Parametry  
 `td`  
 [in] Token dla klasy docelowej lub interfejs. Jest to `mdTypeDef` lub `mdTypeDefNil` tokenu.  
  
 `szEvent`  
 [in] Nazwa zdarzenia.  
  
 `dwEventFlags`  
 [in] Flagi zdarzenia.  
  
 `tkEventType`  
 [in] Token dla klasy zdarzeń. Jest to `mdTypeDef`, `mdTypeRef`, lub `mdTokenNil` tokenu.  
  
 `mdAddOn`  
 [in] Metoda używana do subskrybowania zdarzenia lub wartość null.  
  
 `mdRemoveOn`  
 [in] Metoda użyta Aby anulować subskrypcję zdarzenia lub wartość null.  
  
 `mdFire`  
 [in] Metoda używana (przez klasę pochodną), aby zgłosić zdarzenie.  
  
 `rmdOtherMethods[]`  
 [in] Tablica do innych metod, skojarzone ze zdarzeniem. Tablica jest kończony przy użyciu `mdMethodDefNil` tokenu.  
  
 `pmdEvent`  
 [out] Token metadanych, przypisany do zdarzenia.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** COR.h  
  
 **Biblioteka:** Używany jako zasób w MSCorEE.dll  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [IMetaDataEmit, interfejs](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [IMetaDataEmit2, interfejs](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
