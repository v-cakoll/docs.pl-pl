---
title: IMetaDataAssemblyEmit::DefineExportedType — Metoda
ms.date: 03/30/2017
api_name:
- IMetaDataAssemblyEmit.DefineExportedType
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataAssemblyEmit::DefineExportedType
helpviewer_keywords:
- IMetaDataAssemblyEmit::DefineExportedType method [.NET Framework metadata]
- DefineExportedType method [.NET Framework metadata]
ms.assetid: fad01d7a-3178-4c8c-9f0a-4641e3701c9b
topic_type:
- apiref
ms.openlocfilehash: 44f97ef498eb8e64c55fc86b9f290b9e088293f6
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/23/2019
ms.locfileid: "74432070"
---
# <a name="imetadataassemblyemitdefineexportedtype-method"></a>IMetaDataAssemblyEmit::DefineExportedType — Metoda
Tworzy strukturę `ExportedType` zawierającą metadane dla określonego typu wyeksportowanego i zwraca skojarzony token metadanych.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT DefineExportedType (  
    [in]  LPCWSTR             szName,  
    [in]  mdToken             tkImplementation,   
    [in]  mdTypeDef           tkTypeDef,  
    [in]  DWORD               dwExportedTypeFlags,  
    [out] mdExportedType      *pmdct  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `szName`  
 podczas Nazwa typu do wyeksportowania. W przypadku wersji 1,1 środowiska uruchomieniowego języka wspólnego nazwa wyeksportowanego typu musi być dokładnie zgodna z nazwą podaną w `TypeDef` dla tego typu.  
  
 `tkImplementation`  
 podczas Token określający, gdzie jest zaimplementowany wyeksportowany typ. Prawidłowe wartości i ich powiązane znaczenie są następujące:  
  
- `mdFile` typ jest zaimplementowany w innym pliku w tym zestawie.  
  
- `mdAssemblyRef` typ jest zaimplementowany w innym zestawie.  
  
- `mdExportedTYpe` typ jest zagnieżdżony w innym typie.  
  
- `mdFileNil` typ znajduje się w tym samym pliku co manifest i nie jest typem zagnieżdżonym.  
  
 `tkTypeDef`  
 podczas Token do metadanych, który określa typ do wyeksportowania. Ta wartość jest wprowadzana w tabeli `TypeDef` w pliku, który implementuje typ i ma zastosowanie tylko wtedy, gdy ten plik znajduje się w tym zestawie.  
  
 `dwExportedTypeFlags`  
 podczas Bitowa kombinacja wartości wyliczenia [CorTypeAttr —](../../../../docs/framework/unmanaged-api/metadata/cortypeattr-enumeration.md) , które definiują ustawienia właściwości dla wyeksportowanego typu.  
  
 `pmdct`  
 określoną Wskaźnik do zwracanego tokenu metadanych, który wskazuje wyeksportowany typ.  
  
## <a name="remarks"></a>Uwagi  
 Dla każdego typu, który jest udostępniany przez ten zestaw, należy zdefiniować strukturę metadanych `ExportedType`, która jest zaimplementowana w module innym niż ten, który zawiera manifest.  
  
## <a name="requirements"></a>Wymagania  
 **Platforma:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** Cor. h  
  
 **Biblioteka:** Używany jako zasób w bibliotece MsCorEE. dll  
  
 **Wersje .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [IMetaDataAssemblyEmit, interfejs](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-interface.md)
