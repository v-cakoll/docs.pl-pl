---
title: ICLRMetaHost::GetRuntime — Metoda
ms.date: 03/30/2017
api_name:
- ICLRMetaHost.GetRuntime
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRMetaHost::GetRuntime
helpviewer_keywords:
- GetRuntime method [.NET Framework hosting]
- ICLRMetaHost::GetRuntime method [.NET Framework hosting]
ms.assetid: a10749f1-ab91-47cf-982f-d8ccd2e81bd2
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: a9889ddf1c03f14835101f31d0a3b264f0016267
ms.sourcegitcommit: 58fc0e6564a37fa1b9b1b140a637e864c4cf696e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/08/2019
ms.locfileid: "57676554"
---
# <a name="iclrmetahostgetruntime-method"></a>ICLRMetaHost::GetRuntime — Metoda
Pobiera [ICLRRuntimeInfo](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md) interfejs, który odnosi się do określonej wersji środowiska uruchomieniowego języka wspólnego (CLR). Ta metoda zastępuje [CorBindToRuntimeEx](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md) funkcja używana z [STARTUP_LOADER_SAFEMODE](../../../../docs/framework/unmanaged-api/hosting/startup-flags-enumeration.md) flagi.  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT GetRuntime (  
    [in] LPCWSTR pwzVersion,  
    [in, REFIID riid,  
    [out,iid_is(riid), retval] LPVOID *ppRuntime  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `pwzVersion`  
 [in] Wersja kompilacji programu .NET Framework, które są przechowywane w metadanych, w formacie "v*A*. *B*[. *X*] ". *A*, *B*, i *X* są liczby dziesiętne, które odpowiadają wersji głównej, pomocniczej wersji i numer kompilacji.  
  
> [!NOTE]
>  Ten parametr musi odpowiadać nazwie katalogu dla .NET Framework w wersji, wyświetlaną w obszarze C:\Windows\Microsoft.NET\Framework lub C:\Windows\Microsoft.NET\Framework64.  
  
 Przykładowe wartości są "wartości v1.0.3705", "v1.1.4322" i "v2.0.50727" oraz "v4.0. *X*", gdzie *X* zależy od numeru kompilacji zainstalowane. Prefiks "v" jest wymagana.  
  
 `riid`  
 [in] Identyfikator dla żądanego interfejsu. Obecnie jedyną prawidłową wartością tego parametru jest IID_ICLRRuntimeInfo.  
  
 `ppRuntime`  
 [out] Wskaźnik do [ICLRRuntimeInfo](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md) interfejs, który odnosi się do żądanego środowiska uruchomieniowego.  
  
## <a name="return-value"></a>Wartość zwracana  
 Ta metoda zwraca następujące specyficzne wyniki HRESULT, a także HRESULT błędów wskazujących Niepowodzenie metody.  
  
|HRESULT|Opis|  
|-------------|-----------------|  
|S_OK|Metoda została ukończona pomyślnie.|  
|E_POINTER|`pwzVersion` lub `ppRuntime` ma wartość null.|  
  
## <a name="remarks"></a>Uwagi  
 Ta metoda użyje spójne interfejsy starszej wersji takich jak [ICorRuntimeHost](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md) funkcji interfejsu i starszej wersji, takich jak przestarzałego `CorBindTo*` funkcji (zobacz [przestarzałe CLR funkcje hostingu](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md) w programie .NET Framework 2.0, hostowanie interfejsu API). Oznacza to środowisk wykonawczych, które są ładowane przy użyciu starszej wersji interfejsu API są widoczne dla nowego interfejsu API i środowisk wykonawczych, które są ładowane przy użyciu nowego interfejsu API są widoczne dla starszej wersji interfejsu API.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** MetaHost.h  
  
 **Biblioteka:** Dołączony jako zasób w MSCorEE.dll  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także
- [ICLRMetaHost, interfejs](../../../../docs/framework/unmanaged-api/hosting/iclrmetahost-interface.md)
- [Przestarzałe klasy coclass i interfejsy hostingu środowiska CLR](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-interfaces-and-coclasses.md)
- [Interfejsy hostingu środowiska CLR](../../../../docs/framework/unmanaged-api/hosting/clr-hosting-interfaces.md)
- [Przestarzałe funkcje hostingu środowiska CLR](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
- [Hosting](../../../../docs/framework/unmanaged-api/hosting/index.md)
