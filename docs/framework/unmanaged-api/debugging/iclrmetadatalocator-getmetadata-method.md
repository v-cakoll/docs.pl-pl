---
title: "ICLRMetadataLocator::GetMetadata — Metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICLRMetadataLocator.GetMetadata
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICLRMetadataLocator::GetMetadata
helpviewer_keywords:
- GetMetadata method, ICLRMetadataLocator interface [.NET Framework debugging]
- ICLRMetadataLocator::GetMetadata method [.NET Framework debugging]
ms.assetid: 704a8893-ac56-43b4-90ea-715f38ccb40e
topic_type: apiref
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 3e86f61212245c67e701e8619354924770ae5eb6
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="iclrmetadatalocatorgetmetadata-method"></a>ICLRMetadataLocator::GetMetadata — Metoda
Metoda wywoływana przez wspólnego języka środowiska uruchomieniowego (języka wspólnego CLR) dostępu do usług danych do pobierania metadanych obrazu.  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT GetMetadata(  
    [in]  LPCWSTR         imagePath,  
    [in]  ULONG32         imageTimestamp,  
    [in]  ULONG32         imageSize,  
    [in]  GUID*           mvid,  
    [in]  ULONG32         mdRva,  
    [in]  ULONG32         flags,  
    [in]  ULONG32         bufferSize,  
    [out, size_is(bufferSize), length_is(*dataSize)]  
          BYTE*           buffer,  
    [out] ULONG32*        dataSize  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `imagePath`  
 [in] Ciąg, który określa ścieżkę do pliku obrazu.  
  
 `imageTimestamp`  
 [in] Sygnatura czasowa pliku obrazu.  
  
 `imageSize`  
 [in] Rozmiar pliku obrazu.  
  
 `mvid`  
 [in] Globalnie unikatowy identyfikator obrazu.  
  
 `mdRva`  
 [in] Wirtualny adres względny (RVA) metadanych. Adres jest określany względem adresu podstawowego obrazu.  
  
 `flags`  
 [in] Zarezerwowane do użytku w przyszłości.  
  
 `bufferSize`  
 [in] Rozmiar buforu, w której ma zostać umieszczony metadanych.  
  
 `buffer`  
 [out] Bufor, w której ma zostać umieszczony metadanych.  
  
 `dataSize`  
 [out] Rozmiar metadanych, który jest zwracany.  
  
## <a name="remarks"></a>Uwagi  
 Ta metoda jest implementowany przez twórcę debugowania aplikacji.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** ClrData.idl, ClrData.h  
  
 **Biblioteka:** CorGuids.lib  
  
 **Wersje programu .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Zobacz też  
 [ICLRMetadataLocator — interfejs](../../../../docs/framework/unmanaged-api/debugging/iclrmetadatalocator-interface.md)
