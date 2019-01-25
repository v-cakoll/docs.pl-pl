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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 1c1c05918965e40801757462ce53257bc36a5d8c
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54587716"
---
# <a name="efngetmanagedexcepstack-function"></a>_EFN_GetManagedExcepStack — Funkcja
Podany adres obiektu zarządzanego wyjątku zwraca wersję ślad stosu zawarte wewnątrz ciągu.  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT _EFN_GetManagedExcepStack(  
    [in]  PDEBUG_CLIENT Client,  
    [in]  ULONG64       StackObjAddr,  
    [out] __out_ecount(cbString) PSTR szStackString,  
    [out] ULONG         cbString  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `Client`  
 [in] Klient debugowane.  
  
 `StackObjAddr`  
 [in] Wskaźnik do obiektu zarządzanego, pochodzące z <xref:System.Exception>.  
  
 szStackString  
 [out] Zwracanego ciągu.  
  
 `cbString`  
 [out] Liczba dostępnych w buforu ciągu znaków.  
  
## <a name="remarks"></a>Uwagi  
 Jeśli żaden kod zarządzany w wątku obecnie występuje w kontekście, funkcja zwraca HRESULT SOS_E_NOMANAGEDCODE z wartością funkcji 0xa0 i kod błędu 0x1000.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** SOS_Stacktrace.h  
  
 **Wersja programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także
- [Debugowanie statycznych funkcji globalnych](../../../../docs/framework/unmanaged-api/debugging/debugging-global-static-functions.md)
