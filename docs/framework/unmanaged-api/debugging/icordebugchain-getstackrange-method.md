---
title: ICorDebugChain::GetStackRange — Metoda
ms.date: 03/30/2017
api_name:
- ICorDebugChain.GetStackRange
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugChain::GetStackRange
helpviewer_keywords:
- ICorDebugChain::GetStackRange method [.NET Framework debugging]
- GetStackRange method, ICorDebugChain interface [.NET Framework debugging]
ms.assetid: 554284e7-3f6c-4d40-8da5-1c9317fbd484
topic_type:
- apiref
ms.openlocfilehash: d9430c5a1f37a0507b383ea5437f7d7fed706c43
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73123860"
---
# <a name="icordebugchaingetstackrange-method"></a>ICorDebugChain::GetStackRange — Metoda
Pobiera zakres adresów segmentu stosu dla tego łańcucha.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT GetStackRange (  
    [out] CORDB_ADDRESS      *pStart,   
    [out] CORDB_ADDRESS      *pEnd  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `pStart`  
 określoną Wskaźnik do `CORDB_ADDRESS` wartości, który jest adresem początkowym segmentu stosu.  
  
 `pEnd`  
 określoną Wskaźnik do wartości `CORDB_ADDRESS`, która jest adresem końcowym segmentu stosu.  
  
## <a name="remarks"></a>Uwagi  
 Zakres liczbowy jest zrozumiały tylko dla porównania lokalizacji ramek stosu. Nie można wykonać żadnych założeń dotyczących tego, co jest rzeczywiście przechowywane na stosie.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorDebug. idl, CorDebug. h  
  
 **Biblioteka:** CorGuids. lib  
  
 **Wersje .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
