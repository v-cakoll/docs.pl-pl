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
ms.openlocfilehash: 7babd0a90b9882acb03b6360753f55c57a399b9e
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/27/2020
ms.locfileid: "84005638"
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
 podczas Token dla docelowej klasy lub interfejsu. Jest to `mdTypeDef` `mdTypeDefNil` token lub.  
  
 `szEvent`  
 podczas Nazwa zdarzenia.  
  
 `dwEventFlags`  
 podczas Flagi zdarzeń.  
  
 `tkEventType`  
 podczas Token dla klasy Event. Jest to `mdTypeDef` , a `mdTypeRef` , lub `mdTokenNil` token.  
  
 `mdAddOn`  
 podczas Metoda używana do subskrybowania zdarzenia lub wartość null.  
  
 `mdRemoveOn`  
 podczas Metoda używana do anulowania subskrypcji zdarzenia lub wartość null.  
  
 `mdFire`  
 podczas Metoda używana (przez klasę pochodną) do podniesienia zdarzenia.  
  
 `rmdOtherMethods[]`  
 podczas Tablica tokenów dla innych metod skojarzonych ze zdarzeniem. Tablica została zakończona z `mdMethodDefNil` tokenem.  
  
 `pmdEvent`  
 określoną Token metadanych przypisany do zdarzenia.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).  
  
 **Nagłówek:** Cor. h  
  
 **Biblioteka:** Używany jako zasób w bibliotece MSCorEE. dll  
  
 **.NET Framework wersje:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Zobacz też

- [IMetaDataEmit — Interfejs](imetadataemit-interface.md)
- [IMetaDataEmit2, interfejs](imetadataemit2-interface.md)
