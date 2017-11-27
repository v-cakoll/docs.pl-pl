---
title: "ICLRDataTarget::Request — Metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICLRDataTarget.Request
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICLRDataTarget::Request
helpviewer_keywords:
- ICLRDataTarget::Request method [.NET Framework debugging]
- Request method [.NET Framework debugging]
ms.assetid: 4723bd1c-eddb-4ed2-897a-010024a47e01
topic_type: apiref
caps.latest.revision: "13"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 0e0ce905ea21267419e6a68e73f918de8fc364f3
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="iclrdatatargetrequest-method"></a>ICLRDataTarget::Request — Metoda
Metoda wywoływana przez wspólne języka wspólnego (CLR) danych dostęp do usługi do żądania operacji zdefiniowanej przez implementację.  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT Request (  
    [in] ULONG32            reqCode,  
    [in] ULONG32            inBufferSize,  
    [in, size_is(inBufferSize)]   
        BYTE                *inBuffer,  
    [in] ULONG32            outBufferSize,  
    [out, size_is(outBufferSize)]   
        BYTE                *outBuffer  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `reqCode`  
 [in] Zdefiniowane przez użytkownika.  
  
 `inBufferSize`  
 [in] Rozmiar buforu wejściowego, który służy do żądania przychodzącego.  
  
 `inBuffer`  
 [in] Bufor zawierający żądania.  
  
 `outBufferSize`  
 [in] Rozmiar buforu wyjściowego, który służy do odpowiedzi.  
  
 `outBuffer`  
 [out] Bufor zawierający odpowiedzi.  
  
## <a name="remarks"></a>Uwagi  
 `Request` Metoda ułatwia dodanie nieokreślony operacjach niestandardowych. Oznacza to, że ta metoda zapewnia rozszerzalności bez konieczności zmiany definicji interfejsu.  
  
 Ta metoda jest implementowany przez twórcę debugowania aplikacji.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** ClrData.idl, ClrData.h  
  
 **Biblioteka:** CorGuids.lib  
  
 **Wersje programu .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Zobacz też  
 [ICLRDataTarget — interfejs](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget-interface.md)
