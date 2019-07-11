---
title: IMetaDataAssemblyImport::GetAssemblyProps — Metoda
ms.date: 03/30/2017
api_name:
- IMetaDataAssemblyImport.GetAssemblyProps
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataAssemblyImport::GetAssemblyProps
helpviewer_keywords:
- GetAssemblyProps method [.NET Framework metadata]
- IMetaDataAssemblyImport::GetAssemblyProps method [.NET Framework metadata]
ms.assetid: 0eaa4aa9-9441-444a-920c-e4b2a2db899e
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: ec04588bd1cc21e585d89c734c152a86fb835b15
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/10/2019
ms.locfileid: "67772722"
---
# <a name="imetadataassemblyimportgetassemblyprops-method"></a>IMetaDataAssemblyImport::GetAssemblyProps — Metoda
Pobiera zbiór właściwości dla zestawu podpisem określonych metadanych.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT GetAssemblyProps (  
    [in]  mdAssembly          mda,  
    [out] const void          **ppbPublicKey,   
    [out] ULONG               *pcbPublicKey,  
    [out] ULONG               *pulHashAlgId,  
    [out] LPWSTR              szName,  
    [in] ULONG                cchName,  
    [out] ULONG               *pchName,  
    [out] ASSEMBLYMETADATA    *pMetaData,  
    [out] DWORD               *pdwAssemblyFlags  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `mda`  
 [in]. `mdAssembly` Token metadanych, który reprezentuje zestaw, dla którego można pobrać właściwości.  
  
 `ppbPublicKey`  
 [out] Wskaźnik do tokenu metadanych lub klucza publicznego.  
  
 `pcbPublicKey`  
 [out] Liczba bajtów zwróconych klucza publicznego.  
  
 `pulHashAlgId`  
 [out] Wskaźnik do algorytm wyznaczania wartości skrótu dla plików w zestawie.  
  
 `szName`  
 [out] Prosta nazwa zestawu.  
  
 `cchName`  
 [in] Rozmiar w szerokie znaki z `szName`.  
  
 `pchName`  
 [out] Liczba szerokie znaki rzeczywistego zwrotu w `szName`.  
  
 `pMetaData`  
 [out] Wskaźnik do assemblymetadata — struktura, która zawiera metadane zestawu.  
  
 `pdwAssemblyFlags`  
 [out] Flagi, które opisują metadane zastosowany do zestawu. Ta wartość składa się z co najmniej jeden [corassemblyflags —](../../../../docs/framework/unmanaged-api/metadata/corassemblyflags-enumeration.md) wartości.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** COR.h  
  
 **Biblioteka:** Używany jako zasób w MsCorEE.dll  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [IMetaDataAssemblyImport, interfejs](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md)
