---
title: LPTHREAD_START_ROUTINE — Wskaźnik funkcji
ms.date: 03/30/2017
api_name:
- LPTHREAD_START_ROUTINE
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- LPTHREAD_START_ROUTINE
helpviewer_keywords:
- LPTHREAD_START_ROUTINE function pointer [.NET Framework hosting]
ms.assetid: 7b9b93b0-fe92-42ba-8693-701168a29dde
topic_type:
- apiref
ms.openlocfilehash: c6e0c02af93b9df726202f397bbb2afc306f3b3a
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73090881"
---
# <a name="lpthread_start_routine-function-pointer"></a>LPTHREAD_START_ROUTINE — Wskaźnik funkcji
Wskazuje funkcję, która powiadamia hosta o rozpoczęciu wykonywania wątku.  
  
 Ten wskaźnik funkcji został uznany za przestarzały w .NET Framework 4.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
typedef DWORD (__stdcall *LPTHREAD_START_ROUTINE) (  
    [in] LPVOID lpThreadParameter  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `lpThreadParameter`  
 podczas Wskaźnik do kodu, który rozpoczął wykonywanie.  
  
## <a name="remarks"></a>Uwagi  
 Funkcja, do której punkty `LPTHREAD_START_ROUTINE` są funkcją wywołania zwrotnego i musi być implementowana przez moduł zapisujący aplikacji hostingowej.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** MSCorEE. h  
  
 **Biblioteka:** MSCorWks. dll  
  
 **Wersje .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [Przestarzałe funkcje hostingu środowiska CLR](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
