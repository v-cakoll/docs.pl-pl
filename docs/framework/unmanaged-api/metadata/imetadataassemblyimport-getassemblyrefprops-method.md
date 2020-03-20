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
ms.openlocfilehash: 9aef471c1155070af0e9bcca14975a65bc5dc763
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79175970"
---
# <a name="imetadataassemblyimportgetassemblyrefprops-method"></a>IMetaDataAssemblyImport::GetAssemblyRefProps — Metoda
Pobiera zestaw właściwości dla odwołania do zestawu z określonym podpisem metadanych.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
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
 [w] Token `mdAssemblyRef` metadanych, który reprezentuje odwołanie do zestawu, dla którego mają zostać właściwości.  
  
 `ppbPublicKeyOrToken`  
 [na zewnątrz] Wskaźnik do klucza publicznego lub tokenu metadanych.  
  
 `pcbPublicKeyOrToken`  
 [na zewnątrz] Liczba bajtów w zwróconym kluczu publicznym lub tokenie.  
  
 `szName`  
 [na zewnątrz] Prosta nazwa zestawu.  
  
 `cchName`  
 [w] Rozmiar, w szerokich znaków, z `szName`.  
  
 `pchName`  
 [na zewnątrz] Wskaźnik do liczby szerokich znaków rzeczywiście `szName`zwrócony w .  
  
 `pMetaData`  
 [na zewnątrz] Wskaźnik do ASSEMBLYMETADATA struktury, która zawiera metadane zestawu.  
  
 `ppbHashValue`  
 [na zewnątrz] Wskaźnik do wartości skrótu. Jest to skrót, przy użyciu algorytmu `PublicKey` SHA-1 właściwości zestawu, do którego odwołuje się, chyba że arfFullOriginator flagi [AssemblyRefFlags wyliczenia](../../../../docs/framework/unmanaged-api/metadata/assemblyrefflags-enumeration.md) jest ustawiona.  
  
 `pcbHashValue`  
 [na zewnątrz] Liczba znaków szerokich w zwróconej wartości skrótu.  
  
 `pdwAssemblyRefFlags`  
 [na zewnątrz] Wskaźnik do flag, które opisują metadane zastosowane do zestawu. Wartość flag jest kombinacją jednej lub więcej wartości [CorAssemblyFlags.](../../../../docs/framework/unmanaged-api/metadata/corassemblyflags-enumeration.md)  
  
## <a name="return-value"></a>Wartość zwracana  
 Ta metoda zwraca S_OK, jeśli zakończy się pomyślnie; w przeciwnym razie zwraca jeden z kodów błędów zdefiniowanych w pliku nagłówka Winerror.h.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [Wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** Okręg wyborczy Cor.h  
  
 **Biblioteka:** Używany jako zasób w pliku MsCorEE.dll  
  
 **Wersje programu .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Zobacz też

- [IMetaDataAssemblyImport — Interfejs](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md)
