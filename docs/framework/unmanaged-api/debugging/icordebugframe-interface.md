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
ms.openlocfilehash: 9c2771d1338943406921447d96dd9a8748153a36
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/12/2020
ms.locfileid: "83209633"
---
# <a name="icordebugframe-interface"></a>ICorDebugFrame, interfejs

Reprezentuje ramkę na bieżącym stosie.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Opis|  
|------------|-----------------|  
|[CreateStepper — Metoda](icordebugframe-createstepper-method.md)|Pobiera ICorDebugStepper do wykonania operacji krokowe względem tego `ICorDebugFrame` .|  
|[GetCallee, metoda](icordebugframe-getcallee-method.md)|Pobiera wskaźnik do elementu `ICorDebugFrame` w bieżącym łańcuchu, który ta ramka nazywa lub zwraca wartość null, jeśli jest to wewnętrzna ramka w łańcuchu.|  
|[GetCaller, metoda](icordebugframe-getcaller-method.md)|Pobiera wskaźnik do elementu `ICorDebugFrame` w bieżącym łańcuchu, który wywołał tę ramkę, lub zwraca wartość null, jeśli jest to najbardziej skrajna ramka w łańcuchu.|  
|[GetChain, metoda](icordebugframe-getchain-method.md)|Pobiera wskaźnik do ICorDebugChain, który `ICorDebugFrame` jest częścią.|  
|[GetCode, metoda](icordebugframe-getcode-method.md)|Pobiera wskaźnik do ICorDebugCode skojarzonego z tą ramką stosu.|  
|[GetFunction, metoda](icordebugframe-getfunction-method.md)|Pobiera wskaźnik do ICorDebugFunction, który zawiera kod skojarzony z tą ramką stosu.|  
|[GetFunctionToken, metoda](icordebugframe-getfunctiontoken-method.md)|Pobiera token metadanych dla funkcji, która zawiera kod skojarzony z tą ramką stosu.|  
|[GetStackRange — Metoda](icordebugframe-getstackrange-method.md)|Pobiera bezwzględny zakres adresów ramki stosu reprezentowanej przez ten element `ICorDebugFrame` .|  
  
## <a name="remarks"></a>Uwagi  
  
> [!NOTE]
> Ten interfejs nie obsługuje wywoływania zdalnego na wielu maszynach ani wielu procesów.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).  
  
 **Nagłówek:** CorDebug. idl, CorDebug. h  
  
 **Biblioteka:** CorGuids. lib  
  
 **.NET Framework wersje:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Zobacz też

- [Debugowanie — Interfejsy](debugging-interfaces.md)
