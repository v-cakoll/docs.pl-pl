---
title: IMetaDataEmit::SetTypeDefProps — Metoda
ms.date: 03/30/2017
api_name:
- IMetaDataEmit.SetTypeDefProps
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit::SetTypeDefProps
helpviewer_keywords:
- SetTypeDefProps method [.NET Framework metadata]
- IMetaDataEmit::SetTypeDefProps method [.NET Framework metadata]
ms.assetid: 480d596a-759f-4d29-ac1a-3dbff8f3544d
topic_type:
- apiref
ms.openlocfilehash: b05527f118de059c674ea659b1a22b7895126cf4
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/27/2020
ms.locfileid: "84007770"
---
# <a name="imetadataemitsettypedefprops-method"></a>IMetaDataEmit::SetTypeDefProps — Metoda
Ustawia funkcje typu zdefiniowanego przez poprzednie wywołanie [IMetaDataEmit::D efinetypedef](imetadataemit-definetypedef-method.md).  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT SetTypeDefProps (  
    [in]  mdTypeDef   td,
    [in]  DWORD       dwTypeDefFlags,
    [in]  mdToken     tkExtends,
    [in]  mdToken     rtkImplements[]
);  
```  
  
## <a name="parameters"></a>Parametry  
 `td`  
 podczas `mdTypeDef`Token uzyskany od oryginalnego wywołania do [IMetaDataEmit::D efinetypedef](imetadataemit-definetypedef-method.md).  
  
 `dwTypeDefFlags`  
 [w] `TypeDef` Attributes. To jest maska bitów `CorTypeAttr` wartości.  
  
 `tkExtends`  
 podczas `mdToken`Klasy podstawowej. Uzyskano od poprzedniego wywołania do [IMetaDataEmit::D efineimporttype](imetadataemit-defineimporttype-method.md)lub `null` .  
  
 `rtkImplements[]`  
 podczas Tablica tokenów dla interfejsów, które implementuje ten typ. Te `mdTypeRef` tokeny są uzyskiwane przy użyciu [IMetaDataEmit::D efineimporttype](imetadataemit-defineimporttype-method.md). Ostatni element tablicy musi być `mdTokenNil` .  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).  
  
 **Nagłówek:** Cor. h  
  
 **Biblioteka:** Używany jako zasób w bibliotece MSCorEE. dll  
  
 **.NET Framework wersje:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Zobacz też

- [IMetaDataEmit — Interfejs](imetadataemit-interface.md)
- [IMetaDataEmit2, interfejs](imetadataemit2-interface.md)
