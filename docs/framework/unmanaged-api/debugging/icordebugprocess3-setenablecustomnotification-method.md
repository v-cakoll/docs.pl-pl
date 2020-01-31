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
ms.openlocfilehash: f2f365f3fe1568f2dd3bad677dd77a13946002e1
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/28/2020
ms.locfileid: "76792466"
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
 Gdy `fEnable` jest ustawiona na `true`, wywołania metody <xref:System.Diagnostics.Debugger.NotifyOfCrossThreadDependency%2A?displayProperty=nameWithType> wyzwalają wywołanie zwrotne [ICorDebugManagedCallback3:: CustomNotification —](icordebugmanagedcallback3-customnotification-method.md) . Powiadomienia są domyślnie wyłączone; w związku z tym debuger musi określić wszelkie typy powiadomień, o których wie i który chce obsłużyć. Ponieważ Klasa [ICorDebugClass](icordebug-interface.md) jest objęta zakresem przez domenę aplikacji, debuger musi wywoływać `SetEnableCustomNotification` dla każdej domeny aplikacji w procesie, jeśli chce otrzymywać powiadomienie przez cały proces.  
  
 Począwszy od .NET Framework 4, jedyne obsługiwane powiadomienie to powiadomienie obejmujące zależność między wątkami.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorDebug. idl, CorDebug. h  
  
 **Biblioteka:** CorGuids. lib  
  
 **Wersje .NET Framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [ICorDebugProcess3, interfejs](icordebugprocess3-interface.md)
- [Debugowanie, interfejsy](debugging-interfaces.md)
- [Debugowanie](index.md)
