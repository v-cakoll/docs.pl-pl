---
title: ICorDebugModule2::SetJMCStatus — Metoda
ms.date: 03/30/2017
api_name:
- ICorDebugModule2.SetJMCStatus
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugModule2::SetJMCStatus
helpviewer_keywords:
- SetJMCStatus method, ICorDebugModule2 interface [.NET Framework debugging]
- ICorDebugModule2::SetJMCStatus method [.NET Framework debugging]
ms.assetid: 8c6d2089-4dbb-4715-b9e9-2a4491c8c9ce
topic_type:
- apiref
ms.openlocfilehash: d5109043a8601d7997f52e88ea472644f1b9ca03
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/12/2020
ms.locfileid: "83208788"
---
# <a name="icordebugmodule2setjmcstatus-method"></a>ICorDebugModule2::SetJMCStatus — Metoda
Ustawia stan Tylko mój kod (JMC) dla wszystkich metod wszystkich klas w tym ICorDebugModule2 do określonej wartości, z wyjątkiem tych w `pTokens` tablicy, które są ustawiane na wartość odwrotną.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT SetJMCStatus (  
    [in] BOOL                        bIsJustMyCode,  
    [in] ULONG32                     cTokens,  
    [in, size_is(cTokens)] mdToken   pTokens[]  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `bIsJustMycode`  
 podczas Ustaw na `true` , jeśli kod ma być debugowany; w przeciwnym razie ustaw wartość `false` .  
  
 `cTokens`  
 podczas Rozmiar `pTokens` tablicy.  
  
 `pTokens`  
 podczas Tablica `mdToken` wartości, z których każdy odwołuje się do metody, która ma ustawiony stan JMC! `bIsJustMycode` .  
  
## <a name="remarks"></a>Uwagi  
 Stan JMC każdej metody określonej w `pTokens` tablicy jest ustawiony na odwrotność `bIsJustMycode` wartości. Stan wszystkich innych metod w tym module jest ustawiony na `bIsJustMycode` wartość.  
  
 `SetJMCStatus`Metoda powoduje wymazanie wszystkich poprzednich ustawień JMC w tym module.  
  
 `SetJMCStatus`Metoda zwraca S_OK HRESULT, jeśli wszystkie funkcje zostały ustawione pomyślnie. Zwraca CORDBG_E_FUNCTION_NOT_DEBUGGABLE HRESULT, jeśli niektóre funkcje, które są oznaczone, `true` nie są możliwością debugowania.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).  
  
 **Nagłówek:** CorDebug. idl, CorDebug. h  
  
 **Biblioteka:** CorGuids. lib  
  
 **.NET Framework wersje:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]
