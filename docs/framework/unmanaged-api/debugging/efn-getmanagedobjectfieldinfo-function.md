---
title: _EFN_GetManagedObjectFieldInfo — Funkcja
ms.date: 03/30/2017
api_name:
- _EFN_GetManagedObjectFieldInfo
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- _EFN_GetManagedObjectFieldInfo
helpviewer_keywords:
- _EFN_GetManagedObjectFieldInfo function [.NET Framework debugging]
ms.assetid: 3b93bcff-62a4-47b2-babc-6bcf4216119a
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: dfa4db00662ed3abffbfd01e6e36005cd272a271
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54664593"
---
# <a name="efngetmanagedobjectfieldinfo-function"></a>_EFN_GetManagedObjectFieldInfo — Funkcja
Pobiera przesunięcie od początku obiektu, do pola i wartość do pola, używając wskaźnika udostępnionego obiektu i nazwy pola.  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT _EFN_GetManagedObjectFieldInfo(  
    [in]  PDEBUG_CLIENT Client,  
    [in]  ULONG64       objAddr,  
    [in]  __out_ecount (mdNameLen) PSTR szFieldName,  
    [out] PULONG64      pValue,  
    [out] PULONG        pOffset  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `Client`  
 [in] Wskaźnik do klienta debugowania.  
  
 `objAddr`  
 [in] Wskaźnik zarządzanego obiektu.  
  
 szFieldName  
 [in] Wskaźnik do obiektu zarządzanego, do nazwy pola.  
  
 `pValue`  
 [out] Wartość pola. Ten parametr może mieć wartości null.  
  
 `pOffset`  
 [out] Przesunięcie od `objAddr` do pola. Ten parametr może mieć wartości null.  
  
## <a name="remarks"></a>Uwagi  
 Przesunięcie wynosi 0, przesunięcie nie zostanie zapisane.  
  
 Jeśli żaden kod zarządzany w wątku obecnie występuje w kontekście, funkcja zwraca HRESULT SOS_E_NOMANAGEDCODE z wartością funkcji 0xa0 i kod błędu 0x1000.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** SOS_Stacktrace.h  
  
 **Wersja programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także
- [Debugowanie statycznych funkcji globalnych](../../../../docs/framework/unmanaged-api/debugging/debugging-global-static-functions.md)
