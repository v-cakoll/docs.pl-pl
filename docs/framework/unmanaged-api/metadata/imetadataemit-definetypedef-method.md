---
title: IMetaDataEmit::DefineTypeDef — Metoda
ms.date: 03/30/2017
api_name:
- IMetaDataEmit.DefineTypeDef
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit::DefineTypeDef
helpviewer_keywords:
- IMetaDataEmit::DefineTypeDef method [.NET Framework metadata]
- DefineTypeDef method [.NET Framework metadata]
ms.assetid: dd11c485-be95-4b97-9cd8-68679a4fb432
topic_type:
- apiref
ms.openlocfilehash: 4f1c3e823b35fcf7d5935eee111e042b2291d216
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79175762"
---
# <a name="imetadataemitdefinetypedef-method"></a>IMetaDataEmit::DefineTypeDef — Metoda
Tworzy definicję typu dla wspólnego typu środowiska uruchomieniowego języka i pobiera token metadanych dla tej definicji typu.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT DefineTypeDef (
    [in]  LPCWSTR     szTypeDef,
    [in]  DWORD       dwTypeDefFlags,
    [in]  mdToken     tkExtends,
    [in]  mdToken     rtkImplements[],
    [out] mdTypeDef   *ptd  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `szTypeDef`  
 [w] Nazwa typu w Unicode.  
  
 `dwTypeDefFlags`  
 [w] `TypeDef` atrybutów. Jest to maska `CoreTypeAttr` bitowa wartości.  
  
 `tkExtends`  
 [w] Token klasy podstawowej. Musi to być `mdTypeDef` token `mdTypeRef` lub token.  
  
 `rtkImplements`  
 [w] Tablica tokenów określających interfejsy, które implementuje ta klasa lub interfejs.  
  
 `ptd`  
 [na zewnątrz] Token `mdTypeDef` przypisany.  
  
## <a name="remarks"></a>Uwagi  
 Flaga `dwTypeDefFlags` w określa, czy tworzony typ jest typem odwołania do systemu typu typ (klasa lub interfejs) lub typem wartości systemu typu wspólnego.  
  
 W zależności od dostarczonych parametrów ta metoda, jako `mdInterfaceImpl` efekt uboczny, może również utworzyć rekord dla każdego interfejsu, który jest dziedziczony lub implementowany przez ten typ. Jednak ta metoda nie zwraca `mdInterfaceImpl` żadnego z tych tokenów. Jeśli klient chce później dodać lub `mdInterfaceImpl` zmodyfikować token, `IMetaDataImport` musi użyć interfejsu, aby je wyliczyć. Jeśli chcesz użyć semantyki COM `[default]` interfejsu, należy podać domyślny interfejs jako `rtkImplements`pierwszy element w ; atrybut niestandardowy ustawiony w klasie wskazuje, że klasa ma domyślny interfejs (który jest zawsze zakłada się, że jest pierwszym `mdInterfaceImpl` tokenem zadeklarowanym dla klasy).  
  
 Każdy element `rtkImplements` tablicy `mdTypeDef` zawiera `mdTypeRef` lub token. Ostatnim elementem w tablicy musi być `mdTokenNil`.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [Wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** Okręg wyborczy Cor.h  
  
 **Biblioteka:** Używany jako zasób w pliku MSCorEE.dll  
  
 **Wersje programu .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Zobacz też

- [IMetaDataEmit — Interfejs](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [IMetaDataEmit2, interfejs](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
