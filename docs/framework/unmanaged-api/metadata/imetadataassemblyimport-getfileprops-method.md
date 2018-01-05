---
title: "IMetaDataAssemblyImport::GetFileProps — Metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMetaDataAssemblyImport.GetFileProps
api_location: mscoree.dll
api_type: COM
f1_keywords: IMetaDataAssemblyImport::GetFileProps
helpviewer_keywords:
- GetFileProps method [.NET Framework metadata]
- IMetaDataAssemblyImport::GetFileProps method [.NET Framework metadata]
ms.assetid: c5e6216f-ae3d-4697-9688-66b69c1251ec
topic_type: apiref
caps.latest.revision: "10"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 55984c4adaf291e3b962514cdc3bea964d1c91bb
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="imetadataassemblyimportgetfileprops-method"></a>IMetaDataAssemblyImport::GetFileProps — Metoda
Pobiera właściwości pliku podpisem określonych metadanych.  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT GetFileProps (  
    [in]  mdFile      mdf,   
    [out] LPWSTR      szName,   
    [in]  ULONG       cchName,   
    [out] ULONG       *pchName,   
    [out] const void  **ppbHashValue,   
    [out] ULONG       *pcbHashValue,   
    [out] DWORD       *pdwFileFlags  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `mdf`  
 [in] `mdFile` Token metadanych, który reprezentuje plik, dla którego można pobrać właściwości.  
  
 `szName`  
 [out] Prosta nazwa pliku.  
  
 `cchName`  
 [in] Rozmiar w znaki dwubajtowe z `szName`.  
  
 `pchName`  
 [out] Liczba znaki dwubajtowe faktycznie zwracane w `szName`.  
  
 `ppbHashValue`  
 [out] Wskaźnik do wartości skrótu. Jest to wartość skrótu, za pomocą algorytmu SHA-1, w pliku.  
  
 `pcbHashValue`  
 [out] Liczba szerokości znaków w wartości zwracane wyznaczania wartości skrótu.  
  
 `pdwFileFlags`  
 [out] Wskaźnik do flag, które opisują zastosowane w pliku metadanych. Wartość flagi składa się z co najmniej jeden [CorFileFlags](../../../../docs/framework/unmanaged-api/metadata/corfileflags-enumeration.md) wartości.  
  
## <a name="requirements"></a>Wymagania  
 **Platforma:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** Cor.h  
  
 **Biblioteka:** używany jako zasób w MsCorEE.dll  
  
 **Wersje programu .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Zobacz też  
 [IMetaDataAssemblyImport, interfejs](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md)
