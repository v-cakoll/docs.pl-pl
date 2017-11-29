---
title: "CreateDebuggingInterfaceFromVersion — Funkcja"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: CreateDebuggingInterfaceFromVersion
api_location:
- mscoree.dll
- mscoreei.dll
api_type: DLLExport
f1_keywords: CreateDebuggingInterfaceFromVersion
helpviewer_keywords: CreateDebuggingInterfaceFromVersion function [.NET Framework hosting]
ms.assetid: a746a849-463c-44f5-a2f0-9e812ed8bcc3
topic_type: apiref
caps.latest.revision: "20"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: cc352603ef1c3610edf99f7bdd877c6bb0e5d9fb
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="createdebugginginterfacefromversion-function"></a>CreateDebuggingInterfaceFromVersion — Funkcja
Tworzy [ICorDebug](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md) obiekt na podstawie określonej wersji informacji.  
  
 Ta funkcja jest przestarzała w [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)]. Aby uzyskać interfejsu na środowisko uruchomieniowe języka wspólnego (CLR) 2.0, użyj [ICLRRuntimeInfo::GetInterface](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-getinterface-method.md) — metoda i określ identyfikator klasy CLSID_CLRDebuggingLegacy oraz identyfikatora interfejsu IID_ICorDebug. Aby uzyskać interfejs 4 CLR lub później, wywołaj [CLRCreateInstance](../../../../docs/framework/unmanaged-api/hosting/clrcreateinstance-function.md) funkcji, a następnie określ identyfikator klasy CLSID_CLRDebugging i identyfikatora interfejsu IID_ICLRDebugging.  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT CreateDebuggingInterfaceFromVersion (  
    [in]  int      iDebuggerVersion,   
    [in]  LPCWSTR  szDebuggeeVersion,   
    [out] IUnknown **ppCordb  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `iDebuggerVersion`  
 [in] Wersja `ICorDebug` przez debuger zgodnie z oczekiwaniami. Zobacz [CorDebugInterfaceVersion](../../../../docs/framework/unmanaged-api/debugging/cordebuginterfaceversion-enumeration.md) wyliczenie dla prawidłowych wartości.  
  
 `szDebuggeeVersion`  
 [in] Typowe wersja środowiska uruchomieniowego CLR skojarzony z aplikacją lub procesów do debugowania. Zobacz [GetVersionFromProcess](../../../../docs/framework/unmanaged-api/hosting/getversionfromprocess-function.md) lub [GetRequestedRuntimeVersion](../../../../docs/framework/unmanaged-api/hosting/getrequestedruntimeversion-function.md) metody, aby uzyskać informacje dotyczące pobierania tej wartości.  
  
 `ppCordb`  
 [out] Lokalizacja, w której otrzymuje wskaźnik `ICorDebug` obiektu.  
  
## <a name="return-value"></a>Wartość zwracana  
 Ta metoda zwraca standardowe kody błędów COM, zgodnie z definicją w pliku pliku WinError.h oprócz następujących wartości.  
  
|Kod powrotu|Opis|  
|-----------------|-----------------|  
|S_OK|Metoda została ukończona pomyślnie.|  
|E_INVALIDARG|`szDebuggeeVersion`lub `ppCordb` ma wartość null lub wersja parametry są niepoprawne.|  
  
## <a name="remarks"></a>Uwagi  
 `szDebuggeeVersion` Parametr mapowany na odpowiednią wersję programu MSCorDbi.dll.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** MSCorEE.h  
  
 **Biblioteka:** biblioteki MSCorEE.dll  
  
 **Wersje programu .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Zobacz też  
 [Przestarzałe funkcje hostingu środowiska CLR.](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
