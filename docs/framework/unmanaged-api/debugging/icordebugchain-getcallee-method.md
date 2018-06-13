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
ms.openlocfilehash: f050a3d9d37e43713c40896fb162bcf9932c6512
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33403373"
---
# <a name="icordebugchaingetcallee-method"></a>ICorDebugChain::GetCallee — Metoda
Pobiera łańcucha, która została wywołana przez ten łańcuch.  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT GetCallee (  
    [out] ICorDebugChain     **ppChain  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `ppChain`  
 [out] Wskaźnik do adresu ICorDebugChain obiektu, który odpowiada nazwie łańcucha. Jeśli ten łańcuch jest aktualnie wykonywany (oznacza to, czy ten łańcuch nie oczekuje na nazwie łańcucha do zwrócenia), `ppChain` będzie mieć wartość null.  
  
## <a name="remarks"></a>Uwagi  
 Ten łańcuch będzie oczekiwał na nazwie łańcucha do zwrócenia przed kontynuuje wykonywanie. Łańcuch o nazwie może być inny wątek w przypadku międzyprocesowe między wątkami.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorDebug.idl, CorDebug.h  
  
 **Biblioteka:** CorGuids.lib  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
