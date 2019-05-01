---
title: IMetaDataAssemblyImport::GetFileProps — Metoda
ms.date: 03/30/2017
api_name:
- IMetaDataAssemblyImport.GetFileProps
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataAssemblyImport::GetFileProps
helpviewer_keywords:
- GetFileProps method [.NET Framework metadata]
- IMetaDataAssemblyImport::GetFileProps method [.NET Framework metadata]
ms.assetid: c5e6216f-ae3d-4697-9688-66b69c1251ec
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: da38c04f5d67dc0220b1828ba0e5cdeb84346bb6
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62044463"
---
# <a name="imetadataassemblyimportgetfileprops-method"></a>IMetaDataAssemblyImport::GetFileProps — Metoda
Pobiera właściwości pliku za pomocą podpisu określonych metadanych.  
  
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
  
## <a name="parameters"></a>Parametry  
 `mdf`  
 [in] `mdFile` Token metadanych, który reprezentuje plik dla którego można pobrać właściwości.  
  
 `szName`  
 [out] Prosta nazwa pliku.  
  
 `cchName`  
 [in] Rozmiar w szerokie znaki z `szName`.  
  
 `pchName`  
 [out] Liczba szerokie znaki rzeczywistego zwrotu w `szName`.  
  
 `ppbHashValue`  
 [out] Wskaźnik do wartości skrótu. Jest to skrót, przy użyciu algorytmu SHA-1 w pliku.  
  
 `pcbHashValue`  
 [out] Liczba szerokie znaki w wartości zwracane wyznaczania wartości skrótu.  
  
 `pdwFileFlags`  
 [out] Wskaźnik flagi, które opisują metadane zastosowane do pliku. Wartość flagi składa się z co najmniej jeden [corfileflags —](../../../../docs/framework/unmanaged-api/metadata/corfileflags-enumeration.md) wartości.  
  
## <a name="requirements"></a>Wymagania  
 **Platforma:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** COR.h  
  
 **Biblioteka:** Używany jako zasób w MsCorEE.dll  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [IMetaDataAssemblyImport, interfejs](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md)
