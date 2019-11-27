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
ms.openlocfilehash: f11b374ed0ecbfc137c43fb641ae691237604691
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/23/2019
ms.locfileid: "74431517"
---
# <a name="imetadataemitdefineproperty-method"></a>IMetaDataEmit::DefineProperty — Metoda
Tworzy definicję właściwości określonego typu z określonym `get` i metodami dostępu do metody `set` i pobiera token do tej definicji właściwości.  
  
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
 podczas Token klasy lub interfejsu, w którym właściwość jest zdefiniowana.  
  
 `szProperty`  
 podczas Nazwa właściwości.  
  
 `dwPropFlags`  
 podczas Flagi właściwości.  
  
 `pvSig`  
 podczas Podpis właściwości.  
  
 `cbSig`  
 podczas Liczba bajtów w `pvSig`.  
  
 `dwCPlusTypeFlag`  
 podczas Typ wartości domyślnej właściwości.  
  
 `pValue`  
 podczas Wartość domyślna właściwości.  
  
 `cchValue`  
 podczas Liczba znaków (Unicode) w `pValue`.  
  
 `mdSetter`  
 podczas Metoda, która ustawia wartość właściwości.  
  
 `mdGetter`  
 podczas Metoda, która pobiera wartość właściwości.  
  
 `rmdOtherMethods[]`  
 podczas Tablica innych metod skojarzonych z właściwością. Przerwij tablicę przy użyciu `mdTokenNil`.  
  
 `pmdProp`  
 określoną Przypisany token `mdProperty`.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** Cor. h  
  
 **Biblioteka:** Używany jako zasób w bibliotece MSCorEE. dll  
  
 **Wersje .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [IMetaDataEmit, interfejs](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [IMetaDataEmit2, interfejs](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
