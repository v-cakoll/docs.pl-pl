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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 46e3356df6578f2adf2ceee00b1363b65fd014ea
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/10/2019
ms.locfileid: "67760229"
---
# <a name="flockclrversioncallback-function-pointer"></a>FLockClrVersionCallback — Wskaźnik funkcji
Wskazuje funkcję, która Typowe wywołania środowiska uruchomieniowego (języka wspólnego CLR) języka, aby wskazać, że inicjowanie uruchomiona lub ukończone.  
  
 Ten wskaźnik funkcji jest przestarzała w programie .NET Framework 4.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
typedef HRESULT (__stdcall *FLockClrVersionCallback) ( );  
```  
  
## <a name="remarks"></a>Uwagi  
 Ta funkcja jest zaimplementowana przez hosta.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** MSCorEE.h  
  
 **Biblioteka:** MSCorWks.dll  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [LockClrVersion, funkcja](../../../../docs/framework/unmanaged-api/hosting/lockclrversion-function.md)
- [Przestarzałe funkcje hostingu środowiska CLR](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
