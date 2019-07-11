---
title: ICorDebugThread4::HadUnhandledException — Metoda
ms.date: 03/30/2017
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 9bbc3379ff9523564f4eae7da96fca2247601fcd
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/10/2019
ms.locfileid: "67765159"
---
# <a name="icordebugthread4hadunhandledexception-method"></a>ICorDebugThread4::HadUnhandledException — Metoda
Wskazuje, czy wątek nigdy nie miała nieobsługiwany wyjątek.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT GetBlockingObjects (  
    [out] ICorDebugBlockingObjectEnum **ppBlockingObjectEnum  
    );  
```  
  
## <a name="parameters"></a>Parametry  
 `ppBlockingObjectEnum`  
 [out] Wskaźnik do adresu uporządkowane wyliczenie [CorDebugBlockingObject](../../../../docs/framework/unmanaged-api/debugging/cordebugblockingobject-structure.md) struktury.  
  
## <a name="return-value"></a>Wartość zwracana  
 Ta metoda zwraca następujące specyficzne wyniki HRESULT, a także HRESULT błędów wskazujących Niepowodzenie metody.  
  
|HRESULT|Opis|  
|-------------|-----------------|  
|S_OK|Wątek miała nieobsługiwany wyjątek od jego utworzenia.|  
|S_FALSE|Wątek nigdy nie miał nieobsługiwany wyjątek.|  
  
## <a name="remarks"></a>Uwagi  
 Ta metoda wskazuje, czy wątek nigdy nie miała nieobsługiwany wyjątek. Do czasu jest wyzwalana wywołania zwrotnego nieobsługiwany wyjątek lub natywnych dołączania JIT jest inicjowane, ta metoda gwarancję zwracania S_OK. Nie ma żadnej gwarancji, [ICorDebugThread.GetCurrentException](../../../../docs/framework/unmanaged-api/debugging/icordebugthread-getcurrentexception-method.md) metoda zwróci nieobsługiwany wyjątek; jednak będzie Jeśli proces nie jeszcze jest kontynuowane po otrzymaniu wywołania zwrotnego nieobsługiwanego wyjątku lub w natywne dołączania JIT. Ponadto istnieje możliwość (chociaż to mało prawdopodobne) mieć więcej niż jeden wątek za pomocą nieobsługiwany wyjątek w czasie natywnych dołączania JIT jest wyzwalane. W takim przypadku nie ma możliwości do określenia, który wyjątek wyzwalane dołączania JIT.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorDebug.idl, CorDebug.h  
  
 **Biblioteka:** CorGuids.lib  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [ICorDebugThread4, interfejs](../../../../docs/framework/unmanaged-api/debugging/icordebugthread4-interface.md)
- [Debugowanie, interfejsy](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [Debugowanie](../../../../docs/framework/unmanaged-api/debugging/index.md)
