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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 69b398fa003abc0dba00ee89a9bb911a8c2dd6df
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/10/2019
ms.locfileid: "67777514"
---
# <a name="imetadataemitdefineproperty-method"></a>IMetaDataEmit::DefineProperty — Metoda
Utworzenie definicji właściwości dla określonego typu z określonego `get` i `set` metod dostępu do metody, a następnie pobiera token do tej definicji właściwości.  
  
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
 [in] Token dla klasy lub interfejsu, w którym właściwość jest zdefiniowana.  
  
 `szProperty`  
 [in] Nazwa właściwości.  
  
 `dwPropFlags`  
 [in] Flagi właściwości.  
  
 `pvSig`  
 [in] Podpis właściwości.  
  
 `cbSig`  
 [in] Liczba bajtów w `pvSig`.  
  
 `dwCPlusTypeFlag`  
 [in] Typ wartości domyślnej właściwości.  
  
 `pValue`  
 [in] Wartość domyślna dla właściwości.  
  
 `cchValue`  
 [in] Liczba (Unicode) znaki w `pValue`.  
  
 `mdSetter`  
 [in] Metoda, która ustawia wartości właściwości.  
  
 `mdGetter`  
 [in] Metoda, która pobiera wartość właściwości.  
  
 `rmdOtherMethods[]`  
 [in] Tablica innych metod skojarzony z właściwością. Zakończenie tablicy przy użyciu `mdTokenNil`.  
  
 `pmdProp`  
 [out] `mdProperty` Token przypisany.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** COR.h  
  
 **Biblioteka:** Używany jako zasób w MSCorEE.dll  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [IMetaDataEmit, interfejs](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [IMetaDataEmit2, interfejs](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
