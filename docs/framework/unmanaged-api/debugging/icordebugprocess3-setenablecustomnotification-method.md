---
title: ICorDebugProcess3::SetEnableCustomNotification — Metoda
ms.date: 03/30/2017
api_name:
- ICorDebugProcess3.SetEnableCustomNotification Method
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugProcess3::SetEnableCustomNotification
helpviewer_keywords:
- ICorDebugProcess3::SetEnableCustomNotification method [.NET Framework debugging]
- SetEnableCustomNotification method [.NET Framework debugging]
ms.assetid: afd88ee9-2589-4461-a75a-9b6fe55a2525
topic_type:
- apiref
ms.openlocfilehash: ec60274648315c4fa38f3832d8d39c1a269956b1
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73129706"
---
# <a name="icordebugprocess3setenablecustomnotification-method"></a>ICorDebugProcess3::SetEnableCustomNotification — Metoda
Włącza i wyłącza niestandardowe powiadomienia debugera określonego typu.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT SetEnableCustomNotification(ICorDebugClass * pClass,  
                                    BOOL fEnable);  
```  
  
## <a name="parameters"></a>Parametry  
 `pClass`  
 podczas Typ, który określa niestandardowe powiadomienia debugera.  
  
 `fEnable`  
 [in] `true` włączyć powiadomień debugera niestandardowego; `false` wyłączyć powiadomienia. Wartość domyślna to `false`.  
  
## <a name="remarks"></a>Uwagi  
 Gdy `fEnable` jest ustawiona na `true`, wywołania metody <xref:System.Diagnostics.Debugger.NotifyOfCrossThreadDependency%2A?displayProperty=nameWithType> wyzwalają wywołanie zwrotne [ICorDebugManagedCallback3:: CustomNotification —](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback3-customnotification-method.md) . Powiadomienia są domyślnie wyłączone; w związku z tym debuger musi określić wszelkie typy powiadomień, o których wie i który chce obsłużyć. Ponieważ Klasa [ICorDebugClass](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md) jest objęta zakresem przez domenę aplikacji, debuger musi wywoływać `SetEnableCustomNotification` dla każdej domeny aplikacji w procesie, jeśli chce otrzymywać powiadomienie przez cały proces.  
  
 Począwszy od .NET Framework 4, jedyne obsługiwane powiadomienie to powiadomienie obejmujące zależność między wątkami.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorDebug. idl, CorDebug. h  
  
 **Biblioteka:** CorGuids. lib  
  
 **Wersje .NET Framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [ICorDebugProcess3, interfejs](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess3-interface.md)
- [Debugowanie, interfejsy](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [Debugowanie](../../../../docs/framework/unmanaged-api/debugging/index.md)
