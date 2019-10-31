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
ms.openlocfilehash: a0b70078dee88b270d8361aa9bddcb7d80df1db1
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73129468"
---
# <a name="icordebugmodule2setjmcstatus-method"></a>ICorDebugModule2::SetJMCStatus — Metoda
Ustawia stan Tylko mój kod (JMC) dla wszystkich metod wszystkich klas w tym ICorDebugModule2 do określonej wartości, z wyjątkiem tych w tablicy `pTokens`, które są ustawiane na wartość odwrotną.  
  
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
 podczas Ustaw, aby `true`, jeśli kod ma być debugowany; w przeciwnym razie ustaw wartość `false`.  
  
 `cTokens`  
 podczas Rozmiar tablicy `pTokens`.  
  
 `pTokens`  
 podczas Tablica wartości `mdToken`, z których każdy odwołuje się do metody, która ma ustawiony stan JMC!`bIsJustMycode`.  
  
## <a name="remarks"></a>Uwagi  
 Stan JMC każdej metody, która jest określona w tablicy `pTokens` jest ustawiony na odwrotność wartości `bIsJustMycode`. Stan wszystkich innych metod w tym module jest ustawiony na wartość `bIsJustMycode`.  
  
 Metoda `SetJMCStatus` kasuje wszystkie poprzednie ustawienia JMC w tym module.  
  
 Metoda `SetJMCStatus` zwraca wartość HRESULT S_OK, jeśli wszystkie funkcje zostały ustawione pomyślnie. Zwraca CORDBG_E_FUNCTION_NOT_DEBUGGABLE HRESULT, jeśli niektóre funkcje oznaczone `true` nie są możliwością debugowania.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorDebug. idl, CorDebug. h  
  
 **Biblioteka:** CorGuids. lib  
  
 **Wersje .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]
