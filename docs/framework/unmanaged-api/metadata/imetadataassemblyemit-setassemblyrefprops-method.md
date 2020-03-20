---
title: IMetaDataAssemblyEmit::SetAssemblyRefProps — Metoda
ms.date: 03/30/2017
api_name:
- IMetaDataAssemblyEmit.SetAssemblyRefProps
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataAssemblyEmit::SetAssemblyRefProps
helpviewer_keywords:
- SetAssemblyRefProps method [.NET Framework metadata]
- IMetaDataAssemblyEmit::SetAssemblyRefProps method [.NET Framework metadata]
ms.assetid: 70a32bf3-9051-4f96-ae87-11356d06a073
topic_type:
- apiref
ms.openlocfilehash: 6ad6bbb8a4c69f575bbeba3a297c46e049a97325
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79176048"
---
# <a name="imetadataassemblyemitsetassemblyrefprops-method"></a>IMetaDataAssemblyEmit::SetAssemblyRefProps — Metoda
Modyfikuje `AssemblyRef` strukturę określonych metadanych.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT SetAssemblyRefProps (  
    [in] mdAssemblyRef              ar,  
    [in] const void                 *pbPublicKeyOrToken,  
    [in] ULONG                      cbPublicKeyOrToken,  
    [in] LPCWSTR                    szName,
    [in] const ASSEMBLYMETADATA     *pMetaData,
    [in] const void                 *pbHashValue,  
    [in] ULONG                      cbHashValue,  
    [in] DWORD                      dwAssemblyRefFlags  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `ar`  
 [w] Token metadanych, który `AssemblyRef` określa strukturę metadanych, która ma zostać zmodyfikowana.  
  
 `pbPublicKeyOrToken`  
 [w] Klucz publiczny wydawcy zestawu, do którego istnieje odwołanie.  
  
 `cbPublicKeyOrToken`  
 [w] Rozmiar w bajtach . `pbPublicKeyOrToken`  
  
 `szName`  
 [w] Nazwa tekstowa zestawu czytelna dla człowieka.  
  
 `pMetaData`  
 [w] Wskaźnik do assemblymetadata wystąpienie, który zawiera informacje o wersji, platformy i ustawień regionalnych dla zestawu.  
  
 `pbHashValue`  
 [w] Wskaźnik do danych mieszania skojarzonych z zestawem.  
  
 `cbHashValue`  
 [w] Rozmiar w bajtach . `pbHashValue`  
  
 `dwAssemblyRefFlags`  
 [w] Bitowa kombinacja [AssemblyRefFlags](../../../../docs/framework/unmanaged-api/metadata/assemblyrefflags-enumeration.md) wartości, które określają atrybuty zestawu, do którego istnieje odwołanie.  
  
## <a name="remarks"></a>Uwagi  
 Aby utworzyć `AssemblyRef` strukturę metadanych, należy użyć [metody IMetaDataAssemblyEmit::DefineAssemblyRef.](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-defineassemblyref-method.md)  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [Wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** Okręg wyborczy Cor.h  
  
 **Biblioteka:** Używany jako zasób w pliku MsCorEE.dll  
  
 **Wersje programu .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Zobacz też

- [IMetaDataAssemblyEmit — Interfejs](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-interface.md)
