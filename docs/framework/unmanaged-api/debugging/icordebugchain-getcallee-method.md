---
title: ICorDebugChain::GetCallee — Metoda
ms.date: 03/30/2017
api_name:
- ICorDebugChain.GetCallee
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugChain::GetCallee method
helpviewer_keywords:
- ICorDebugChain::GetCallee method [.NET Framework debugging]
- GetCallee method, ICorDebugChain interface [.NET Framework debugging]
ms.assetid: 19560c79-abdc-4bdf-a5fe-eb362a59edc0
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 79743b78ea3d19bab4756b580d2feddd07e0a23b
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/10/2019
ms.locfileid: "67744984"
---
# <a name="icordebugchaingetcallee-method"></a>ICorDebugChain::GetCallee — Metoda
Pobiera łańcucha, który został wywołany przez tego łańcucha.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT GetCallee (  
    [out] ICorDebugChain     **ppChain  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `ppChain`  
 [out] Wskaźnik na adres icordebugchain — obiekt, który reprezentuje o nazwie łańcucha. Jeśli ta sieć jest w trakcie wykonywania (to znaczy, jeśli ten łańcuch nie oczekuje na o nazwie łańcuch do zwrócenia), `ppChain` będzie miał wartość null.  
  
## <a name="remarks"></a>Uwagi  
 Ten łańcuch będzie czekać na o nazwie łańcuch do zwrócenia przed jego wznawia działanie. Łańcuch o nazwie może znajdować się na inny wątek w przypadku międzyprocesowe między wątkami.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorDebug.idl, CorDebug.h  
  
 **Biblioteka:** CorGuids.lib  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
