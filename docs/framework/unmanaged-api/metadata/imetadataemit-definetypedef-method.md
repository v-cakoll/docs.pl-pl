---
title: "IMetaDataEmit::DefineTypeDef — Metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMetaDataEmit.DefineTypeDef
api_location: mscoree.dll
api_type: COM
f1_keywords: IMetaDataEmit::DefineTypeDef
helpviewer_keywords:
- IMetaDataEmit::DefineTypeDef method [.NET Framework metadata]
- DefineTypeDef method [.NET Framework metadata]
ms.assetid: dd11c485-be95-4b97-9cd8-68679a4fb432
topic_type: apiref
caps.latest.revision: "18"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: a344f592b47d452b4d016f08cefddda650128188
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="imetadataemitdefinetypedef-method"></a>IMetaDataEmit::DefineTypeDef — Metoda
Tworzy definicji typu dla typu środowiska uruchomieniowego języka wspólnego i pobiera token metadanych dla tej definicji typu.  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT DefineTypeDef (   
    [in]  LPCWSTR     szTypeDef,   
    [in]  DWORD       dwTypeDefFlags,   
    [in]  mdToken     tkExtends,   
    [in]  mdToken     rtkImplements[],   
    [out] mdTypeDef   *ptd  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `szTypeDef`  
 [in] Nazwa typu w standardzie Unicode.  
  
 `dwTypeDefFlags`  
 [in] `TypeDef` atrybutów. To jest maską bitów z `CoreTypeAttr` wartości.  
  
 `tkExtends`  
 [in] Token klasy podstawowej. Musi to być albo `mdTypeDef` lub `mdTypeRef` tokenu.  
  
 `rtkImplements`  
 [in] Tablica określenie interfejsów, które implementuje w tej klasy lub interfejsu.  
  
 `ptd`  
 [out] `mdTypeDef` Token przypisany.  
  
## <a name="remarks"></a>Uwagi  
 Flaga w `dwTypeDefFlags` Określa, czy typ tworzony jest wspólnego typu system typu odwołania (klasy lub interfejsu) lub typu wartości system typu wspólnego.  
  
 W zależności od podanych parametrów tej metody jako efekt uboczny może także utworzyć `mdInterfaceImpl` rekordu dla każdego interfejsu, który jest dziedziczone lub zaimplementowany przez tego typu. Jednak ta metoda nie zwraca żadnego z tych adresów `mdInterfaceImpl` tokenów. Jeśli klient będzie chciał później dodać lub zmodyfikować `mdInterfaceImpl` tokenów, należy użyć `IMetaDataImport` interfejs do wyliczenia. Jeśli chcesz użyć semantykę COM `[default]` interfejsu, należy określić domyślnego interfejsu jako pierwszy element w `rtkImplements`; atrybut niestandardowy ustawiony dla klasy wskaże, że klasa ma domyślnego interfejsu (który zawsze zakłada się, że najpierw `mdInterfaceImpl` token zadeklarowana w klasie).  
  
 Każdy element `rtkImplements` tablicy blokad `mdTypeDef` lub `mdTypeRef` tokenu. Ostatni element w tablicy musi być `mdTokenNil`.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** Cor.h  
  
 **Biblioteka:** używany jako zasób w MSCorEE.dll  
  
 **Wersje programu .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Zobacz też  
 [IMetaDataEmit — interfejs](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)  
 [IMetaDataEmit2 — interfejs](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
