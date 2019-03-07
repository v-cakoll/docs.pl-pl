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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: d20c640d6a6a43b7bde4c7d46df470c7bc8c5aa2
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/06/2019
ms.locfileid: "57499527"
---
# <a name="icordebugmodule2setjmcstatus-method"></a>ICorDebugModule2::SetJMCStatus — Metoda
Ustawia stan tylko mój kod (JMC) wszystkich metod wszystkie klasy w tym icordebugmodule2 — do określonej wartości, z wyjątkiem tych `pTokens` tablicy, która ustawia przeciwną wartość.  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT SetJMCStatus (  
    [in] BOOL                        bIsJustMyCode,  
    [in] ULONG32                     cTokens,  
    [in, size_is(cTokens)] mdToken   pTokens[]  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `bIsJustMycode`  
 [in] Ustaw `true` Jeśli kod ma być debugowany; w przeciwnym razie, wartość `false`.  
  
 `cTokens`  
 [in] Rozmiar `pTokens` tablicy.  
  
 `pTokens`  
 [in] Tablica `mdToken` wartości, z których każdy odwołuje się do metody, która będzie miał stan JMC równa!`bIsJustMycode`.  
  
## <a name="remarks"></a>Uwagi  
 Stan JMC każdej metody, która została określona w `pTokens` tablicy jest równa przeciwieństwo `bIsJustMycode` wartość. Stan wszystkich innych metod, w tym module jest ustawiony na `bIsJustMycode` wartość.  
  
 `SetJMCStatus` Metoda usuwa wszystkie poprzednie ustawienia JMC, w tym module.  
  
 `SetJMCStatus` Metoda zwraca wartość HRESULT S_OK, jeśli wszystkie funkcje zostały pomyślnie ustawiono. Zwraca HRESULT CORDBG_E_FUNCTION_NOT_DEBUGGABLE, jeśli niektóre funkcje, które są oznaczone `true` nie są debugowania.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorDebug.idl, CorDebug.h  
  
 **Biblioteka:** CorGuids.lib  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]
