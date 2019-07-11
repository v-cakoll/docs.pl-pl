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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 198141545119976cb9107bc9c09b913572e266ce
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/10/2019
ms.locfileid: "67781128"
---
# <a name="mdainfo-structure"></a>MDAInfo — Struktura
Zawiera szczegółowe informacje na temat `Event_MDAFired` zdarzenia, co powoduje wyzwolenie tworzenia zarządzanego Asystenta debugowania (MDA).  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
typedef struct _MDAInfo {  
    LPCWSTR  lpMDACaption;  
    LPCWSTR  lpMDAMessage  
} MDAInfo;  
```  
  
## <a name="members"></a>Elementy członkowskie  
  
|Element członkowski|Opis|  
|------------|-----------------|  
|`lpMDACaption`|Tytuł bieżącego MDA. Tytuł w tym artykule opisano rodzaj błędu, który wyzwolił `Event_MDAFired` zdarzeń.|  
|`lpMDAMessage`|Komunikatu wyjściowego dostarczane przez bieżącego MDA.|  
  
## <a name="remarks"></a>Uwagi  
 Debugowanie — pomoce, które działają w połączeniu z środowisko uruchomieniowe języka wspólnego (CLR) do wykonywania zadań, np. zidentyfikowanie nieprawidłowe warunki w silnika wykonania środowiska uruchomieniowego lub zrzucania dodatkowe informacje na temat stanu asystentów zarządzanego debugowania (mda) aparat. Mda generowania wiadomości XML o zdarzeniach, które w przeciwnym razie są trudne do pułapki. Są one szczególnie przydatne podczas debugowania przejścia między kodem zarządzanym i niezarządzanym.  
  
 Po wyzwoleniu zdarzenia wyzwalającego tworzenia MDA, środowisko uruchomieniowe wykonuje następujące czynności:  
  
- Jeśli host nie został zarejestrowany [iactiononclrevent —](../../../../docs/framework/unmanaged-api/hosting/iactiononclrevent-interface.md) wystąpienia, wywołując [iclroneventmanager::registeractiononevent —](../../../../docs/framework/unmanaged-api/hosting/iclroneventmanager-registeractiononevent-method.md) Aby otrzymywać powiadomienia o `Event_MDAFired` zdarzenia środowiska uruchomieniowego kontynuuje jego Domyślnie-hostowanej działania.  
  
- Jeśli host został zarejestrowany program obsługi dla tego zdarzenia, środowisko uruchomieniowe sprawdza, czy debuger jest dołączony do procesu. Jeśli tak jest, środowisko uruchomieniowe przerywa debugowanie. Gdy debuger będzie nadal występował, wywoła hosta. Jeśli debuger nie jest dołączony, środowisko wykonawcze wywołuje `IActionOnCLREvent::OnEvent` i przekazuje wskaźnik do `MDAInfo` wystąpienia jako `data` parametru.  
  
 Hosta można wybrać, aby aktywować MDA oraz otrzymywać powiadomienia, gdy zdarzenie MDA jest aktywowane. Host daje szansę, aby zastąpić domyślne zachowanie i aby przerwać wątków zarządzanych, która wywołała zdarzenie, aby uniemożliwić uszkodzenia stan procesu. Aby uzyskać więcej informacji na temat używania mda zobacz [diagnozowanie błędów przy użyciu asystentów zarządzanego debugowania](../../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md).  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** MSCorEE.idl  
  
 **Biblioteka:** Dołączony jako zasób w MSCorEE.dll  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [Hosting, struktury](../../../../docs/framework/unmanaged-api/hosting/hosting-structures.md)
- [Diagnozowanie błędów przy użyciu asystentów zarządzanego debugowania](../../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)
