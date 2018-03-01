---
title: "ICorDebugThread4::HadUnhandledException — Metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- ICorDebugThread4.HadUnhandledException Method
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugThread4::HadUnhandledException
helpviewer_keywords:
- ICorDebugThread4::HadUnhandledException method [.NET Framework debugging]
- HadUnhandledException method [.NET Framework debugging]
ms.assetid: 05558daa-39e2-4c38-aeaf-e2aec4a09468
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 5a79d06f0a65facfbaa821d3dd6af547fd3d0305
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugthread4hadunhandledexception-method"></a>ICorDebugThread4::HadUnhandledException — Metoda
Wskazuje, czy wątek nigdy miał nieobsługiwany wyjątek.  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT GetBlockingObjects (  
    [out] ICorDebugBlockingObjectEnum **ppBlockingObjectEnum  
    );  
```  
  
#### <a name="parameters"></a>Parametry  
 `ppBlockingObjectEnum`  
 [out] Wskaźnik do adresu w kolejności wyliczenie [CorDebugBlockingObject](../../../../docs/framework/unmanaged-api/debugging/cordebugblockingobject-structure.md) struktury.  
  
## <a name="return-value"></a>Wartość zwracana  
 Ta metoda zwraca następujące określonych wyników HRESULT, a także HRESULT błędów wskazujących Niepowodzenie metody.  
  
|HRESULT|Opis|  
|-------------|-----------------|  
|S_OK|Wątek miał nieobsługiwany wyjątek od czasu jego utworzenia.|  
|WARTOŚCI S_FALSE|Wątek nigdy nie miał nieobsługiwany wyjątek.|  
  
## <a name="remarks"></a>Uwagi  
 Ta metoda wskazuje, czy wątek nigdy miał nieobsługiwany wyjątek. Do czasu wywołania zwrotnego nieobsługiwany wyjątek zostanie wywołany lub natywnego dołączania JIT jest inicjowane, ta metoda jest gwarantowana zwrócić wartość S_OK. Nie ma żadnych gwarancji, że [ICorDebugThread.GetCurrentException](../../../../docs/framework/unmanaged-api/debugging/icordebugthread-getcurrentexception-method.md) metoda zwróci nieobsługiwany wyjątek; jednak zostanie Jeśli proces nie jeszcze jest kontynuowane po pierwsze wywołanie zwrotne nieobsługiwany wyjątek lub na natywny dołączania JIT. Ponadto istnieje możliwość (chociaż jest mało prawdopodobne) ma więcej niż jeden wątek z nieobsługiwany wyjątek w czasie natywnego dołączania JIT zostanie wywołany. W takim przypadku nie ma nie można określić, który wyjątków wyzwalane dołączania JIT.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorDebug.idl, CorDebug.h  
  
 **Biblioteka:** CorGuids.lib  
  
 **Wersje programu .NET framework:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Zobacz też  
 [ICorDebugThread4, interfejs](../../../../docs/framework/unmanaged-api/debugging/icordebugthread4-interface.md)  
 [Debugowanie, interfejsy](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
 [Debugowanie](../../../../docs/framework/unmanaged-api/debugging/index.md)
