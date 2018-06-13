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
ms.openlocfilehash: 0810ba945c1ed5874dae79704362a399c7349604
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33445825"
---
# <a name="imetadataassemblyimportgetassemblyrefprops-method"></a>IMetaDataAssemblyImport::GetAssemblyRefProps — Metoda
Pobiera zbiór właściwości dla odwołania do zestawu o sygnaturze określonych metadanych.  
  
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
  
#### <a name="parameters"></a>Parametry  
 `mdar`  
 [in] `mdAssemblyRef` Token metadanych, który reprezentuje odwołanie do zestawu, do którego można pobrać właściwości.  
  
 `ppbPublicKeyOrToken`  
 [out] Wskaźnik do klucza publicznego lub token metadanych.  
  
 `pcbPublicKeyOrToken`  
 [out] Liczba bajtów zwróconych publiczny klucza lub tokenu.  
  
 `szName`  
 [out] Prosta nazwa zestawu.  
  
 `cchName`  
 [in] Rozmiar w znaki dwubajtowe z `szName`.  
  
 `pchName`  
 [out] Wskaźnik do liczby znaki dwubajtowe faktycznie zwracane w `szName`.  
  
 `pMetaData`  
 [out] Wskaźnik do struktury assemblymetadata — zawierający metadane zestawu.  
  
 `ppbHashValue`  
 [out] Wskaźnik do wartości skrótu. Jest to wartość skrótu, za pomocą algorytmu SHA-1, z `PublicKey` właściwości zestawu, do którego nastąpiło odwołanie, chyba że arfFullOriginator flagę [AssemblyRefFlags](../../../../docs/framework/unmanaged-api/metadata/assemblyrefflags-enumeration.md) wyliczenie jest ustawiona.  
  
 `pcbHashValue`  
 [out] Liczba szerokości znaków w wartości zwracane wyznaczania wartości skrótu.  
  
 `pdwAssemblyRefFlags`  
 [out] Wskaźnik do flagi opisujące metadanych zastosowany do zestawu. Wartość flagi składa się z co najmniej jeden [CorAssemblyFlags](../../../../docs/framework/unmanaged-api/metadata/corassemblyflags-enumeration.md) wartości.  
  
## <a name="return-value"></a>Wartość zwracana  
 Ten — metoda zwraca wartość S_OK w razie powodzenia; w przeciwnym razie zwraca jeden z kodów błędów zdefiniowanych w pliku nagłówka pliku Winerror.h.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** Cor.h  
  
 **Biblioteka:** używany jako zasób w MsCorEE.dll  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Zobacz też  
 [IMetaDataAssemblyImport, interfejs](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md)
