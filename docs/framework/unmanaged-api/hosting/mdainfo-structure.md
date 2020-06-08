---
title: MDAInfo — Struktura
ms.date: 03/30/2017
api_name:
- MDAInfo
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- MDAInfo
helpviewer_keywords:
- MDAInfo structure [.NET Framework hosting]
ms.assetid: fb8c14f7-d461-43d1-8b47-adb6723b9b93
topic_type:
- apiref
ms.openlocfilehash: 517e0ae7fb5d5151f94f82d9146ebbf40bad2ef9
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/08/2020
ms.locfileid: "84503864"
---
# <a name="mdainfo-structure"></a>MDAInfo — Struktura
Zawiera szczegółowe informacje o `Event_MDAFired` zdarzeniu, które wyzwala tworzenie zarządzanego asystenta debugowania (MDA).  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
typedef struct _MDAInfo {  
    LPCWSTR  lpMDACaption;  
    LPCWSTR  lpMDAMessage  
} MDAInfo;  
```  
  
## <a name="members"></a>Elementy członkowskie  
  
|Członek|Opis|  
|------------|-----------------|  
|`lpMDACaption`|Tytuł bieżącego elementu MDA. Tytuł opisuje rodzaj błędu, który wyzwolił `Event_MDAFired` zdarzenie.|  
|`lpMDAMessage`|Komunikat wyjściowy dostarczony przez bieżące zdarzenie MDA.|  
  
## <a name="remarks"></a>Uwagi  
 Zarządzane Asystenci debugowania (MDA) to pomoce debugowania, które działają w połączeniu ze środowiskiem uruchomieniowym języka wspólnego (CLR) do wykonywania zadań, takich jak identyfikowanie nieprawidłowych warunków w aparacie wykonawczym środowiska uruchomieniowego lub zatopienie dodatkowych informacji o stanie aparatu. MDA generuje komunikaty XML o zdarzeniach, które w przeciwnym razie trudno jest Zalewka. Są one szczególnie przydatne do debugowania przejść między zarządzanym i niezarządzanym kodem.  
  
 Środowisko uruchomieniowe wykonuje następujące czynności, gdy zostanie wyzwolone zdarzenie wyzwalające utworzenie elementu MDA:  
  
- Jeśli host nie zarejestrował wystąpienia [IActionOnCLREvent](iactiononclrevent-interface.md) przez wywołanie [ICLROnEventManager:: RegisterActionOnEvent —](iclroneventmanager-registeractiononevent-method.md) w celu powiadomienia o `Event_MDAFired` zdarzeniu, środowisko uruchomieniowe kontynuuje działanie z domyślnym, nieobsługiwanym zachowaniem.  
  
- Jeśli host zarejestrował procedurę obsługi dla tego zdarzenia, środowisko uruchomieniowe sprawdzi, czy debuger jest dołączony do procesu. Jeśli tak jest, środowisko uruchomieniowe jest przerywane w debugerze. Gdy debuger kontynuuje działanie, wywołuje hosta. Jeśli debuger nie jest dołączony, środowisko uruchomieniowe wywołuje `IActionOnCLREvent::OnEvent` i przekazuje wskaźnik do `MDAInfo` wystąpienia jako `data` parametr.  
  
 Host może zdecydować się na aktywację MDA i otrzymywanie powiadomień, gdy zostanie uaktywnione zdarzenie MDA. Dzięki temu host może przesłonić domyślne zachowanie i przerwać zarządzany wątek, który wywołał zdarzenie, aby zapobiec uszkodzeniu stanu procesu. Aby uzyskać więcej informacji na temat korzystania z programu MDA, zobacz [Diagnozowanie błędów przy użyciu asystentów zarządzanego debugowania](../../debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md).  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).  
  
 **Nagłówek:** MSCorEE. idl  
  
 **Biblioteka:** Uwzględnione jako zasób w bibliotece MSCorEE. dll  
  
 **.NET Framework wersje:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [Hosting, struktury](hosting-structures.md)
- [Diagnozowanie błędów przy użyciu asystentów zarządzanego debugowania](../../debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)
