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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 984ec5dea757971081ce05c858788473a0f616e7
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/10/2019
ms.locfileid: "67775275"
---
# <a name="imetadataassemblyemitsetassemblyrefprops-method"></a>IMetaDataAssemblyEmit::SetAssemblyRefProps — Metoda
Modyfikuje określonego `AssemblyRef` struktury metadanych.  
  
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
 [in] Token metadanych, który określa `AssemblyRef` struktury metadanych do zmodyfikowania.  
  
 `pbPublicKeyOrToken`  
 [in] Klucz publiczny wydawcy przywoływanego zestawu.  
  
 `cbPublicKeyOrToken`  
 [in] Rozmiar w bajtach `pbPublicKeyOrToken`.  
  
 `szName`  
 [in] Nazwa tekstowych zrozumiałych zestawu.  
  
 `pMetaData`  
 [in] Wskaźnik na wystąpienie assemblymetadata —, który zawiera informacje o wersji, platformy i ustawienia regionalne dla zestawu.  
  
 `pbHashValue`  
 [in] Wskaźnik do danych wyznaczania wartości skrótu, skojarzone z zestawem.  
  
 `cbHashValue`  
 [in] Rozmiar w bajtach `pbHashValue`.  
  
 `dwAssemblyRefFlags`  
 [in] Bitowa kombinacja [assemblyrefflags —](../../../../docs/framework/unmanaged-api/metadata/assemblyrefflags-enumeration.md) wartości, które określają atrybuty przywoływanego zestawu.  
  
## <a name="remarks"></a>Uwagi  
 Aby utworzyć `AssemblyRef` struktury metadanych, użyj [IMetaDataAssemblyEmit::DefineAssemblyRef](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-defineassemblyref-method.md) metody.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** COR.h  
  
 **Biblioteka:** Używany jako zasób w MsCorEE.dll  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [IMetaDataAssemblyEmit, interfejs](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-interface.md)
