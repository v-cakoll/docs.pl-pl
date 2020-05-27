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
ms.openlocfilehash: 720133e64c02aa09c9ff7e43a20630b0d55c1acf
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/27/2020
ms.locfileid: "84008758"
---
# <a name="imetadataemitseteventprops-method"></a>IMetaDataEmit::SetEventProps — Metoda
Ustawia lub aktualizuje określoną funkcję zdarzenia zdefiniowaną przez poprzednie wywołanie do [IMetaDataEmit::D efineevent](imetadataemit-defineevent-method.md).  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
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
 podczas Token zdarzenia.  
  
 `dwEventFlags`  
 podczas Flagi zdarzeń. To jest maska bitów `CorEventAttr` wartości.  
  
 `tkEventType`  
 podczas Token dla klasy Event. Jest to albo `mdTypeDef` `mdTypeRef` token.  
  
 `mdAddOn`  
 podczas Metoda używana do subskrybowania zdarzenia lub wartość null.  
  
 `mdRemoveOn`  
 podczas Metoda używana do anulowania subskrypcji zdarzenia lub wartość null.  
  
 `mdFire`  
 podczas Metoda używana (przez klasę pochodną) do podniesienia zdarzenia.  
  
 `rmdOtherMethods[]`  
 podczas Tablica tokenów dla innych metod skojarzonych ze zdarzeniem. Ostatni element tablicy musi być `mdMethodDefNil` .  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).  
  
 **Nagłówek:** Cor. h  
  
 **Biblioteka:** Używany jako zasób w bibliotece MSCorEE. dll  
  
 **.NET Framework wersje:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Zobacz też

- [IMetaDataEmit — Interfejs](imetadataemit-interface.md)
- [IMetaDataEmit2, interfejs](imetadataemit2-interface.md)
