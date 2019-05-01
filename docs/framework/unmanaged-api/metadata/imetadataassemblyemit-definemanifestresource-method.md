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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: b617e29e2df22b59114c8b978daa645de1cc6176
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61905271"
---
# <a name="imetadataassemblyemitdefinemanifestresource-method"></a>IMetaDataAssemblyEmit::DefineManifestResource — Metoda
Tworzy `ManifestResource` struktury zawierającymi metadane dla określonego zasobu manifestu, a następnie zwraca token skojarzone metadane.  
  
## <a name="syntax"></a>Składnia  
  
```  
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
 [in] Nazwa zasobu.  
  
 `tkImplementation`  
 [in] Token metadanych typu `mdtFile` lub `mdtAssemblyRef` która jest mapowana na potrzeby dostawcy zasobów. Wartość NULL wskazuje plik, w której jest osadzony metadanych dostawcy zasobów.  
  
 `dwOffset`  
 [in] Przesunięcie początku zasobu w pliku. Dla zasobów w plikach autonomicznego ta będzie zawsze równa zero. Jeśli zasób jest osadzony w pliku PE (przenośny plik wykonywalny), to przesunięcie obiektu BLOB, który rozpoczyna się w lokalizacji określonej w pliku nagłówkowym cor.h zasobu.  
  
 `dwResourceFlags`  
 [in] Bitowa kombinacja wartości flagi, które określają ustawienia właściwości definicji zasobu.  
  
 `pmdmr`  
 [out] Wskaźnik do tokenu zwróconych metadanych.  
  
## <a name="remarks"></a>Uwagi  
 Jeden `ManifestResource` struktury metadanych musi być zdefiniowana dla każdego zasobu, który jest implementowany w każdym z plików zestawu.  
  
## <a name="requirements"></a>Wymagania  
 **Platforma:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** COR.h  
  
 **Biblioteka:** Używany jako zasób w MsCorEE.dll  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [IMetaDataAssemblyEmit, interfejs](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-interface.md)
