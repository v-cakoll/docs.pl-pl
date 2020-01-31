---
title: ICorDebugHeapValue, interfejs
ms.date: 03/30/2017
api_name:
- ICorDebugHeapValue
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugHeapValue
helpviewer_keywords:
- ICorDebugHeapValue interface [.NET Framework debugging]
ms.assetid: 1bca66db-0359-4ae8-846e-e35f7e547e8b
topic_type:
- apiref
ms.openlocfilehash: fa31b8a6cc96935319e9bef3e561790b65e33a87
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/28/2020
ms.locfileid: "76777588"
---
# <a name="icordebugheapvalue-interface"></a>ICorDebugHeapValue, interfejs

Podklasa elementu "ICorDebugValue" reprezentująca obiekt, który został zebrany przez moduł zbierający elementy bezużyteczne środowiska uruchomieniowego języka wspólnego (CLR).  
  
## <a name="methods"></a>Metody  
  
|Metoda|Opis|  
|------------|-----------------|  
|[CreateRelocBreakpoint, metoda](icordebugheapvalue-createrelocbreakpoint-method.md)|Nie zaimplementowane.|  
|[IsValid, metoda](icordebugheapvalue-isvalid-method.md)|Pobiera wartość wskazującą, czy obiekt reprezentowany przez ten `ICorDebugHeapValue` jest prawidłowy, czy został odrzucony przez moduł zbierający elementy bezużyteczne. Ta metoda jest przestarzała w .NET Framework w wersji 2,0.|  
  
## <a name="remarks"></a>Uwagi  
  
> [!NOTE]
> Ten interfejs nie obsługuje wywoływania zdalnego na wielu maszynach ani wielu procesów.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorDebug. idl, CorDebug. h  
  
 **Biblioteka:** CorGuids. lib  
  
 **Wersje .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [Debugowanie, interfejsy](debugging-interfaces.md)
