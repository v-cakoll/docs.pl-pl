---
title: LPOVERLAPPED_COMPLETION_ROUTINE — Wskaźnik funkcji
ms.date: 03/30/2017
api_name:
- LPOVERLAPPED_COMPLETION_ROUTINE
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- LPOVERLAPPED_COMPLETION_ROUTINE
helpviewer_keywords:
- LPOVERLAPPED_COMPLETION_ROUTINE function pointer [.NET Framework hosting]
ms.assetid: 5fb645d9-b818-401c-8c2c-c30d86de58ba
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: cd4b7ffef9c0ba3aba54387245b2d5c9ec1ae906
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33441759"
---
# <a name="lpoverlappedcompletionroutine-function-pointer"></a>LPOVERLAPPED_COMPLETION_ROUTINE — Wskaźnik funkcji
Wskazuje funkcji, które powiadamia hosta przy nakładających się (oznacza to, asynchroniczne) zostało ukończone operacje We/Wy na urządzeniu.  
  
 This, wskaźnik funkcji jest przestarzała w [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)].  
  
## <a name="syntax"></a>Składnia  
  
```  
typedef VOID (*LPOVERLAPPED_COMPLETION_ROUTINE) (  
    [in] DWORD  dwErrorCode,  
    [in] DWORD  dwNumberOfBytesTransfered,  
    [in] LPVOID lpOverlapped  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `dwErrorCode`  
 [in] Wartość, która jest kod błędu, jeśli urządzenie zostało zamknięte; w przeciwnym razie ta wartość wynosi zero.  
  
 Zamykanie urządzenia powoduje, że wszystkie oczekujące operacje We/Wy na urządzeniu należy natychmiast wykonać.  
  
 `dwNumberOfBytesTransfered`  
 [in] Liczba bajtów przesłanych w ramach operacji We/Wy.  
  
 `lpOverlapped`  
 [in] Wskaźnik do struktury, który zawiera informacje, które ma być używany do wykonania żądania We/Wy.  
  
## <a name="remarks"></a>Uwagi  
 Funkcja, do której `LPOVERLAPPED_COMPLETION_ROUTINE` punktów jest funkcją wywołania zwrotnego i musi być implementowana przez Edytor hostingu aplikacji. Funkcja wywołania zwrotnego umożliwia hosta do przetwarzania zakończone żądanie operacji We/Wy.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** MSCorEE.h  
  
 **Biblioteka:** Mscorwks.dll.a;a;pierwsza  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Zobacz też  
 [Przestarzałe funkcje hostingu środowiska CLR](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
