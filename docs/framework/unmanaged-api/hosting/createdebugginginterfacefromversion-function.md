---
title: CreateDebuggingInterfaceFromVersion — Funkcja
ms.date: 03/30/2017
api_name:
- CreateDebuggingInterfaceFromVersion
api_location:
- mscoree.dll
- mscoreei.dll
api_type:
- DLLExport
f1_keywords:
- CreateDebuggingInterfaceFromVersion
helpviewer_keywords:
- CreateDebuggingInterfaceFromVersion function [.NET Framework hosting]
ms.assetid: a746a849-463c-44f5-a2f0-9e812ed8bcc3
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: fe34ffded73e8305e4ade3bb9b402b1d8e1bcc49
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/10/2019
ms.locfileid: "67764676"
---
# <a name="createdebugginginterfacefromversion-function"></a>CreateDebuggingInterfaceFromVersion — Funkcja
Tworzy [ICorDebug](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md) obiektu na podstawie określonej wersji informacji.  
  
 Ta funkcja jest przestarzała w programie .NET Framework 4. Aby uzyskać interfejs na środowisko uruchomieniowe języka wspólnego (CLR) w wersji 2.0, użyj [iclrruntimeinfo::getinterface —](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-getinterface-method.md) metody i określ identyfikator klasy CLSID_CLRDebuggingLegacy oraz identyfikator interfejsu IID_ICorDebug. Aby uzyskać interfejs dla środowiska CLR 4 lub nowszy, wywołaj [CLRCreateInstance](../../../../docs/framework/unmanaged-api/hosting/clrcreateinstance-function.md) funkcji, a następnie określ identyfikator klasy CLSID_CLRDebugging i identyfikator interfejsu IID_ICLRDebugging.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT CreateDebuggingInterfaceFromVersion (  
    [in]  int      iDebuggerVersion,   
    [in]  LPCWSTR  szDebuggeeVersion,   
    [out] IUnknown **ppCordb  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `iDebuggerVersion`  
 [in] Wersja `ICorDebug` jest to oczekiwane przez debuger. Zobacz [cordebuginterfaceversion —](../../../../docs/framework/unmanaged-api/debugging/cordebuginterfaceversion-enumeration.md) wyliczenie prawidłowych wartości.  
  
 `szDebuggeeVersion`  
 [in] Typowe wersja środowiska uruchomieniowego języka skojarzone z aplikacją lub procesu do debugowania. Zobacz [getversionfromprocess —](../../../../docs/framework/unmanaged-api/hosting/getversionfromprocess-function.md) lub [getrequestedruntimeversion —](../../../../docs/framework/unmanaged-api/hosting/getrequestedruntimeversion-function.md) metody, aby uzyskać informacje dotyczące pobierania tej wartości.  
  
 `ppCordb`  
 [out] Lokalizacji, która otrzymuje wskaźnik `ICorDebug` obiektu.  
  
## <a name="return-value"></a>Wartość zwracana  
 Ta metoda zwraca standardowych kodów błędu modelu COM, zgodnie z definicją w pliku WinError.h oprócz następujących wartości.  
  
|Kod powrotu|Opis|  
|-----------------|-----------------|  
|S_OK|Metoda została ukończona pomyślnie.|  
|E_INVALIDARG|`szDebuggeeVersion` lub `ppCordb` ma wartość null lub wersji ciąg jest niepoprawny.|  
  
## <a name="remarks"></a>Uwagi  
 `szDebuggeeVersion` Parametr mapowany na odpowiednią wersję plik MSCorDbi.dll.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** MSCorEE.h  
  
 **Biblioteka:** MSCorEE.dll  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [Przestarzałe funkcje hostingu środowiska CLR](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
