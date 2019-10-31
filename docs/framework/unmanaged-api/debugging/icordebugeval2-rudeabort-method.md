---
title: ICorDebugEval2::RudeAbort — Metoda
ms.date: 03/30/2017
api_name:
- ICorDebugEval2.RudeAbort
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugEval2::RudeAbort
helpviewer_keywords:
- ICorDebugEval2::RudeAbort method [.NET Framework debugging]
- RudeAbort method, ICorDebugEval2 interface [.NET Framework debugging]
ms.assetid: 02468edf-d32b-4cb3-aaa8-3dd2abfc8b25
topic_type:
- apiref
ms.openlocfilehash: a486935d5d53a6fc7d862160ed1186c5774814c7
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73084797"
---
# <a name="icordebugeval2rudeabort-method"></a>ICorDebugEval2::RudeAbort — Metoda
Przerywa Obliczanie wykonywane przez tę `ICorDebugEval2`.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT RudeAbort ();  
```  
  
## <a name="remarks"></a>Uwagi  
 `RudeAbort` nie zwolni żadnych blokad, które są przechowywane przez ewaluatora, więc pozostawia sesję debugowania w stanie niebezpiecznym. Wywołaj tę metodę z największą ostrożnością.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorDebug. idl, CorDebug. h  
  
 **Biblioteka:** CorGuids. lib  
  
 **Wersje .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]
