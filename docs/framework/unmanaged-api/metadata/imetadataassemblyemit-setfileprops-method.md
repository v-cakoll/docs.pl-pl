---
title: IMetaDataAssemblyEmit::SetFileProps — Metoda
ms.date: 03/30/2017
api_name:
- IMetaDataAssemblyEmit.SetFileProps
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataAssemblyEmit::SetFileProps
helpviewer_keywords:
- IMetaDataAssemblyEmit::SetFileProps method [.NET Framework metadata]
- SetFileProps method [.NET Framework metadata]
ms.assetid: 85667d38-611c-45a9-938d-930ac7a7b681
topic_type:
- apiref
ms.openlocfilehash: 9990daea1b097532de53684921d3f10c520a3b1a
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/27/2020
ms.locfileid: "84008069"
---
# <a name="imetadataassemblyemitsetfileprops-method"></a>IMetaDataAssemblyEmit::SetFileProps — Metoda
Modyfikuje określoną `File` strukturę metadanych.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT SetFileProps (  
    [in] mdFile        file,  
    [in] const void    *pbHashValue,
    [in] ULONG         cbHashValue,  
    [in] DWORD         dwFileFlags  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `file`  
 podczas Token metadanych określający `File` strukturę metadanych, która ma zostać zmodyfikowana.  
  
 `pbHashValue`  
 podczas Wskaźnik do danych skrótu skojarzonych z plikiem.  
  
 `cbHashValue`  
 podczas Rozmiar w bajtach `pbHashValue` .  
  
 `dwFileFlags`  
 podczas Bitowa kombinacja wartości [CorFileFlags —](corfileflags-enumeration.md) , które określają różne atrybuty pliku.  
  
## <a name="remarks"></a>Uwagi  
 Aby utworzyć `File` strukturę metadanych, użyj metody [IMetaDataAssemblyEmit::D efinefile](imetadataassemblyemit-definefile-method.md) .  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).  
  
 **Nagłówek:** Cor. h  
  
 **Biblioteka:** Używany jako zasób w bibliotece MsCorEE. dll  
  
 **.NET Framework wersje:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Zobacz też

- [IMetaDataAssemblyEmit — Interfejs](imetadataassemblyemit-interface.md)
