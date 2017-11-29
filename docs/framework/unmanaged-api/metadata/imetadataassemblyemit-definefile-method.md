---
title: "IMetaDataAssemblyEmit::DefineFile — Metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMetaDataAssemblyEmit.DefineFile
api_location: mscoree.dll
api_type: COM
f1_keywords: IMetaDataAssemblyEmit::DefineFile
helpviewer_keywords:
- IMetaDataAssemblyEmit::DefineFile method [.NET Framework metadata]
- DefineFile method [.NET Framework metadata]
ms.assetid: c065aadf-c1ca-4981-bde6-597042cb29c4
topic_type: apiref
caps.latest.revision: "10"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: f3be44603eb16c6e74b34c0f569fc5bb11264ca0
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="imetadataassemblyemitdefinefile-method"></a>IMetaDataAssemblyEmit::DefineFile — Metoda
Tworzy `File` struktury metadane zawierające metadanych dla zestawu odwołuje się ten zestaw i zwraca token skojarzone metadane.  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT DefineFile (  
    [in]  LPCWSTR        szName,   
    [in]  const void     *pbHashValue,   
    [in]  ULONG          cbHashValue,  
    [in]  DWORD          dwFileFlags,  
    [out] mdFile         *pmdf  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `szName`  
 [in] Nazwa pliku, który ma być używane.  
  
 `pbHashValue`  
 [in] Wskaźnik do wyznaczania wartości skrótu skojarzonych z zestawu danych.  
  
 `cbHashValue`  
 [in] Wyrażony w bajtach rozmiar `pbHashValue`.  
  
 `dwFileFlags`  
 [in] Bitowe połączenie `FileFlags` wartości, które określają ustawienia właściwości.  
  
 `pmdf`  
 [out] Wskaźnik do zwróconego `File` tokenu.  
  
## <a name="remarks"></a>Uwagi  
 Jeden `File` struktura metadanych musi być zdefiniowana dla każdego pliku, który jest częścią tego zestawu w czasie ten zestaw został utworzony, wyłączając plik zawierający metadane.  
  
## <a name="requirements"></a>Wymagania  
 **Platforma:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** Cor.h  
  
 **Biblioteka:** używany jako zasób w MsCorEE.dll  
  
 **Wersje programu .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Zobacz też  
 [IMetaDataAssemblyEmit — interfejs](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-interface.md)
