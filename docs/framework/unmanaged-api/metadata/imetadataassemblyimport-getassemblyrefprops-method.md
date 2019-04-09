---
title: IMetaDataAssemblyImport::GetAssemblyRefProps — Metoda
ms.date: 03/30/2017
api_name:
- IMetaDataAssemblyImport.GetAssemblyRefProps
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataAssemblyImport::GetAssemblyRefProps
helpviewer_keywords:
- IMetaDataAssemblyImport::GetAssemblyRefProps method [.NET Framework metadata]
- GetAssemblyRefProps method [.NET Framework metadata]
ms.assetid: 5c6b7fb4-cbca-4479-b650-ab9a99732ea0
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: e6c550ff7af2dda8bc06afd771024fe290339904
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59089786"
---
# <a name="imetadataassemblyimportgetassemblyrefprops-method"></a>IMetaDataAssemblyImport::GetAssemblyRefProps — Metoda
Pobiera zbiór właściwości odwołanie do zestawu za pomocą podpisu określonych metadanych.  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT GetAssemblyRefProps (  
    [in]  mdAssemblyRef        mdar,   
    [out] const void          **ppbPublicKeyOrToken,   
    [out] ULONG                *pcbPublicKeyOrToken,   
    [out] LPWSTR               szName,   
    [in]  ULONG                cchName,   
    [out] ULONG                *pchName,   
    [out] ASSEMBLYMETADATA     *pMetaData,   
    [out] const void           **ppbHashValue,   
    [out] ULONG                *pcbHashValue,   
    [out] DWORD                *pdwAssemblyRefFlags  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `mdar`  
 [in] `mdAssemblyRef` Token metadanych, który reprezentuje odwołanie do zestawu dla którego należy pobrać właściwości.  
  
 `ppbPublicKeyOrToken`  
 [out] Wskaźnik do tokenu metadanych lub klucza publicznego.  
  
 `pcbPublicKeyOrToken`  
 [out] Liczba bajtów zwróconych publicznego klucza lub tokenu.  
  
 `szName`  
 [out] Prosta nazwa zestawu.  
  
 `cchName`  
 [in] Rozmiar w szerokie znaki z `szName`.  
  
 `pchName`  
 [out] Wskaźnik do liczby szerokie znaki rzeczywistego zwrotu w `szName`.  
  
 `pMetaData`  
 [out] Wskaźnik do assemblymetadata — struktura, która zawiera metadane zestawu.  
  
 `ppbHashValue`  
 [out] Wskaźnik do wartości skrótu. Jest to skrót, przy użyciu algorytmu SHA-1 z `PublicKey` właściwości zestawu, do którego nastąpiło odwołanie, chyba że flagę arfFullOriginator [assemblyrefflags —](../../../../docs/framework/unmanaged-api/metadata/assemblyrefflags-enumeration.md) ma ustawioną wartość wyliczenia.  
  
 `pcbHashValue`  
 [out] Liczba szerokie znaki w wartości zwracane wyznaczania wartości skrótu.  
  
 `pdwAssemblyRefFlags`  
 [out] Wskaźnik flagi, które opisują metadane zastosowany do zestawu. Wartość flagi składa się z co najmniej jeden [corassemblyflags —](../../../../docs/framework/unmanaged-api/metadata/corassemblyflags-enumeration.md) wartości.  
  
## <a name="return-value"></a>Wartość zwracana  
 Ta metoda zwraca wartość S_OK, jeśli się powiedzie; w przeciwnym razie zwraca jeden z kodów błędów zdefiniowanych w pliku nagłówka w pliku Winerror.h.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** COR.h  
  
 **Biblioteka:** Używany jako zasób w MsCorEE.dll  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [IMetaDataAssemblyImport — Interfejs](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md)
