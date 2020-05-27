---
title: IMetaDataEmit::SetPropertyProps — Metoda
ms.date: 03/30/2017
api_name:
- IMetaDataEmit.SetPropertyProps
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit::SetPropertyProps
helpviewer_keywords:
- SetPropertyProps method [.NET Framework metadata]
- IMetaDataEmit::SetPropertyProps method [.NET Framework metadata]
ms.assetid: e2501fc8-b2bc-4dcc-9205-e3acd5a53ffe
topic_type:
- apiref
ms.openlocfilehash: b5af877c26c20bf64a27618bf24a7bce5b410419
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/27/2020
ms.locfileid: "84007783"
---
# <a name="imetadataemitsetpropertyprops-method"></a>IMetaDataEmit::SetPropertyProps — Metoda
Ustawia funkcje przechowywane w metadanych dla właściwości zdefiniowanej przez poprzednie wywołanie [metody DefineProperty —](imetadataemit-defineproperty-method.md).  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT SetPropertyProps (
    [in]  mdProperty      pr,
    [in]  DWORD           dwPropFlags,
    [in]  DWORD           dwCPlusTypeFlag,
    [in]  void const      *pValue,
    [in]  ULONG           cchValue,
    [in]  mdMethodDef     mdSetter,
    [in]  mdMethodDef     mdGetter,
    [in]  mdMethodDef     rmdOtherMethods[]
);  
```  
  
## <a name="parameters"></a>Parametry  
 `pr`  
 podczas Token dla właściwości, która ma zostać zmieniona.  
  
 `dwPropFlags`  
 podczas Flagi właściwości.  
  
 `dwCPlusTypeFlag`  
 podczas Typ wartości domyślnej właściwości.  
  
 `pValue`  
 podczas Wartość domyślna właściwości.  
  
 `cchValue`  
 podczas Liczba znaków (Unicode) w `pValue` .  
  
 `mdSetter`  
 podczas Metoda, która ustawia wartość właściwości.  
  
 `mdGetter`  
 podczas Metoda, która pobiera wartość właściwości.  
  
 `rmdOtherMethods[]`  
 podczas Tablica innych metod skojarzonych z właściwością. Przerwij tę tablicę przy użyciu `mdTokenNil` tokenu.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).  
  
 **Nagłówek:** Cor. h  
  
 **Biblioteka:** Używany jako zasób w bibliotece MSCorEE. dll  
  
 **.NET Framework wersje:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Zobacz też

- [IMetaDataEmit — Interfejs](imetadataemit-interface.md)
- [IMetaDataEmit2, interfejs](imetadataemit2-interface.md)
