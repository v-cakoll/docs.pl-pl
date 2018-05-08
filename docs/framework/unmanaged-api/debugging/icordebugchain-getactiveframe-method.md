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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: a104d4d3cc74a6c1cb343818c9b0b3e8978b97df
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="icordebugchaingetactiveframe-method"></a>ICorDebugChain::GetActiveFrame — Metoda
Pobiera aktywny (to znaczy najnowszych) ramki w łańcuchu.  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT GetActiveFrame (  
    [out] ICorDebugFrame   **ppFrame  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `ppFrame`  
 [out] Wskaźnik do adresu ICorDebugFrame obiekt, który reprezentuje aktywne (oznacza to, że najnowsze) ramki w łańcuchu.  
  
## <a name="remarks"></a>Uwagi  
 Jeśli nie jest dostępne nie ramki stosu zarządzanych `ppFrame` jest ustawiony na wartość null.  
  
 Jeśli aktywną ramkę nie jest dostępny, połączenie powiedzie się i `ppFrame` będzie mieć wartość null. Aktywne ramek nie będą dostępne, łańcuchy inicjowane z powodu CHAIN_ENTER_UNMANAGED i niektóre łańcuchów inicjowane z powodu CHAIN_CLASS_INIT. Zobacz cordebugchainreason — wyliczenie.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorDebug.idl, CorDebug.h  
  
 **Biblioteka:** CorGuids.lib  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
