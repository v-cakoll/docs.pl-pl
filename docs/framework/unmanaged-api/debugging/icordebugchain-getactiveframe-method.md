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
ms.openlocfilehash: 2f67188539d5ad5523c255fbc663e990e1b8245f
ms.sourcegitcommit: 957c49696eaf048c284ef8f9f8ffeb562357ad95
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/07/2020
ms.locfileid: "82894683"
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
 Jeśli żadna ramka zarządzanego stosu nie jest dostępna `ppFrame` , jest ustawiona na wartość null.  
  
 Jeśli aktywna ramka jest niedostępna, wywołanie powiedzie się i `ppFrame` będzie miało wartość null. Aktywne ramki nie będą dostępne dla łańcuchów inicjowanych z powodu CHAIN_ENTER_UNMANAGED, a w przypadku niektórych łańcuchów inicjowanych z powodu CHAIN_CLASS_INIT. Zobacz Wyliczenie CorDebugChainReason —.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).  
  
 **Nagłówek:** CorDebug. idl, CorDebug. h  
  
 **Biblioteka:** CorGuids. lib  
  
 **.NET Framework wersje:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
