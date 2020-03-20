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
ms.openlocfilehash: 336ba38bc80fcb2649a12c78691e52c5e4d70bfe
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79179114"
---
# <a name="iclrdatatargetrequest-method"></a>ICLRDataTarget::Request — Metoda
Wywoływane przez usługi dostępu do danych środowiska wykonawczego języka wspólnego (CLR) do żądania operacji, zgodnie z definicją implementacji.  
  
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
 [w] Zdefiniowane przez użytkownika.  
  
 `inBufferSize`  
 [w] Rozmiar buforu wejściowego, który jest używany dla żądania przychodzącego.  
  
 `inBuffer`  
 [w] Bufor zawierający żądanie.  
  
 `outBufferSize`  
 [w] Rozmiar buforu wyjściowego, który jest używany dla odpowiedzi.  
  
 `outBuffer`  
 [na zewnątrz] Bufor zawierający odpowiedź.  
  
## <a name="remarks"></a>Uwagi  
 Metoda `Request` ułatwia dodawanie nieokreślonych operacji niestandardowych. Oznacza to, że ta metoda zapewnia rozszerzalność bez konieczności zmiany definicji interfejsu.  
  
 Ta metoda jest implementowana przez moduł zapisujący aplikacji debugowania.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [Wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** ClrData.idl, ClrData.h  
  
 **Biblioteka:** CorGuids.lib  
  
 **Wersje programu .NET Framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Zobacz też

- [ICLRDataTarget, interfejs](iclrdatatarget-interface.md)
