---
title: "ICorDebugController::Detach — Metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugController.Detach
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugController::Detach
helpviewer_keywords:
- Detach method, ICorDebugController interface [.NET Framework debugging]
- ICorDebugController::Detach method [.NET Framework debugging]
ms.assetid: 06fae364-f2c6-4a50-aa7e-3da9f2684dc3
topic_type: apiref
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 2d8c1df2fd2aa52f9f5e90a27d42f6568686e908
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="icordebugcontrollerdetach-method"></a>ICorDebugController::Detach — Metoda
Odłącza debugera z domeny proces lub aplikacji.  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT Detach ();  
```  
  
## <a name="remarks"></a>Uwagi  
 Domeny aplikacji lub proces kontynuuje wykonywanie, ale obiektu "ICorDebugProcess" lub "ICorDebugAppDomain" nie jest już prawidłowy i wystąpi nie dalsze wywołania zwrotne.  
  
 W programie .NET Framework w wersji 2.0 Jeśli włączone jest debugowanie niezarządzane, ta metoda zakończy się niepowodzeniem ze względu na ograniczenia systemu operacyjnego.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorDebug.idl, CorDebug.h  
  
 **Biblioteka:** CorGuids.lib  
  
 **Wersje programu .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Zobacz też  
 
