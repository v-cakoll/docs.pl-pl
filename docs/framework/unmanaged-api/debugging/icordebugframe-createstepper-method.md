---
title: ICorDebugFrame::CreateStepper — Metoda
ms.date: 03/30/2017
api_name:
- ICorDebugFrame.CreateStepper
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugFrame::CreateStepper
helpviewer_keywords:
- ICorDebugFrame::CreateStepper method [.NET Framework debugging]
- CreateStepper method, ICorDebugFrame interface [.NET Framework debugging]
ms.assetid: 689e7f28-20c1-4d5c-9baa-17441cd63a88
topic_type:
- apiref
ms.openlocfilehash: 6ea2b24d37f56a5cb9e6b3dea0d666c8acc719dc
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73091030"
---
# <a name="icordebugframecreatestepper-method"></a>ICorDebugFrame::CreateStepper — Metoda
Pobiera stepper, który umożliwia debugerowi wykonywanie operacji krokowych względem tego ICorDebugFrame.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT CreateStepper (  
    [out] ICorDebugStepper   **ppStepper  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `ppStepper`  
 określoną Wskaźnik do adresu obiektu ICorDebugStepper, który umożliwia debugerowi wykonywanie operacji krokowe względem bieżącej ramki.  
  
## <a name="remarks"></a>Uwagi  
 Jeśli ramka nie jest aktywna, obiekt stepper zazwyczaj będzie musiał powrócić do ramki przed ukończeniem kroku.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorDebug. idl, CorDebug. h  
  
 **Biblioteka:** CorGuids. lib  
  
 **Wersje .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
