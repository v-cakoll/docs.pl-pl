---
title: IMetaDataAssemblyEmit::DefineManifestResource — Metoda
ms.date: 03/30/2017
api_name:
- IMetaDataAssemblyEmit.DefineManifestResource
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataAssemblyEmit::DefineManifestResource
helpviewer_keywords:
- DefineManifestResource method [.NET Framework metadata]
- IMetaDataAssemblyEmit::DefineManifestResource method [.NET Framework metadata]
ms.assetid: 27f6d295-0fe9-4cda-b77e-6e7d5c53df09
topic_type:
- apiref
ms.openlocfilehash: 83170815f4aa65988bb6a6394bd466a0ba376ebf
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/23/2019
ms.locfileid: "74432050"
---
# <a name="imetadataassemblyemitdefinemanifestresource-method"></a>IMetaDataAssemblyEmit::DefineManifestResource — Metoda
Tworzy strukturę `ManifestResource` zawierającą metadane dla określonego zasobu manifestu i zwraca skojarzony token metadanych.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT DefineManifestResource (  
    [in] LPCWSTR                szName,   
    [in] mdToken                tkImplementation,   
    [in] DWORD                  dwOffset,   
    [in] DWORD                  dwResourceFlags,  
    [out] mdManifestResource    *pmdmr  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `szName`  
 podczas Nazwa zasobu.  
  
 `tkImplementation`  
 podczas Token metadanych typu `mdtFile` lub `mdtAssemblyRef`, który jest mapowany do dostawcy zasobów. Wartość NULL wskazuje, że plik, w którym są osadzone metadane, jest dostawcą zasobów.  
  
 `dwOffset`  
 podczas Przesunięcie do początku zasobu w pliku. W przypadku zasobów w plikach autonomicznych zawsze będzie to zero. Jeśli zasób jest osadzony w pliku PE (przenośny plik wykonywalny), jest to przesunięcie obiektu BLOB zasobu, który jest uruchamiany w lokalizacji określonej w pliku nagłówkowym cor. h.  
  
 `dwResourceFlags`  
 podczas Bitowa kombinacja wartości flag, które określają ustawienia właściwości dla definicji zasobu.  
  
 `pmdmr`  
 określoną Wskaźnik do zwracanego tokenu metadanych.  
  
## <a name="remarks"></a>Uwagi  
 Dla każdego zasobu, który jest zaimplementowany w każdym z plików zestawu, musi być zdefiniowana jedna `ManifestResource` Struktura metadanych.  
  
## <a name="requirements"></a>Wymagania  
 **Platforma:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** Cor. h  
  
 **Biblioteka:** Używany jako zasób w bibliotece MsCorEE. dll  
  
 **Wersje .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [IMetaDataAssemblyEmit, interfejs](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-interface.md)
