---
title: "ICorDebugFrame::CreateStepper — Metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugFrame.CreateStepper
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugFrame::CreateStepper
helpviewer_keywords:
- ICorDebugFrame::CreateStepper method [.NET Framework debugging]
- CreateStepper method, ICorDebugFrame interface [.NET Framework debugging]
ms.assetid: 689e7f28-20c1-4d5c-9baa-17441cd63a88
topic_type: apiref
caps.latest.revision: "12"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: a6f575febc488d01700c32198d4c00916dd5e249
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="icordebugframecreatestepper-method"></a>ICorDebugFrame::CreateStepper — Metoda
Pobiera stepper, umożliwiający debugera do wykonywania operacji wykonywania krokowego względem tego ICorDebugFrame.  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT CreateStepper (  
    [out] ICorDebugStepper   **ppStepper  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `ppStepper`  
 [out] Wskaźnik do adres obiektu ICorDebugStepper — który umożliwia debugera do wykonywania operacji wykonywania krokowego względem bieżącej ramki.  
  
## <a name="remarks"></a>Uwagi  
 Jeśli ramka nie jest aktywne, zwykle mają obiektu stepper powrócić do ramki, przed zakończeniem kroku.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorDebug.idl, CorDebug.h  
  
 **Biblioteka:** CorGuids.lib  
  
 **Wersje programu .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
