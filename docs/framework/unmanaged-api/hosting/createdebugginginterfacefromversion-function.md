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
ms.openlocfilehash: adc8ea16f0ab2bf383f8a63c49ba7d61c6bac113
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79176451"
---
# <a name="createdebugginginterfacefromversion-function"></a>CreateDebuggingInterfaceFromVersion — Funkcja
Tworzy obiekt [ICorDebug](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md) na podstawie informacji o określonej wersji.  
  
 Ta funkcja jest przestarzała w .NET Framework 4. Zamiast tego, aby uzyskać interfejs dla środowiska wykonawczego języka wspólnego (CLR) 2.0, należy użyć [metody ICLRRuntimeInfo::GetInterface](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-getinterface-method.md) i określić identyfikator klasy CLSID_CLRDebuggingLegacy i identyfikator interfejsu IID_ICorDebug. Aby uzyskać interfejs dla clr 4 lub nowszego, wywołaj [clrCreateInstance](../../../../docs/framework/unmanaged-api/hosting/clrcreateinstance-function.md) funkcji i określić identyfikator klasy CLSID_CLRDebugging i identyfikator interfejsu IID_ICLRDebugging.  
  
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
 [w] Wersja tego `ICorDebug` jest oczekiwana przez debugera. Zobacz [wyliczenie CorDebugInterfaceVersion](../../../../docs/framework/unmanaged-api/debugging/cordebuginterfaceversion-enumeration.md) dla prawidłowych wartości.  
  
 `szDebuggeeVersion`  
 [w] Wersja środowiska wykonawczego języka wspólnego skojarzone z aplikacji lub procesu do debugowania. Zobacz [GetVersionFromProcess](../../../../docs/framework/unmanaged-api/hosting/getversionfromprocess-function.md) lub [GetRequestedRuntimeVersion](../../../../docs/framework/unmanaged-api/hosting/getrequestedruntimeversion-function.md) metody informacji na temat pobierania tej wartości.  
  
 `ppCordb`  
 [na zewnątrz] Lokalizacja, która odbiera wskaźnik `ICorDebug` do obiektu.  
  
## <a name="return-value"></a>Wartość zwracana  
 Ta metoda zwraca standardowe kody błędów COM zdefiniowane w pliku WinError.h oprócz następujących wartości.  
  
|Kod powrotu|Opis|  
|-----------------|-----------------|  
|S_OK|Metoda została ukończona pomyślnie.|  
|E_invalidarg|`szDebuggeeVersion`lub `ppCordb` ma wartość null lub ciąg wersji jest niepoprawny.|  
  
## <a name="remarks"></a>Uwagi  
 Parametr `szDebuggeeVersion` jest mapowana na odpowiednią wersję pliku MSCorDbi.dll.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [Wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** MSCorEE.h  
  
 **Biblioteka:** Mscoree.dll  
  
 **Wersje programu .NET Framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Zobacz też

- [Przestarzałe funkcje hostingu środowiska CLR](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
