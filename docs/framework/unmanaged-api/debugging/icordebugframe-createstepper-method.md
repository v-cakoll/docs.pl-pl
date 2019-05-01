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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 3fe3cbc4bad83496bcc58aaea60e6724b1d1f06c
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61988900"
---
# <a name="icordebugframecreatestepper-method"></a>ICorDebugFrame::CreateStepper — Metoda
Pobiera stepper, umożliwiająca debugera do wykonywania operacji przechodzenia krok po kroku względem tego ICorDebugFrame.  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT CreateStepper (  
    [out] ICorDebugStepper   **ppStepper  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `ppStepper`  
 [out] Wskaźnik na adres ICorDebugStepper — obiekt, który pozwala debugerowi na wykonywanie operacji przechodzenia krok po kroku względem bieżącej ramki.  
  
## <a name="remarks"></a>Uwagi  
 Jeśli ramki nie jest aktywny, obiekt stepper zwykle musi powrócić do ramki, przed zakończeniem kroku.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorDebug.idl, CorDebug.h  
  
 **Biblioteka:** CorGuids.lib  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
