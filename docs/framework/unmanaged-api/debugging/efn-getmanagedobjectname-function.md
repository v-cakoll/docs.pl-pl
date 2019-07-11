---
title: _EFN_GetManagedObjectName — Funkcja
ms.date: 03/30/2017
api_name:
- _EFN_GetManagedObjectName
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- _EFN_GetManagedObjectName
helpviewer_keywords:
- _EFN_GetManagedObjectName function [.NET Framework debugging]
ms.assetid: 6e7c6bee-7ced-495f-bf6c-2a5f0c716f7e
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: d3490477f30cd1c0badaa9cfd71433a5bf9d7a99
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/10/2019
ms.locfileid: "67738996"
---
# <a name="efngetmanagedobjectname-function"></a>\_EFN\_GetManagedObjectName Function
Pobiera nazwę typu przy użyciu wskaźnika udostępnionego obiektu zarządzanego.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT _EFN_GetManagedObjectName(  
    [in]  PDEBUG_CLIENT  Client,  
    [in]  ULONG64        objAddr,  
    [out] __out_ecount(cbName) PSTR szName,  
    [out] ULONG          cbName  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `Client`  
 [in] Wskaźnik do klienta debugowania.  
  
 `objAddr`  
 [in] Wskaźnik zarządzanego obiektu.  
  
 szName  
 [out] Nazwa typu.  
  
 `cbName`  
 [out] Liczba dostępnych w buforu ciągu znaków.  
  
## <a name="remarks"></a>Uwagi  
 Jeśli żaden kod zarządzany w wątku obecnie występuje w kontekście, funkcja zwraca HRESULT SOS_E_NOMANAGEDCODE z wartością funkcji 0xa0 i kod błędu 0x1000.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** SOS_Stacktrace.h  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [Debugowanie statycznych funkcji globalnych](../../../../docs/framework/unmanaged-api/debugging/debugging-global-static-functions.md)
