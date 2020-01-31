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
ms.openlocfilehash: 0a7e764d89dd42bcaf81da5cf6a16991b6b8a16e
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/28/2020
ms.locfileid: "76793705"
---
# <a name="iclrdatatargetrequest-method"></a>ICLRDataTarget::Request — Metoda
Wywoływane przez usługi dostępu do danych środowiska uruchomieniowego języka wspólnego (CLR) do żądania operacji zgodnie z definicją w implementacji.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
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
 podczas Zdefiniowane przez użytkownika.  
  
 `inBufferSize`  
 podczas Rozmiar buforu wejściowego, który jest używany w żądaniu przychodzącym.  
  
 `inBuffer`  
 podczas Bufor zawierający żądanie.  
  
 `outBufferSize`  
 podczas Rozmiar buforu wyjściowego, który jest używany na potrzeby odpowiedzi.  
  
 `outBuffer`  
 określoną Bufor zawierający odpowiedź.  
  
## <a name="remarks"></a>Uwagi  
 Metoda `Request` ułatwia dodawanie nieokreślonych operacji niestandardowych. Oznacza to, że ta metoda zapewnia rozszerzalność bez konieczności zmiany definicji interfejsu.  
  
 Ta metoda jest implementowana przez moduł zapisujący aplikacji debugowania.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** ClrData. idl, ClrData. h  
  
 **Biblioteka:** CorGuids. lib  
  
 **Wersje .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [ICLRDataTarget, interfejs](iclrdatatarget-interface.md)
