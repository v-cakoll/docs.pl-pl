---
title: IMetaDataEmit::DefineProperty — Metoda
ms.date: 03/30/2017
api_name:
- IMetaDataEmit.DefineProperty
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit::DefineProperty
helpviewer_keywords:
- IMetaDataEmit::DefineProperty method [.NET Framework metadata]
- DefineProperty method [.NET Framework metadata]
ms.assetid: 5c4c1dc2-d40d-4173-bbe6-7058fb21c98f
topic_type:
- apiref
ms.openlocfilehash: eb3ecbf39376e7126b5ec93a26badcbf5076d1db
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79175788"
---
# <a name="imetadataemitdefineproperty-method"></a>IMetaDataEmit::DefineProperty — Metoda
Tworzy definicję właściwości dla określonego typu, z określonymi `get` i `set` akcesorami metod i pobiera token do tej definicji właściwości.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT DefineProperty (
    [in]  mdTypeDef          td,
    [in]  LPCWSTR            szProperty,
    [in]  DWORD              dwPropFlags,
    [in]  PCCOR_SIGNATURE    pvSig,
    [in]  ULONG              cbSig,
    [in]  DWORD              dwCPlusTypeFlag,
    [in]  void const         *pValue,
    [in]  ULONG              cchValue,
    [in]  mdMethodDef        mdSetter,
    [in]  mdMethodDef        mdGetter,
    [in]  mdMethodDef        rmdOtherMethods[],
    [out] mdProperty         *pmdProp
);  
```  
  
## <a name="parameters"></a>Parametry  
 `td`  
 [w] Token dla klasy lub interfejsu, na którym właściwość jest definiowana.  
  
 `szProperty`  
 [w] Nazwa właściwości.  
  
 `dwPropFlags`  
 [w] Flagi właściwości.  
  
 `pvSig`  
 [w] Podpis właściwości.  
  
 `cbSig`  
 [w] Liczba bajtów `pvSig`w pliku .  
  
 `dwCPlusTypeFlag`  
 [w] Typ wartości domyślnej właściwości.  
  
 `pValue`  
 [w] Wartość domyślna właściwości.  
  
 `cchValue`  
 [w] Liczba znaków (Unicode) `pValue`w pliku .  
  
 `mdSetter`  
 [w] Metoda, która ustawia wartość właściwości.  
  
 `mdGetter`  
 [w] Metoda, która pobiera wartość właściwości.  
  
 `rmdOtherMethods[]`  
 [w] Tablica innych metod skojarzonych z właściwością. Zakończ tablicę za `mdTokenNil`pomocą pliku .  
  
 `pmdProp`  
 [na zewnątrz] Token `mdProperty` przypisany.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [Wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** Okręg wyborczy Cor.h  
  
 **Biblioteka:** Używany jako zasób w pliku MSCorEE.dll  
  
 **Wersje programu .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Zobacz też

- [IMetaDataEmit — Interfejs](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [IMetaDataEmit2, interfejs](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
