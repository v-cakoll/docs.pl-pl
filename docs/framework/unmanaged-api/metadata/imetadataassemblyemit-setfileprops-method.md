---
title: "IMetaDataAssemblyEmit::SetFileProps — Metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMetaDataAssemblyEmit.SetFileProps
api_location: mscoree.dll
api_type: COM
f1_keywords: IMetaDataAssemblyEmit::SetFileProps
helpviewer_keywords:
- IMetaDataAssemblyEmit::SetFileProps method [.NET Framework metadata]
- SetFileProps method [.NET Framework metadata]
ms.assetid: 85667d38-611c-45a9-938d-930ac7a7b681
topic_type: apiref
caps.latest.revision: "12"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: f179ce3e54a5229423d7267cd52a97edef3b619d
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="imetadataassemblyemitsetfileprops-method"></a>IMetaDataAssemblyEmit::SetFileProps — Metoda
Modyfikuje określony `File` struktura metadanych.  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT SetFileProps (  
    [in] mdFile        file,  
    [in] const void    *pbHashValue,   
    [in] ULONG         cbHashValue,  
    [in] DWORD         dwFileFlags  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `file`  
 [in] Token metadanych, który określa `File` struktura metadanych ma być zmodyfikowana.  
  
 `pbHashValue`  
 [in] Wskaźnik do wyznaczania wartości skrótu danych skojarzonych z plikiem.  
  
 `cbHashValue`  
 [in] Wyrażony w bajtach rozmiar `pbHashValue`.  
  
 `dwFileFlags`  
 [in] Bitowe połączenie [CorFileFlags](../../../../docs/framework/unmanaged-api/metadata/corfileflags-enumeration.md) wartości, które określają różne atrybuty pliku.  
  
## <a name="remarks"></a>Uwagi  
 Aby utworzyć `File` metadanych struktury, użyj [IMetaDataAssemblyEmit::DefineFile](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-definefile-method.md) metody.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** Cor.h  
  
 **Biblioteka:** używany jako zasób w MsCorEE.dll  
  
 **Wersje programu .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Zobacz też  
 [IMetaDataAssemblyEmit — interfejs](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-interface.md)
