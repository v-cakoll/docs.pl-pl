---
title: "IMetaDataAssemblyEmit::DefineManifestResource — Metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMetaDataAssemblyEmit.DefineManifestResource
api_location: mscoree.dll
api_type: COM
f1_keywords: IMetaDataAssemblyEmit::DefineManifestResource
helpviewer_keywords:
- DefineManifestResource method [.NET Framework metadata]
- IMetaDataAssemblyEmit::DefineManifestResource method [.NET Framework metadata]
ms.assetid: 27f6d295-0fe9-4cda-b77e-6e7d5c53df09
topic_type: apiref
caps.latest.revision: "9"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 516099f0735e83982fcbab62936bb398c4f7b02d
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="imetadataassemblyemitdefinemanifestresource-method"></a>IMetaDataAssemblyEmit::DefineManifestResource — Metoda
Tworzy `ManifestResource` struktury metadane zawierające dla określonego zasobu manifestu i zwraca token skojarzone metadane.  
  
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
  
#### <a name="parameters"></a>Parametry  
 `szName`  
 [in] Nazwa zasobu.  
  
 `tkImplementation`  
 [in] Token metadanych typu `mdtFile` lub `mdtAssemblyRef` mapujący do dostawcy zasobów. Wartości NULL wskazuje, że plik, w którym jest osadzony metadanych jest dostawcy zasobów.  
  
 `dwOffset`  
 [in] Przesunięcie początku zasobów w pliku. Dla zasobów w plikach autonomicznego ta będzie zawsze równa zero. Jeśli zasób jest osadzony w pliku PE (przenośny plik wykonywalny), to przesunięcie obiektu BLOB, który uruchamia się w lokalizacji określonej w pliku nagłówka cor.h zasobu.  
  
 `dwResourceFlags`  
 [in] Bitowe połączenie wartości flagi, które określają ustawienia właściwości definicji zasobu.  
  
 `pmdmr`  
 [out] Wskaźnik do tokenu metadane zwrócony.  
  
## <a name="remarks"></a>Uwagi  
 Jeden `ManifestResource` struktura metadanych musi być zdefiniowana dla każdego zasobu jest zaimplementowana w każdym z zestawu plików.  
  
## <a name="requirements"></a>Wymagania  
 **Platforma:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** Cor.h  
  
 **Biblioteka:** używany jako zasób w MsCorEE.dll  
  
 **Wersje programu .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Zobacz też  
 [IMetaDataAssemblyEmit — interfejs](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-interface.md)
