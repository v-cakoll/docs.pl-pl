---
title: FLockClrVersionCallback — Wskaźnik funkcji
ms.date: 03/30/2017
api_name:
- FLockClrVersionCallback
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- FLockClrVersionCallback
helpviewer_keywords:
- FLockClrVersionCallback function pointer [.NET Framework hosting]
ms.assetid: 98a4762d-9ad2-45bd-9d03-39064a028b44
topic_type:
- apiref
ms.openlocfilehash: f1ad414c30788801e14a33e98a0893e2a0f58d0c
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73136521"
---
# <a name="flockclrversioncallback-function-pointer"></a>FLockClrVersionCallback — Wskaźnik funkcji
Wskazuje funkcję, którą wywołuje środowisko uruchomieniowe języka wspólnego (CLR), aby wskazać, że inicjalizacja została uruchomiona lub ukończona.  
  
 Ten wskaźnik funkcji został uznany za przestarzały w .NET Framework 4.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
typedef HRESULT (__stdcall *FLockClrVersionCallback) ( );  
```  
  
## <a name="remarks"></a>Uwagi  
 Ta funkcja jest implementowana przez hosta.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** MSCorEE. h  
  
 **Biblioteka:** MSCorWks. dll  
  
 **Wersje .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [LockClrVersion, funkcja](../../../../docs/framework/unmanaged-api/hosting/lockclrversion-function.md)
- [Przestarzałe funkcje hostingu środowiska CLR](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
