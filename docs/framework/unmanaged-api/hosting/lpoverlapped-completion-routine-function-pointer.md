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
ms.openlocfilehash: 59565b28991f6d61ff2c6c77540eace92461aa89
ms.sourcegitcommit: 155012a8a826ee8ab6aa49b1b3a3b532e7b7d9bd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2019
ms.locfileid: "66490174"
---
# <a name="lpoverlappedcompletionroutine-function-pointer"></a>LPOVERLAPPED_COMPLETION_ROUTINE — Wskaźnik funkcji
Wskazuje funkcję, która powiadamia hosta, gdy nakładająca (czyli asynchroniczne) we/wy na urządzeniu została zakończona.  
  
 Ten wskaźnik funkcji jest przestarzała w programie .NET Framework 4.  
  
## <a name="syntax"></a>Składnia  
  
```  
typedef VOID (*LPOVERLAPPED_COMPLETION_ROUTINE) (  
    [in] DWORD  dwErrorCode,  
    [in] DWORD  dwNumberOfBytesTransfered,  
    [in] LPVOID lpOverlapped  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `dwErrorCode`  
 [in] Wartość, która jest kod błędu, jeśli urządzenie zostało zamknięte; w przeciwnym razie ta wartość wynosi zero.  
  
 Zamknięcie urządzenia powoduje, że wszystkie oczekujące operacje We/Wy na urządzeniu należy natychmiast wykonać.  
  
 `dwNumberOfBytesTransfered`  
 [in] Liczba bajtów przesłanych w operacji We/Wy.  
  
 `lpOverlapped`  
 [in] Wskaźnik do struktury, która zawiera informacje, które ma być używany do wykonania żądania We/Wy.  
  
## <a name="remarks"></a>Uwagi  
 Funkcja, do którego `LPOVERLAPPED_COMPLETION_ROUTINE` punktów jest funkcją wywołania zwrotnego i musi być implementowana przez moduł zapisujący aplikacji macierzystej. Funkcja wywołania zwrotnego Zezwalaj hostowi na przetwarzanie zakończone żądanie operacji We/Wy.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** MSCorEE.h  
  
 **Biblioteka:** MSCorWks.dll  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [Przestarzałe funkcje hostingu środowiska CLR](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
