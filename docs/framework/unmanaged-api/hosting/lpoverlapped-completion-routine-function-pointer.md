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
ms.openlocfilehash: 103ac75e7c3eaf9739c3a448ff1c052c158621db
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73090907"
---
# <a name="lpoverlapped_completion_routine-function-pointer"></a>LPOVERLAPPED_COMPLETION_ROUTINE — Wskaźnik funkcji
Wskazuje funkcję, która powiadamia hosta, gdy nakładają się (czyli asynchroniczne) operacje wejścia/wyjścia do urządzenia.  
  
 Ten wskaźnik funkcji został uznany za przestarzały w .NET Framework 4.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
typedef VOID (*LPOVERLAPPED_COMPLETION_ROUTINE) (  
    [in] DWORD  dwErrorCode,  
    [in] DWORD  dwNumberOfBytesTransfered,  
    [in] LPVOID lpOverlapped  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `dwErrorCode`  
 podczas Wartość, która jest kodem błędu, jeśli urządzenie zostało zamknięte; w przeciwnym razie ta wartość jest równa zero.  
  
 Zamknięcie urządzenia powoduje natychmiastowe zakończenie wszystkich oczekujących operacji we/wy na urządzeniu.  
  
 `dwNumberOfBytesTransfered`  
 podczas Liczba bajtów przesłanych przez operację we/wy.  
  
 `lpOverlapped`  
 podczas Wskaźnik do struktury zawierającej informacje, które mają zostać użyte do ukończenia żądania we/wy.  
  
## <a name="remarks"></a>Uwagi  
 Funkcja, do której punkty `LPOVERLAPPED_COMPLETION_ROUTINE` są funkcją wywołania zwrotnego i musi być implementowana przez moduł zapisujący aplikacji hostingowej. Funkcja wywołania zwrotnego umożliwia hostowi przetwarzanie ukończonego żądania we/wy.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** MSCorEE. h  
  
 **Biblioteka:** MSCorWks. dll  
  
 **Wersje .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [Przestarzałe funkcje hostingu środowiska CLR](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
