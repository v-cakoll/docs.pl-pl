---
title: ICorDebugManagedCallback2::MDANotification — Metoda
ms.date: 03/30/2017
api_name:
- ICorDebugManagedCallback2.MDANotification
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugManagedCallback2::MDANotification
helpviewer_keywords:
- MDANotification method [.NET Framework debugging]
- ICorDebugManagedCallback2::MDANotification method [.NET Framework debugging]
ms.assetid: 93f79627-bd31-4f4f-b95d-46a032a52fe4
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 4011932af6f4b058906c19566e4c1abe96b409db
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/10/2019
ms.locfileid: "67762094"
---
# <a name="icordebugmanagedcallback2mdanotification-method"></a>ICorDebugManagedCallback2::MDANotification — Metoda
Zapewnia powiadomienie napotkała wykonywania kodu zarządzanego Asystenta debugowania (MDA) w aplikacji, która jest debugowana.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT MDANotification(  
    [in] ICorDebugController  *pController,  
    [in] ICorDebugThread      *pThread,  
    [in] ICorDebugMDA         *pMDA  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `pController`  
 [in] Wskaźnik do icordebugcontroller — interfejs, który przedstawia proces ani domeny aplikacji, w którym wystąpiło zdarzenie MDA.  
  
 Debuger nie powinna dokonywać żadnych założeń dotyczących tego, czy ma używać kontroler proces lub domenę aplikacji, mimo że zawsze można wykonać zapytanie interfejsu umożliwiają określenie.  
  
 `pThread`  
 [in] Wskaźnik do icordebugthread — interfejs, który udostępnia wątków zarządzanych, w którym wystąpiło zdarzenie debugowania.  
  
 Jeśli MDA wystąpił na niezarządzanych wątków, wartość `pThread` będzie miał wartość null.  
  
 Identyfikator wątku systemu operacyjnego (OS) należy uzyskać od samego obiektu MDA.  
  
 `pMDA`  
 [in] Wskaźnik do [icordebugmda —](../../../../docs/framework/unmanaged-api/debugging/icordebugmda-interface.md) interfejsu, który udostępnia informacje MDA.  
  
## <a name="remarks"></a>Uwagi  
 MDA heurystyczne ostrzeżenie i nie wymaga żadnych akcji jawne debugera, z wyjątkiem wywoływania [ICorDebugController::Continue](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-continue-method.md) Aby wznowić wykonywanie aplikacji, która jest debugowana.  
  
 Środowisko uruchomieniowe języka wspólnego (CLR) można określić, które są uruchamiane mda i dane, które znajduje się w dowolnym danym MDA w dowolnym momencie. W związku z tym debugery nie należy tworzyć żadnych funkcji wymagających określonych wzorców MDA.  
  
 MDA może być umieszczona w kolejce i uruchamiany wkrótce, po napotkaniu MDA. Może się to zdarzyć, jeśli środowisko wykonawcze musi czekać, aż do napotkania punktu bezpieczne w celu wyzwalania MDA, zamiast wyzwalania MDA po napotkaniu go. Oznacza to również, że środowisko uruchomieniowe może wyzwalać liczba mda w jednym zestawie umieszczonych w kolejce wywołania zwrotne (podobne do operacji zdarzeń "Dołącz").  
  
 Debuger powinien zwolnić odwołanie do `ICorDebugMDA` wystąpienia natychmiast po powrocie z `MDANotification` wywołanie zwrotne, aby umożliwić CLR odtwarzanie pamięci używane przez MDA. Zwalnianie wystąpienie może zwiększyć wydajność, jeśli wiele mda są wyzwalania.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorDebug.idl, CorDebug.h  
  
 **Biblioteka:** CorGuids.lib  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [Diagnozowanie błędów przy użyciu asystentów zarządzanego debugowania](../../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)
- [ICorDebugManagedCallback2, interfejs](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback2-interface.md)
- [ICorDebugManagedCallback, interfejs](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-interface.md)
