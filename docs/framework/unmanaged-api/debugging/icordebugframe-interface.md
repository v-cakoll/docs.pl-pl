---
title: ICorDebugFrame — Interfejs
ms.date: 03/30/2017
api_name:
- ICorDebugFrame
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugFrame
helpviewer_keywords:
- ICorDebugFrame interface [.NET Framework debugging]
ms.assetid: 0c48f764-3c64-4602-b2f4-4ffc60eb2c65
topic_type:
- apiref
ms.openlocfilehash: 5aeea11b7e61869968aafe3425e27d6004f495ea
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73124071"
---
# <a name="icordebugframe-interface"></a>ICorDebugFrame — Interfejs

Reprezentuje ramkę na bieżącym stosie.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Opis|  
|------------|-----------------|  
|[CreateStepper, metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugframe-createstepper-method.md)|Pobiera ICorDebugStepper do wykonania operacji wykonywania krokowego względem tego `ICorDebugFrame`.|  
|[GetCallee, metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugframe-getcallee-method.md)|Pobiera wskaźnik do `ICorDebugFrame` w bieżącym łańcuchu, który ta ramka nazywa lub zwraca wartość null, jeśli jest to wewnętrzna ramka w łańcuchu.|  
|[GetCaller, metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugframe-getcaller-method.md)|Pobiera wskaźnik do `ICorDebugFrame` w bieżącym łańcuchu, który wywołał tę ramkę, lub zwraca wartość null, jeśli jest to najbardziej skrajna ramka w łańcuchu.|  
|[GetChain, metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugframe-getchain-method.md)|Pobiera wskaźnik do ICorDebugChain, do którego należy ten `ICorDebugFrame` jest częścią.|  
|[GetCode, metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugframe-getcode-method.md)|Pobiera wskaźnik do ICorDebugCode skojarzonego z tą ramką stosu.|  
|[GetFunction, metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugframe-getfunction-method.md)|Pobiera wskaźnik do ICorDebugFunction, który zawiera kod skojarzony z tą ramką stosu.|  
|[GetFunctionToken, metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugframe-getfunctiontoken-method.md)|Pobiera token metadanych dla funkcji, która zawiera kod skojarzony z tą ramką stosu.|  
|[GetStackRange, metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugframe-getstackrange-method.md)|Pobiera bezwzględny zakres adresów ramki stosu reprezentowanej przez ten `ICorDebugFrame`.|  
  
## <a name="remarks"></a>Uwagi  
  
> [!NOTE]
> Ten interfejs nie obsługuje wywoływania zdalnego na wielu maszynach ani wielu procesów.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorDebug. idl, CorDebug. h  
  
 **Biblioteka:** CorGuids. lib  
  
 **Wersje .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [Debugowanie, interfejsy](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
