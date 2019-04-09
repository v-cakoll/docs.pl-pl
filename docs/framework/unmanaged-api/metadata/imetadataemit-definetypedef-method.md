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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 9b6f5881f289bed258191baf4f43264ea6ba35db
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59141807"
---
# <a name="imetadataemitdefinetypedef-method"></a>IMetaDataEmit::DefineTypeDef — Metoda
Tworzy definicję typu na typ środowiska uruchomieniowego języka wspólnego, a następnie pobiera token metadanych dla tej definicji typu.  
  
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
  
## <a name="parameters"></a>Parametry  
 `szTypeDef`  
 [in] Nazwa typu w formacie Unicode.  
  
 `dwTypeDefFlags`  
 [in] `TypeDef` atrybutów. Jest to z `CoreTypeAttr` wartości.  
  
 `tkExtends`  
 [in] Token klasy bazowej. Musi być albo `mdTypeDef` lub `mdTypeRef` tokenu.  
  
 `rtkImplements`  
 [in] Tablica Określanie interfejsy, które implementuje tej klasy lub interfejsu.  
  
 `ptd`  
 [out] `mdTypeDef` Token przypisany.  
  
## <a name="remarks"></a>Uwagi  
 Flaga w `dwTypeDefFlags` Określa, czy typ tworzona jest wspólnego typu systemu typu odwołania (klasę lub interfejs) lub typu wartościowego system typu wspólnego.  
  
 W zależności od podanych parametrów tej metody jako efekt uboczny może również utworzyć `mdInterfaceImpl` rekordów dla każdego interfejsu, który jest dziedziczony lub zaimplementować według tego typu. Jednak ta metoda nie zwraca żadnego z tych `mdInterfaceImpl` tokenów. Jeśli klient chce, aby później dodać lub zmodyfikować `mdInterfaceImpl` tokenów, należy użyć `IMetaDataImport` interfejs do wyliczenia. Jeśli chcesz używać COM bezpośrednio z semantyki `[default]` interfejsu, należy podać domyślny interfejs jako pierwszego elementu w `rtkImplements`; atrybutu niestandardowego, ustaw klasy wskaże, że klasa ma domyślnego interfejsu (który jest zawsze zakłada się, że najpierw `mdInterfaceImpl` token zadeklarowana w klasie).  
  
 Każdy element obiektu `rtkImplements` tablica zawierająca `mdTypeDef` lub `mdTypeRef` tokenu. Po ostatnim elemencie w tablicy musi być `mdTokenNil`.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** COR.h  
  
 **Biblioteka:** Używany jako zasób w MSCorEE.dll  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [IMetaDataEmit — Interfejs](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [IMetaDataEmit2 — Interfejs](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
