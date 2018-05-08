---
title: ICorDebugFrame Interface1
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: f3d6c1a2bfd66e275b506d4465731c48cd7c6515
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="icordebugframe-interface1"></a>ICorDebugFrame Interface1
Reprezentuje ramkę na bieżącym stosie.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Opis|  
|------------|-----------------|  
|[CreateStepper, metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugframe-createstepper-method.md)|Pobiera ICorDebugStepper — w celu wykonania operacji wykonywania krokowego względem to `ICorDebugFrame`.|  
|[GetCallee, metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugframe-getcallee-method.md)|Pobiera wskaźnik do `ICorDebugFrame` w łańcuchu bieżącego czy wywołać tej ramki, lub zwraca wartość null, jeśli to jest najbardziej ramki w łańcuchu.|  
|[GetCaller, metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugframe-getcaller-method.md)|Pobiera wskaźnik do `ICorDebugFrame` w łańcuchu bieżącego, która o nazwie tej ramki lub zwraca wartość null, jeśli to jest najbardziej zewnętrznego ramki w łańcuchu.|  
|[GetChain, metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugframe-getchain-method.md)|Pobiera wskaźnik do ICorDebugChain to `ICorDebugFrame` jest częścią.|  
|[GetCode, metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugframe-getcode-method.md)|Pobiera wskaźnik do ICorDebugCode skojarzone z tą ramką stosu.|  
|[GetFunction, metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugframe-getfunction-method.md)|Pobiera wskaźnik do ICorDebugFunction, który zawiera kod skojarzony z tą ramką stosu.|  
|[GetFunctionToken, metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugframe-getfunctiontoken-method.md)|Pobiera token metadanych dla funkcji, która zawiera kod skojarzony z tą ramką stosu.|  
|[GetStackRange, metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugframe-getstackrange-method.md)|Pobiera adres bezwzględny zakres ramki stosu reprezentowany przez ten `ICorDebugFrame`.|  
  
## <a name="remarks"></a>Uwagi  
  
> [!NOTE]
>  Ten interfejs nie obsługuje wywoływany zdalnie, między komputerami lub między procesami.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorDebug.idl, CorDebug.h  
  
 **Biblioteka:** CorGuids.lib  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Zobacz też  
 [Debugowanie, interfejsy](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
