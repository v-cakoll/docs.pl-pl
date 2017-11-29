---
title: "IMetaDataEmit::DefineProperty — Metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMetaDataEmit.DefineProperty
api_location: mscoree.dll
api_type: COM
f1_keywords: IMetaDataEmit::DefineProperty
helpviewer_keywords:
- IMetaDataEmit::DefineProperty method [.NET Framework metadata]
- DefineProperty method [.NET Framework metadata]
ms.assetid: 5c4c1dc2-d40d-4173-bbe6-7058fb21c98f
topic_type: apiref
caps.latest.revision: "10"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: fc0403fd51f028510eb60d93ff96fc7d05606366
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="imetadataemitdefineproperty-method"></a>IMetaDataEmit::DefineProperty — Metoda
Utworzenie definicji właściwości dla określonego typu z określonym `get` i `set` akcesorów — metoda i pobiera token do tej definicji właściwości.  
  
## <a name="syntax"></a>Składnia  
  
```  
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
  
#### <a name="parameters"></a>Parametry  
 `td`  
 [in] Token dla klasy lub interfejsu, na którym jest zdefiniowana właściwość.  
  
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
 [in] Wartość domyślna właściwości.  
  
 `cchValue`  
 [in] Liczba (Unicode) znaków `pValue`.  
  
 `mdSetter`  
 [in] Metoda, która ustawia wartości właściwości.  
  
 `mdGetter`  
 [in] Metoda, która pobiera wartości właściwości.  
  
 `rmdOtherMethods[]`  
 [in] Tablica innych metod skojarzony z właściwością. Przerwanie tablicy o `mdTokenNil`.  
  
 `pmdProp`  
 [out] `mdProperty` Token przypisany.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** Cor.h  
  
 **Biblioteka:** używany jako zasób w MSCorEE.dll  
  
 **Wersje programu .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Zobacz też  
 [IMetaDataEmit — interfejs](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)  
 [IMetaDataEmit2 — interfejs](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
