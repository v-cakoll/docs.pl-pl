---
title: ICLRMetadataLocator::GetMetadata — Metoda
ms.date: 03/30/2017
api_name:
- ICLRMetadataLocator.GetMetadata
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICLRMetadataLocator::GetMetadata
helpviewer_keywords:
- GetMetadata method, ICLRMetadataLocator interface [.NET Framework debugging]
- ICLRMetadataLocator::GetMetadata method [.NET Framework debugging]
ms.assetid: 704a8893-ac56-43b4-90ea-715f38ccb40e
topic_type:
- apiref
ms.openlocfilehash: 1f28a4b4acd9d6050d33b9824aa49a9b9041b59b
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73111251"
---
# <a name="iclrmetadatalocatorgetmetadata-method"></a>ICLRMetadataLocator::GetMetadata — Metoda
Wywoływane przez usługi dostępu do danych środowiska uruchomieniowego języka wspólnego (CLR) do pobierania metadanych obrazu.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
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
  
## <a name="parameters"></a>Parametry  
 `imagePath`  
 podczas Ciąg określający ścieżkę pliku obrazu.  
  
 `imageTimestamp`  
 podczas Sygnatura czasowa pliku obrazu.  
  
 `imageSize`  
 podczas Rozmiar pliku obrazu.  
  
 `mvid`  
 podczas Unikatowy identyfikator globalny obrazu.  
  
 `mdRva`  
 podczas Względny adres wirtualny (RVA) metadanych. Adres jest określany względem adresu podstawowego obrazu.  
  
 `flags`  
 podczas Zarezerwowane do użytku w przyszłości.  
  
 `bufferSize`  
 podczas Rozmiar buforu, w którym mają zostać umieszczone metadane.  
  
 `buffer`  
 określoną Bufor, w którym mają zostać umieszczone metadane.  
  
 `dataSize`  
 określoną Rozmiar zwracanych metadanych.  
  
## <a name="remarks"></a>Uwagi  
 Ta metoda jest implementowana przez moduł zapisujący aplikacji debugowania.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** ClrData. idl, ClrData. h  
  
 **Biblioteka:** CorGuids. lib  
  
 **Wersje .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [ICLRMetadataLocator, interfejs](../../../../docs/framework/unmanaged-api/debugging/iclrmetadatalocator-interface.md)
