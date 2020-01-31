---
title: ICorDebugFrame, interfejs
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
ms.openlocfilehash: ba138e79e0d6fb6f9c5e9c3efe3466f3c88cccae
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/28/2020
ms.locfileid: "76782623"
---
# <a name="icordebugframe-interface"></a>ICorDebugFrame, interfejs

Reprezentuje ramkę na bieżącym stosie.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Opis|  
|------------|-----------------|  
|[CreateStepper, metoda](icordebugframe-createstepper-method.md)|Pobiera ICorDebugStepper do wykonania operacji wykonywania krokowego względem tego `ICorDebugFrame`.|  
|[GetCallee, metoda](icordebugframe-getcallee-method.md)|Pobiera wskaźnik do `ICorDebugFrame` w bieżącym łańcuchu, który ta ramka nazywa lub zwraca wartość null, jeśli jest to wewnętrzna ramka w łańcuchu.|  
|[GetCaller, metoda](icordebugframe-getcaller-method.md)|Pobiera wskaźnik do `ICorDebugFrame` w bieżącym łańcuchu, który wywołał tę ramkę, lub zwraca wartość null, jeśli jest to najbardziej skrajna ramka w łańcuchu.|  
|[GetChain, metoda](icordebugframe-getchain-method.md)|Pobiera wskaźnik do ICorDebugChain, do którego należy ten `ICorDebugFrame` jest częścią.|  
|[GetCode, metoda](icordebugframe-getcode-method.md)|Pobiera wskaźnik do ICorDebugCode skojarzonego z tą ramką stosu.|  
|[GetFunction, metoda](icordebugframe-getfunction-method.md)|Pobiera wskaźnik do ICorDebugFunction, który zawiera kod skojarzony z tą ramką stosu.|  
|[GetFunctionToken, metoda](icordebugframe-getfunctiontoken-method.md)|Pobiera token metadanych dla funkcji, która zawiera kod skojarzony z tą ramką stosu.|  
|[GetStackRange, metoda](icordebugframe-getstackrange-method.md)|Pobiera bezwzględny zakres adresów ramki stosu reprezentowanej przez ten `ICorDebugFrame`.|  
  
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
