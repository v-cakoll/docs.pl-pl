---
title: _EFN_GetManagedExcepStack — Funkcja
ms.date: 03/30/2017
api_name:
- _EFN_GetManagedExcepStack
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- _EFN_GetManagedExcepStack
helpviewer_keywords:
- _EFN_GetManagedExcepStack function [.NET Framework debugging]
ms.assetid: 21ceed9e-62b2-4024-b027-6d095109955a
topic_type:
- apiref
ms.openlocfilehash: 824be4a401d265575b48f66045dd944d521e64a4
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/28/2020
ms.locfileid: "76789154"
---
# <a name="_efn_getmanagedexcepstack-function"></a>\_EFN\_GetManagedExcepStack Function
Dany adres obiektu wyjątku zarządzanego zwraca wersję ciągu śledzenia stosu zawartych wewnątrz.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT _EFN_GetManagedExcepStack(  
    [in]  PDEBUG_CLIENT Client,  
    [in]  ULONG64       StackObjAddr,  
    [out] __out_ecount(cbString) PSTR szStackString,  
    [out] ULONG         cbString  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `Client`  
 podczas Debugowany klient.  
  
 `StackObjAddr`  
 podczas Wskaźnik obiektu zarządzanego pochodzący z <xref:System.Exception>.  
  
 szStackString  
 określoną Zwrócony ciąg.  
  
 `cbString`  
 określoną Liczba znaków dostępnych w buforze ciągów.  
  
## <a name="remarks"></a>Uwagi  
 W przypadku braku kodu zarządzanego w wątku, który jest obecnie w kontekście, funkcja zwraca wartość HRESULT SOS_E_NOMANAGEDCODE z wartością instrumentu 0xa0 i kodem błędu 0x1000.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** SOS_Stacktrace. h  
  
 **Wersja .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [Debugowanie statycznych funkcji globalnych](debugging-global-static-functions.md)
