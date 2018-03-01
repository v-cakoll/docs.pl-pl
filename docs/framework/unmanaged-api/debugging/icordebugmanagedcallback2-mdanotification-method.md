---
title: "ICorDebugManagedCallback2::MDANotification — Metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
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
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 5a58e286feb3387557d0a37c463f2af67abf8cc5
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugmanagedcallback2mdanotification-method"></a>ICorDebugManagedCallback2::MDANotification — Metoda
Zapewnia powiadomienie, że wykonywanie kodu napotkał zarządzany Asystent debugowania (MDA) w aplikacji, która jest debugowana.  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT MDANotification(  
    [in] ICorDebugController  *pController,  
    [in] ICorDebugThread      *pThread,  
    [in] ICorDebugMDA         *pMDA  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `pController`  
 [in] Wskaźnik do ICorDebugController — interfejs udostępniający procesu lub domena aplikacji, w którym wystąpił MDA.  
  
 Debuger nie należy podejmować żadnych założeń, czy kontroler jest procesem lub domena aplikacji, mimo że zawsze można wykonać kwerendy interfejs umożliwiający określenie.  
  
 `pThread`  
 [in] Wskaźnik do ICorDebugThread — interfejs udostępniający zarządzanego wątku, w którym wystąpiło zdarzenie debugowania.  
  
 Jeśli MDA wystąpił na niezarządzanego wątku, wartość `pThread` będzie mieć wartość null.  
  
 Od samego obiektu MDA, należy uzyskać identyfikator wątku systemu operacyjnego (systemu operacyjnego).  
  
 `pMDA`  
 [in] Wskaźnik do [ICorDebugMDA](../../../../docs/framework/unmanaged-api/debugging/icordebugmda-interface.md) interfejs, który opisuje informacje o MDA.  
  
## <a name="remarks"></a>Uwagi  
 MDA to ostrzeżenie heurystyczne i nie wymaga żadnych działań jawne debugera, z wyjątkiem wywołania [ICorDebugController::Continue](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-continue-method.md) można wznowić wykonywania aplikacji, która jest debugowana.  
  
 Środowisko uruchomieniowe języka wspólnego (CLR) można określić, którego są uruchamiane mda i dane, które znajduje się w dowolnym danym MDA w dowolnym momencie. W związku z tym debugery nie powinien utworzyć żadnej funkcji, które wymagają określonych wzorców MDA.  
  
 Mda mogą być umieszczone w kolejce i uruchamiany wkrótce po napotkaniu MDA. Może to się zdarzyć, jeśli środowisko uruchomieniowe musi czekać, aż osiągnie punkt bezpieczne dla wyzwalania MDA, zamiast wyzwalania MDA po napotkaniu go. Oznacza to również, że środowisko wykonawcze mogą wyzwalać liczba mda w pojedynczy zestaw umieszczonych w kolejce wywołania zwrotne (podobnie do operacji zdarzeń "Dołącz").  
  
 Debuger powinien zwolnienia odwołania do `ICorDebugMDA` wystąpienia natychmiast po powrocie ze `MDANotification` wywołania zwrotnego, aby umożliwić CLR do odtworzenia pamięci używane przez MDA. Wydanie wystąpienia może zwiększyć wydajność, jeśli wiele mda są wyzwalania.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorDebug.idl, CorDebug.h  
  
 **Biblioteka:** CorGuids.lib  
  
 **Wersje programu .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Zobacz też  
 [Diagnozowanie błędów przy użyciu asystentów zarządzanego debugowania](../../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)  
 [ICorDebugManagedCallback2, interfejs](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback2-interface.md)  
 [ICorDebugManagedCallback, interfejs](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-interface.md)
