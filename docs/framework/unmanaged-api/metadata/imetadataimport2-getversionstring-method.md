---
title: "IMetaDataImport2::GetVersionString — Metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMetaDataImport2.GetVersionString
api_location: mscoree.dll
api_type: COM
f1_keywords: IMetaDataImport2::GetVersionString
helpviewer_keywords:
- GetVersionString method, IMetaDataImport2 interface [.NET Framework metadata]
- IMetaDataImport2::GetVersionString method [.NET Framework metadata]
ms.assetid: 308183ee-fd44-4432-9d86-ef00d181b49b
topic_type: apiref
caps.latest.revision: "11"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: d08f43a790305c960d557064539de680a2d04af9
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="imetadataimport2getversionstring-method"></a>IMetaDataImport2::GetVersionString — Metoda
Pobiera numer wersji środowiska uruchomieniowego, który został użyty do budowania zestawu.  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT GetVersionString (  
   [out] LPWSTR      pwzBuf,  
   [in]  DWORD       ccBufSize,  
   [out] DWORD       *pccBufSize  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `pwzBuf`  
 [out] Tablica do przechowywania ciąg, który określa wersję.  
  
 `ccBufSize`  
 [in] Rozmiar w znaki dwubajtowe z `pwzBuf` tablicy.  
  
 `pccBufSize`  
 [out] Liczba znaki dwubajtowe, włącznie z terminatorem null, jest zwracany w `pwzBuf` tablicy.  
  
## <a name="remarks"></a>Uwagi  
 `GetVersionString` Metoda pobiera wersję skompilowany dla bieżącego zakresu metadanych. Jeśli nigdy nie został zapisany zakresu, nie będzie miała skompilowany dla wersji i zostanie zwrócony pusty ciąg.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** Cor.h  
  
 **Biblioteka:** używany jako zasób w MsCorEE.dll  
  
 **Wersje programu .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Zobacz też  
 [IMetaDataImport2 — interfejs](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)  
 [IMetaDataImport — interfejs](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
