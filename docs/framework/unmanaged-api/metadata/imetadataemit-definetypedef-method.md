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
ms.openlocfilehash: 031996813718a074eebab62ff54a2de52b898c22
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/23/2019
ms.locfileid: "74450217"
---
# <a name="imetadataemitdefinetypedef-method"></a>IMetaDataEmit::DefineTypeDef — Metoda
Tworzy definicję typu dla typu środowiska uruchomieniowego języka wspólnego i pobiera token metadanych dla tej definicji typu.  
  
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
 podczas Nazwa typu w formacie Unicode.  
  
 `dwTypeDefFlags`  
 [in] `TypeDef` atrybuty. To jest maska bitów wartości `CoreTypeAttr`.  
  
 `tkExtends`  
 podczas Token klasy bazowej. Musi to być `mdTypeDef` lub token `mdTypeRef`.  
  
 `rtkImplements`  
 podczas Tablica tokenów określająca interfejsy, które implementuje Ta klasa lub interfejs.  
  
 `ptd`  
 określoną Przypisany token `mdTypeDef`.  
  
## <a name="remarks"></a>Uwagi  
 Flaga w `dwTypeDefFlags` określa, czy tworzony typ jest typem referencyjnym systemu typu wspólnego (Class lub Interface) czy typem wartości typu wspólnego systemu.  
  
 W zależności od dostarczonych parametrów, ta metoda jako efekt uboczny może również utworzyć rekord `mdInterfaceImpl` dla każdego interfejsu, który jest dziedziczony lub zaimplementowany przez ten typ. Jednak ta metoda nie zwraca żadnego z tych tokenów `mdInterfaceImpl`. Jeśli klient chce później dodać lub zmodyfikować token `mdInterfaceImpl`, musi użyć interfejsu `IMetaDataImport`, aby je wyliczyć. Jeśli chcesz używać semantyki COM interfejsu `[default]`, należy podać domyślny interfejs jako pierwszy element w `rtkImplements`; niestandardowy atrybut ustawiony dla klasy wskazuje, że Klasa ma interfejs domyślny (który zawsze przyjmuje się, że jest to pierwszy token `mdInterfaceImpl` zadeklarowany dla klasy).  
  
 Każdy element tablicy `rtkImplements` zawiera token `mdTypeDef` lub `mdTypeRef`. Ostatni element w tablicy musi być `mdTokenNil`.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** Cor. h  
  
 **Biblioteka:** Używany jako zasób w bibliotece MSCorEE. dll  
  
 **Wersje .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [IMetaDataEmit, interfejs](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [IMetaDataEmit2, interfejs](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
