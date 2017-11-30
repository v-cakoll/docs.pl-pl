---
title: "ICorDebugStepper::SetInterceptMask — Metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugStepper.SetInterceptMask
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugStepper::SetInterceptMask
helpviewer_keywords:
- SetInterceptMask method [.NET Framework debugging]
- ICorDebugStepper::SetInterceptMask method [.NET Framework debugging]
ms.assetid: 6245e2ae-5cc2-43ff-8cc1-71953d12113a
topic_type: apiref
caps.latest.revision: "13"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 2a99b504c0ce58ca6b89153667598cd4c2c682d9
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="icordebugsteppersetinterceptmask-method"></a>ICorDebugStepper::SetInterceptMask — Metoda
Ustawia wartość, która określa typy kodu, które zostaną wykorzystane do.  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT SetInterceptMask (  
    [in] CorDebugIntercept    mask  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `mask`  
 [in] Kombinacja wartości wyliczenia CorDebugIntercept, która określa typy kodu.  
  
## <a name="remarks"></a>Uwagi  
 Jeśli ustawiono bit interceptora, stepper ukończy po napotkaniu danego typu przechwytywaniu kodu. Jeśli bit jest wyczyszczone, intercepting kodu zostanie pominięte.  
  
 `SetInterceptMask` Metoda może mieć nieprzewidziane interakcji z [ICorDebugStepper::SetUnmappedStopMask](../../../../docs/framework/unmanaged-api/debugging/icordebugstepper-setunmappedstopmask-method.md) (z punktu widzenia użytkownika). Na przykład jeśli tylko widoczne (oznacza to,-wewnętrzny) część kod inicjujący klasa nie ma informacji o mapowaniu i STOP_NO_MAPPING_INFO nie została ustawiona (zobacz [ICorDebugStepper::SetUnmappedStopMask](../../../../docs/framework/unmanaged-api/debugging/icordebugstepper-setunmappedstopmask-method.md) — metoda i Cordebugunmappedstop — wyliczenie), stepper zostanie Przekrocz nad inicjowania klasy. Domyślnie tylko INTERCEPT_NONE wartość `CorDebugIntercept` wyliczenie będą używane.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorDebug.idl, CorDebug.h  
  
 **Biblioteka:** CorGuids.lib  
  
 **Wersje programu .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
