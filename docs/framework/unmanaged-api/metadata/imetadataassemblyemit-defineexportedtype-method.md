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
ms.openlocfilehash: 388f227377ddf73fe1297e1c777bb1c0607c13d2
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79177879"
---
# <a name="imetadataassemblyemitdefineexportedtype-method"></a>IMetaDataAssemblyEmit::DefineExportedType — Metoda
Tworzy `ExportedType` strukturę zawierającą metadane dla określonego typu eksportowanego i zwraca skojarzony token metadanych.  
  
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
 [w] Nazwa typu, który ma zostać wyeksportowany. W przypadku wersji 1.1 środowiska wykonawczego języka wspólnego nazwa eksportowanego typu musi dokładnie `TypeDef` odpowiadać nazwie podanej w dla danego typu.  
  
 `tkImplementation`  
 [w] Token określający, gdzie jest implementowany typ eksportowany. Prawidłowe wartości i związane z nimi znaczenie to:  
  
- `mdFile`Typ jest implementowany w innym pliku w tym zestawie.  
  
- `mdAssemblyRef`Typ jest implementowany w innym zestawie.  
  
- `mdExportedTYpe`Typ jest zagnieżdżony w ramach innego typu.  
  
- `mdFileNil`Typ znajduje się w tym samym pliku co manifest i nie jest typem zagnieżdżonego.  
  
 `tkTypeDef`  
 [w] Token do metadanych, który określa typ do wyeksportowania. Ta wartość jest wprowadzana w `TypeDef` tabeli w pliku, który implementuje typ i jest istotne tylko wtedy, gdy ten plik znajduje się w tym zestawie.  
  
 `dwExportedTypeFlags`  
 [w] Bitowa kombinacja wartości wyliczenia [CorTypeAttr,](../../../../docs/framework/unmanaged-api/metadata/cortypeattr-enumeration.md) które definiują ustawienia właściwości dla eksportowanego typu.  
  
 `pmdct`  
 [na zewnątrz] Wskaźnik do zwróconego tokenu metadanych, który wskazuje eksportowany typ.  
  
## <a name="remarks"></a>Uwagi  
 Struktura `ExportedType` metadanych musi być zdefiniowana dla każdego typu, który jest widoczna przez ten zestaw i który jest implementowany w module innym niż ten zawierający manifest.  
  
## <a name="requirements"></a>Wymagania  
 **Platforma:** Zobacz [Wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** Okręg wyborczy Cor.h  
  
 **Biblioteka:** Używany jako zasób w pliku MsCorEE.dll  
  
 **Wersje programu .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Zobacz też

- [IMetaDataAssemblyEmit — Interfejs](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-interface.md)
