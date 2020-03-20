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
ms.openlocfilehash: 5aa5d78faa8ca9261594e2a649b11088e1d78ee7
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79177869"
---
# <a name="imetadataassemblyemitdefinemanifestresource-method"></a>IMetaDataAssemblyEmit::DefineManifestResource — Metoda
Tworzy `ManifestResource` strukturę zawierającą metadane dla określonego zasobu manifestu i zwraca skojarzony token metadanych.  
  
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
 [w] Nazwa zasobu.  
  
 `tkImplementation`  
 [w] Token metadanych `mdtFile` typu `mdtAssemblyRef` lub który jest mapowany do dostawcy zasobów. Wartość NULL wskazuje, że plik, w którym osadzone są metadane, jest dostawcą zasobów.  
  
 `dwOffset`  
 [w] Przesunięcie na początek zasobu w pliku. W przypadku zasobów w plikach autonomicznych zawsze będzie to zero. Jeśli zasób jest osadzony w pliku PE (przenośny plik wykonywalny), jest to przesunięcie obiektu BLOB zasobu, który rozpoczyna się w lokalizacji określonej w pliku nagłówka cor.h.  
  
 `dwResourceFlags`  
 [w] Bitowa kombinacja wartości flagi określających ustawienia właściwości dla definicji zasobu.  
  
 `pmdmr`  
 [na zewnątrz] Wskaźnik do zwróconego tokenu metadanych.  
  
## <a name="remarks"></a>Uwagi  
 Jedna `ManifestResource` struktura metadanych musi być zdefiniowana dla każdego zasobu, który jest implementowany w każdym pliku zestawu.  
  
## <a name="requirements"></a>Wymagania  
 **Platforma:** Zobacz [Wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** Okręg wyborczy Cor.h  
  
 **Biblioteka:** Używany jako zasób w pliku MsCorEE.dll  
  
 **Wersje programu .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Zobacz też

- [IMetaDataAssemblyEmit — Interfejs](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-interface.md)
