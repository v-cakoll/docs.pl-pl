---
title: StackOverflowInfo — Struktura
ms.date: 03/30/2017
api_name:
- StackOverflowInfo
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- StackOverflowInfo
helpviewer_keywords:
- StackOverflowInfo structure [.NET Framework hosting]
ms.assetid: 519389f2-0217-436c-99d4-93a76ebce5b5
topic_type:
- apiref
ms.openlocfilehash: 1072026f92edbc646653c6dd74ec8e22d5b887e5
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73105920"
---
# <a name="stackoverflowinfo-structure"></a>StackOverflowInfo — Struktura
Przechowuje typ przepełnienia, który wystąpił, i informacje o wyjątku, który został zgłoszony z powodu przepełnienia.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
typedef struct _StackOverflowInfo {  
    StackOverflowType   soType;  
    EXCEPTION_POINTERS  *pExceptionInfo;  
} StackOverflowInfo;  
```  
  
## <a name="members"></a>Elementy członkowskie  
  
|Element członkowski|Opis|  
|------------|-----------------|  
|`soType`|Wartość wyliczenia [StackOverflowType —](../../../../docs/framework/unmanaged-api/hosting/stackoverflowtype-enumeration.md) , która określa typ przepełnienia.|  
|`pExceptionInfo`|Wskaźnik do obiektu Win32 `EXCEPTION_POINTERS`, który zawiera rekord wyjątku z niezależnym od maszyny opis wyjątku i rekordu kontekstu z zależnością od maszyny w momencie wystąpienia wyjątku.|  
  
## <a name="remarks"></a>Uwagi  
 Obiekt `StackOverflowInfo` jest przenoszona do metody [IActionOnCLREvent:: OnEvent](../../../../docs/framework/unmanaged-api/hosting/iactiononclrevent-onevent-method.md) dla zdarzeń `Event_StackOverflow`.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** MSCorEE. idl  
  
 **Biblioteka:** Uwzględnione jako zasób w bibliotece MSCorEE. dll  
  
 **Wersje .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [Hosting, struktury](../../../../docs/framework/unmanaged-api/hosting/hosting-structures.md)
