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
ms.openlocfilehash: 6966d0ad2fefd8401b19d8e8dcf7776799a066b2
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/23/2019
ms.locfileid: "74432567"
---
# <a name="imetadataemitdefineevent-method"></a>IMetaDataEmit::DefineEvent — Metoda
Tworzy definicję zdarzenia z określonym podpisem metadanych i pobiera token do tej definicji zdarzenia.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
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
 podczas Token dla docelowej klasy lub interfejsu. To jest token `mdTypeDef` lub `mdTypeDefNil`.  
  
 `szEvent`  
 podczas Nazwa zdarzenia.  
  
 `dwEventFlags`  
 podczas Flagi zdarzeń.  
  
 `tkEventType`  
 podczas Token dla klasy Event. Jest to `mdTypeDef`, `mdTypeRef`lub token `mdTokenNil`.  
  
 `mdAddOn`  
 podczas Metoda używana do subskrybowania zdarzenia lub wartość null.  
  
 `mdRemoveOn`  
 podczas Metoda używana do anulowania subskrypcji zdarzenia lub wartość null.  
  
 `mdFire`  
 podczas Metoda używana (przez klasę pochodną) do podniesienia zdarzenia.  
  
 `rmdOtherMethods[]`  
 podczas Tablica tokenów dla innych metod skojarzonych ze zdarzeniem. Tablica zostanie zakończona z tokenem `mdMethodDefNil`.  
  
 `pmdEvent`  
 określoną Token metadanych przypisany do zdarzenia.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** Cor. h  
  
 **Biblioteka:** Używany jako zasób w bibliotece MSCorEE. dll  
  
 **Wersje .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [IMetaDataEmit, interfejs](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [IMetaDataEmit2, interfejs](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
