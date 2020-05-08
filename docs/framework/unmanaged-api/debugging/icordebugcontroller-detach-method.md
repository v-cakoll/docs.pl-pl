---
title: ICorDebugController::Detach — Metoda
ms.date: 03/30/2017
api_name:
- ICorDebugController.Detach
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugController::Detach
helpviewer_keywords:
- Detach method, ICorDebugController interface [.NET Framework debugging]
- ICorDebugController::Detach method [.NET Framework debugging]
ms.assetid: 06fae364-f2c6-4a50-aa7e-3da9f2684dc3
topic_type:
- apiref
ms.openlocfilehash: 480fec4897dac73594515ba8bc0f0e96ceb79ace
ms.sourcegitcommit: 957c49696eaf048c284ef8f9f8ffeb562357ad95
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/07/2020
ms.locfileid: "82892915"
---
# <a name="icordebugcontrollerdetach-method"></a>ICorDebugController::Detach — Metoda
Odłącza debuger od domeny procesu lub aplikacji.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT Detach ();  
```  
  
## <a name="remarks"></a>Uwagi  
 Proces lub domena aplikacji kontynuuje wykonywanie normalnie, ale obiekt "ICorDebugProcess" lub "ICorDebugAppDomain" nie jest już ważny i nie będą wykonywane żadne kolejne wywołania zwrotne.  
  
 W .NET Framework w wersji 2,0, jeśli jest włączone debugowanie niezarządzane, ta metoda zakończy się niepowodzeniem z powodu ograniczeń systemu operacyjnego.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).  
  
 **Nagłówek:** CorDebug. idl, CorDebug. h  
  
 **Biblioteka:** CorGuids. lib  
  
 **.NET Framework wersje:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Zobacz też
