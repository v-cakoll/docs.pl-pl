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
ms.openlocfilehash: a9598be850604f16ee8cc62187e1fed7ecf3a7e4
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79175853"
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
 [w] Token dla klasy docelowej lub interfejsu. Jest to token `mdTypeDef` `mdTypeDefNil` lub token.  
  
 `szEvent`  
 [w] Nazwa zdarzenia.  
  
 `dwEventFlags`  
 [w] Flagi zdarzeń.  
  
 `tkEventType`  
 [w] Token dla klasy zdarzenia. Jest to `mdTypeDef`, `mdTypeRef`a `mdTokenNil` , lub token.  
  
 `mdAddOn`  
 [w] Metoda używana do subskrybowania zdarzenia lub null.  
  
 `mdRemoveOn`  
 [w] Metoda używana do anulowania subskrypcji zdarzenia lub null.  
  
 `mdFire`  
 [w] Metoda używana (przez klasę pochodną) do podniesienia zdarzenia.  
  
 `rmdOtherMethods[]`  
 [w] Tablica tokenów dla innych metod skojarzonych ze zdarzeniem. Tablica zostanie zakończona `mdMethodDefNil` tokenem.  
  
 `pmdEvent`  
 [na zewnątrz] Token metadanych przypisany do zdarzenia.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [Wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** Okręg wyborczy Cor.h  
  
 **Biblioteka:** Używany jako zasób w pliku MSCorEE.dll  
  
 **Wersje programu .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Zobacz też

- [IMetaDataEmit — Interfejs](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [IMetaDataEmit2, interfejs](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
