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
ms.openlocfilehash: dfa900e2184a8c415d75f5702c572b14c4018749
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79177790"
---
# <a name="imetadataassemblyimportgetassemblyprops-method"></a>IMetaDataAssemblyImport::GetAssemblyProps — Metoda
Pobiera zestaw właściwości dla zestawu z określonym podpisem metadanych.  
  
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
 [w]. Token `mdAssembly` metadanych, który reprezentuje zestaw, dla którego mają zostać właściwości.  
  
 `ppbPublicKey`  
 [na zewnątrz] Wskaźnik do klucza publicznego lub tokenu metadanych.  
  
 `pcbPublicKey`  
 [na zewnątrz] Liczba bajtów w zwróconym kluczu publicznym.  
  
 `pulHashAlgId`  
 [na zewnątrz] Wskaźnik do algorytmu używanego do mieszania plików w zestawie.  
  
 `szName`  
 [na zewnątrz] Prosta nazwa zestawu.  
  
 `cchName`  
 [w] Rozmiar, w szerokich znaków, z `szName`.  
  
 `pchName`  
 [na zewnątrz] Liczba szerokich znaków rzeczywiście `szName`zwrócona w .  
  
 `pMetaData`  
 [na zewnątrz] Wskaźnik do ASSEMBLYMETADATA struktury, która zawiera metadane zestawu.  
  
 `pdwAssemblyFlags`  
 [na zewnątrz] Flagi opisujące metadane zastosowane do zestawu. Ta wartość jest kombinacją jednej lub więcej wartości [CorAssemblyFlags.](../../../../docs/framework/unmanaged-api/metadata/corassemblyflags-enumeration.md)  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [Wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** Okręg wyborczy Cor.h  
  
 **Biblioteka:** Używany jako zasób w pliku MsCorEE.dll  
  
 **Wersje programu .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Zobacz też

- [IMetaDataAssemblyImport — Interfejs](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md)
