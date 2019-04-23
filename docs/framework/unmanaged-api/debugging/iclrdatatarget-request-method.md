---
title: ICLRDataTarget::Request — Metoda
ms.date: 03/30/2017
api_name:
- ICLRDataTarget.Request
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICLRDataTarget::Request
helpviewer_keywords:
- ICLRDataTarget::Request method [.NET Framework debugging]
- Request method [.NET Framework debugging]
ms.assetid: 4723bd1c-eddb-4ed2-897a-010024a47e01
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: e9005dd8fde0d7258bd1dd48b561e4925e87733b
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59102697"
---
# <a name="iclrdatatargetrequest-method"></a>ICLRDataTarget::Request — Metoda
Metoda wywoływana przez wspólnego języka wspólnego (CLR) usługi dostępu do danych do żądania operacji, zgodnie z definicją przez implementację.  
  
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
  
## <a name="parameters"></a>Parametry  
 `reqCode`  
 [in] Zdefiniowane przez użytkownika.  
  
 `inBufferSize`  
 [in] Rozmiar buforu wejściowego, który służy do żądania przychodzącego.  
  
 `inBuffer`  
 [in] Bufor zawierający żądania.  
  
 `outBufferSize`  
 [in] Rozmiar buforu wyjściowego, który służy do odpowiedzi.  
  
 `outBuffer`  
 [out] Bufor, zawierająca odpowiedź.  
  
## <a name="remarks"></a>Uwagi  
 `Request` Metoda ułatwia dodawanie nieokreślony operacjach niestandardowych. Oznacza to, że ta metoda zapewnia rozszerzalność bez konieczności zmiany definicji interfejsu.  
  
 Ta metoda jest implementowana przez moduł zapisujący debugowania aplikacji.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** ClrData.idl, ClrData.h  
  
 **Biblioteka:** CorGuids.lib  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [ICLRDataTarget, interfejs](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget-interface.md)
