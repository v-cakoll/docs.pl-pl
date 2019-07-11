---
title: IMetaDataAssemblyImport::GetManifestResourceProps — Metoda
ms.date: 03/30/2017
api_name:
- IMetaDataAssemblyImport.GetManifestResourceProps
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataAssemblyImport::GetManifestResourceProps
helpviewer_keywords:
- GetManifestResourceProps method [.NET Framework metadata]
- IMetaDataAssemblyImport::GetManifestResourceProps method [.NET Framework metadata]
ms.assetid: 00be4789-ac63-4397-b2ec-1629a5c5a585
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: e47b1807e51427487d6af2f96ff5af437c4653eb
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/10/2019
ms.locfileid: "67760946"
---
# <a name="imetadataassemblyimportgetmanifestresourceprops-method"></a>IMetaDataAssemblyImport::GetManifestResourceProps — Metoda
Pobiera zestaw właściwości zasobu manifestu o podpisie określonych metadanych.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT GetManifestResourceProps (  
    [in]  mdManifestResource   mdmr,   
    [out] LPWSTR               szName,   
    [in]  ULONG                cchName,   
    [out] ULONG                *pchName,   
    [out] mdToken              *ptkImplementation,   
    [out] DWORD                *pdwOffset,   
    [out] DWORD                *pdwResourceFlags  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `mdmr`  
 [in] `mdManifestResource` Token reprezentujący zasób, dla którego należy pobrać właściwości.  
  
 `szName`  
 [out] Nazwa zasobu.  
  
 `cchName`  
 [in] Rozmiar w szerokie znaki z `szName`.  
  
 `pchName`  
 [out] Wskaźnik do liczby szerokie znaki rzeczywistego zwrotu w `szName`.  
  
 `ptkImplementation`  
 [out] Wskaźnik do `mdFile` tokenu lub `mdAssemblyRef` token reprezentujący pliku lub zestawu, odpowiednio, który zawiera zasób.  
  
 `pdwOffset`  
 [out] Wskaźnik do wartości, który określa przesunięcie na początku tego zasobu w pliku.  
  
 `pdwResourceFlags`  
 [out] Wskaźnik flagi opisujące metadanych dla zasobu. Wartość flagi składa się z co najmniej jeden [cormanifestresourceflags —](../../../../docs/framework/unmanaged-api/metadata/cormanifestresourceflags-enumeration.md) wartości.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** COR.h  
  
 **Biblioteka:** Używany jako zasób w MsCorEE.dll  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [IMetaDataAssemblyImport, interfejs](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md)
