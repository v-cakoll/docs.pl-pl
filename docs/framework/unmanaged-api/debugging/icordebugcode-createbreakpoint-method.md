---
title: ICorDebugCode::CreateBreakpoint — Metoda
ms.date: 03/30/2017
api_name:
- ICorDebugCode.CreateBreakpoint
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugCode::CreateBreakpoint
helpviewer_keywords:
- ICorDebugCode::CreateBreakpoint method [.NET Framework debugging]
- CreateBreakpoint method, ICorDebugCode interface [.NET Framework debugging]
ms.assetid: 46842618-0fe4-480b-871c-82fba82d23d9
topic_type:
- apiref
ms.openlocfilehash: 40582b1289875d5151ea96e3153c6e4760737e84
ms.sourcegitcommit: 957c49696eaf048c284ef8f9f8ffeb562357ad95
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/07/2020
ms.locfileid: "82893808"
---
# <a name="icordebugcodecreatebreakpoint-method"></a>ICorDebugCode::CreateBreakpoint — Metoda
Tworzy punkt przerwania w tym segmencie kodu w określonym przesunięciu.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT CreateBreakpoint (  
    [in] ULONG32     offset,  
    [out] ICorDebugFunctionBreakpoint **ppBreakpoint  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `offset`  
 podczas Przesunięcie, od którego ma zostać utworzony punkt przerwania.  
  
 `ppBreakpoint`  
 określoną Wskaźnik do adresu obiektu "ICorDebugFunctionBreakpoint", który reprezentuje punkt przerwania.  
  
## <a name="remarks"></a>Uwagi  
 Przed aktywnym punktem przerwania należy dodać go do obiektu procesu.  
  
 Jeśli ten kod jest kodem języka pośredniego (MSIL) firmy Microsoft, a istnieje skompilowana, natywna wersja kodu, punkt przerwania zostanie zastosowany w kodzie skompilowanym JIT. (To samo jest prawdziwe, jeśli kod jest kompilowany w trybie JIT później).  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).  
  
 **Nagłówek:** CorDebug. idl, CorDebug. h  
  
 **Biblioteka:** CorGuids. lib  
  
 **.NET Framework wersje:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
