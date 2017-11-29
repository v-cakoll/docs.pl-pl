---
title: ICorDebugFrame Interface1
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugFrame
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugFrame
helpviewer_keywords: ICorDebugFrame interface [.NET Framework debugging]
ms.assetid: 0c48f764-3c64-4602-b2f4-4ffc60eb2c65
topic_type: apiref
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 2acc825f6592eae80f67e7614ca45f175b6756d8
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="icordebugframe-interface1"></a>ICorDebugFrame Interface1
Reprezentuje ramkę na bieżącym stosie.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Opis|  
|------------|-----------------|  
|[CreateStepper — metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugframe-createstepper-method.md)|Pobiera ICorDebugStepper — w celu wykonania operacji wykonywania krokowego względem to `ICorDebugFrame`.|  
|[GetCallee — metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugframe-getcallee-method.md)|Pobiera wskaźnik do `ICorDebugFrame` w łańcuchu bieżącego czy wywołać tej ramki, lub zwraca wartość null, jeśli to jest najbardziej ramki w łańcuchu.|  
|[GetCaller — metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugframe-getcaller-method.md)|Pobiera wskaźnik do `ICorDebugFrame` w łańcuchu bieżącego, która o nazwie tej ramki lub zwraca wartość null, jeśli to jest najbardziej zewnętrznego ramki w łańcuchu.|  
|[GetChain — metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugframe-getchain-method.md)|Pobiera wskaźnik do ICorDebugChain to `ICorDebugFrame` jest częścią.|  
|[GetCode — metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugframe-getcode-method.md)|Pobiera wskaźnik do ICorDebugCode skojarzone z tą ramką stosu.|  
|[GetFunction — metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugframe-getfunction-method.md)|Pobiera wskaźnik do ICorDebugFunction, który zawiera kod skojarzony z tą ramką stosu.|  
|[GetFunctionToken — metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugframe-getfunctiontoken-method.md)|Pobiera token metadanych dla funkcji, która zawiera kod skojarzony z tą ramką stosu.|  
|[GetStackRange — metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugframe-getstackrange-method.md)|Pobiera adres bezwzględny zakres ramki stosu reprezentowany przez ten `ICorDebugFrame`.|  
  
## <a name="remarks"></a>Uwagi  
  
> [!NOTE]
>  Ten interfejs nie obsługuje wywoływany zdalnie, między komputerami lub między procesami.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorDebug.idl, CorDebug.h  
  
 **Biblioteka:** CorGuids.lib  
  
 **Wersje programu .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Zobacz też  
 [Interfejsy debugowania](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
