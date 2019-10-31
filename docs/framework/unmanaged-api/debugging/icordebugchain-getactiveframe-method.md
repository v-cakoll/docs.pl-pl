---
title: ICorDebugChain::GetActiveFrame — Metoda
ms.date: 03/30/2017
api_name:
- ICorDebugChain.GetActiveFrame
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugChain::GetActiveFrame
helpviewer_keywords:
- ICorDebugChain::GetActiveFrame method [.NET Framework debugging]
- GetActiveFrame method, ICorDebugChain interface [.NET Framework debugging]
ms.assetid: 36887017-670b-4f21-b406-8fab956f84a3
topic_type:
- apiref
ms.openlocfilehash: 03cb1556ee971124ed4c591f38d9f892fc7df7b0
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73192146"
---
# <a name="icordebugchaingetactiveframe-method"></a>ICorDebugChain::GetActiveFrame — Metoda
Pobiera aktywną (czyli ostatnią) ramkę w łańcuchu.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT GetActiveFrame (  
    [out] ICorDebugFrame   **ppFrame  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `ppFrame`  
 określoną Wskaźnik do adresu obiektu ICorDebugFrame, który reprezentuje aktywną (czyli ostatnią) ramkę w łańcuchu.  
  
## <a name="remarks"></a>Uwagi  
 Jeśli nie jest dostępna żadna ramka zarządzanego stosu, `ppFrame` jest ustawiona na wartość null.  
  
 Jeśli aktywna ramka jest niedostępna, wywołanie zakończy się pomyślnie, a `ppFrame` będzie miało wartość null. Aktywne ramki nie będą dostępne dla łańcuchów zainicjowanych z powodu CHAIN_ENTER_UNMANAGED oraz dla niektórych łańcuchów inicjowanych z powodu CHAIN_CLASS_INIT. Zobacz Wyliczenie CorDebugChainReason —.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorDebug. idl, CorDebug. h  
  
 **Biblioteka:** CorGuids. lib  
  
 **Wersje .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
