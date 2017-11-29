---
title: "ICorDebugStepper::StepOut — Metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugStepper.StepOut
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugStepper::StepOut
helpviewer_keywords:
- ICorDebugStepper::StepOut method [.NET Framework debugging]
- StepOut method [.NET Framework debugging]
ms.assetid: aae0f48c-4ede-4256-9251-a7fc85a229dc
topic_type: apiref
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 8b3ceca69b6b4710a3f1b8e1e9bdb4baf574119c
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="icordebugstepperstepout-method"></a>ICorDebugStepper::StepOut — Metoda
Powoduje to ICorDebugStepper — aby pojedynczy krok za pomocą jego zawierającego wątku i do wykonania podczas bieżącej ramki zwraca sterowania do wywoływania ramki.  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT StepOut ();  
```  
  
## <a name="remarks"></a>Uwagi  
 A `StepOut` operacja zostanie wykonana po powrocie zwykle z bieżącej ramki do wywoływania ramki.  
  
 Jeśli `StepOut` jest wywoływane, gdy za pomocą kodu niezarządzanego kroku ukończy po powrocie z do zarządzanego kodu, który wywołuje ona bieżącej ramki.  
  
 W programie .NET Framework w wersji 2.0, nie używaj `StepOut` z STOP_UNMANAGED Flaga ponieważ zakończy się niepowodzeniem. (Użyj [ICorDebugStepper::SetUnmappedStopMask](../../../../docs/framework/unmanaged-api/debugging/icordebugstepper-setunmappedstopmask-method.md) można ustawić flagi wykonywanie krok po kroku.) Międzyoperacyjne debugery musi Wyjdź do kodu natywnego samodzielnie.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorDebug.idl, CorDebug.h  
  
 **Biblioteka:** CorGuids.lib  
  
 **Wersje programu .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
