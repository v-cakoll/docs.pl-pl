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
ms.openlocfilehash: fb381a872cbeb787da0c6920f2cdeef434fb33ea
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/27/2020
ms.locfileid: "84008095"
---
# <a name="imetadataassemblyemitsetassemblyrefprops-method"></a>IMetaDataAssemblyEmit::SetAssemblyRefProps — Metoda
Modyfikuje określoną `AssemblyRef` strukturę metadanych.  
  
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
 podczas Token metadanych określający `AssemblyRef` strukturę metadanych, która ma zostać zmodyfikowana.  
  
 `pbPublicKeyOrToken`  
 podczas Klucz publiczny wydawcy przywoływanego zestawu.  
  
 `cbPublicKeyOrToken`  
 podczas Rozmiar w bajtach `pbPublicKeyOrToken` .  
  
 `szName`  
 podczas Nazwa tekstu do odczytania przez człowieka.  
  
 `pMetaData`  
 podczas Wskaźnik do wystąpienia ASSEMBLYMETADATA, który zawiera wersję, platformę i informacje o ustawieniach regionalnych dla zestawu.  
  
 `pbHashValue`  
 podczas Wskaźnik do danych skrótu skojarzonych z zestawem.  
  
 `cbHashValue`  
 podczas Rozmiar w bajtach `pbHashValue` .  
  
 `dwAssemblyRefFlags`  
 podczas Bitowa kombinacja wartości [AssemblyRefFlags —](assemblyrefflags-enumeration.md) , które określają atrybuty przywoływanego zestawu.  
  
## <a name="remarks"></a>Uwagi  
 Aby utworzyć `AssemblyRef` strukturę metadanych, użyj metody [IMetaDataAssemblyEmit::D efineassemblyref](imetadataassemblyemit-defineassemblyref-method.md) .  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).  
  
 **Nagłówek:** Cor. h  
  
 **Biblioteka:** Używany jako zasób w bibliotece MsCorEE. dll  
  
 **.NET Framework wersje:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Zobacz też

- [IMetaDataAssemblyEmit — Interfejs](imetadataassemblyemit-interface.md)
