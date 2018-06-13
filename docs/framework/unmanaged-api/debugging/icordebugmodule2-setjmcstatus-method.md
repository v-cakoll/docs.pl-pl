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
ms.openlocfilehash: a56b5c31c26dbe5c5371fdb7a10c13ad11847117
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33419475"
---
# <a name="icordebugmodule2setjmcstatus-method"></a>ICorDebugModule2::SetJMCStatus — Metoda
Ustawia stan tylko mój kod (JMC) wszystkich metod wszystkie klasy w tym ICorDebugModule2 na określoną wartość, z wyjątkiem tych, `pTokens` tablicy, która ustawia przeciwną wartość.  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT SetJMCStatus (  
    [in] BOOL                        bIsJustMyCode,  
    [in] ULONG32                     cTokens,  
    [in, size_is(cTokens)] mdToken   pTokens[]  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `bIsJustMycode`  
 [in] Ustaw `true` kod ma być debugowany; w przeciwnym razie, ustawić `false`.  
  
 `cTokens`  
 [in] Rozmiar `pTokens` tablicy.  
  
 `pTokens`  
 [in] Tablica `mdToken` wartości, z których każdy odwołuje się do metody, która będzie mieć jego stan JMC!`bIsJustMycode`.  
  
## <a name="remarks"></a>Uwagi  
 Stan JMC każdej metody, która została określona w `pTokens` tablicy ma ustawioną wartość przeciwieństwem `bIsJustMycode` wartość. Stan wszystkich innych metod, w tym module jest ustawiony na `bIsJustMycode` wartość.  
  
 `SetJMCStatus` Metoda usuwa wszystkie wcześniejsze ustawienia JMC w tym module.  
  
 `SetJMCStatus` Metoda zwraca wartość S_OK HRESULT, jeśli wszystkie funkcje zostały pomyślnie ustawiono. Zwraca HRESULT CORDBG_E_FUNCTION_NOT_DEBUGGABLE, jeśli niektóre funkcje, które są oznaczone `true` nie są możliwością debugowania.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorDebug.idl, CorDebug.h  
  
 **Biblioteka:** CorGuids.lib  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]
