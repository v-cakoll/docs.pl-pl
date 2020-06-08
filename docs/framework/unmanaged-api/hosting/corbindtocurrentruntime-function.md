---
title: CorBindToCurrentRuntime — Funkcja
ms.date: 03/30/2017
api_name:
- CorBindToCurrentRuntime
api_location:
- mscoree.dll
- mscoreei.dll
api_type:
- HeaderDef
f1_keywords:
- CorBindToCurrentRuntime
helpviewer_keywords:
- CorBindToCurrentRuntime function [.NET Framework hosting]
ms.assetid: 6105c13e-d9cd-44d2-a95a-924e042830c7
topic_type:
- apiref
ms.openlocfilehash: 4c015d77deb4e6ed3d43074f2903e26b687de84f
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/08/2020
ms.locfileid: "84493568"
---
# <a name="corbindtocurrentruntime-function"></a>CorBindToCurrentRuntime — Funkcja
Ładuje środowisko uruchomieniowe języka wspólnego (CLR) do procesu przy użyciu informacji o wersji przechowywanych w pliku XML. Format pliku XML jest modelowany po standardowym pliku konfiguracji aplikacji. Aby uzyskać więcej informacji na temat plików konfiguracji, zobacz [Schemat pliku konfiguracji](../../configure-apps/file-schema/index.md).  
  
 Ta funkcja jest przestarzała w .NET Framework 4. Zobacz [ładowanie środowiska uruchomieniowego języka wspólnego do procesu](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/01918c6x(v=vs.100)).  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT CorBindToCurrentRuntime (  
    [in]  LPCWSTR   pwszFileName,  
    [in]  REFCLSID  rclsid,  
    [in]  REFIID    riid,  
    [out] LPVOID    *ppv  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `pwszFileName`  
 podczas Nazwa pliku konfiguracji aplikacji, który określa wersję środowiska CLR do załadowania. Jeśli nazwa pliku nie jest w pełni kwalifikowana, zakłada się, że znajduje się w tym samym katalogu co plik wykonywalny wywołujący wywołanie.  
  
 Wersja środowiska uruchomieniowego do załadowania jest opisana przez atrybut Version w [\<requiredRuntime>](../../configure-apps/file-schema/startup/requiredruntime-element.md) elemencie pliku konfiguracji.  
  
 Jeśli nie określono żadnej wersji lub `<requiredRuntime>` nie można znaleźć elementu, zostanie załadowana Najnowsza wersja środowiska CLR, która jest zainstalowana na maszynie.  
  
 `rclsid`  
 podczas `CLSID`Klasy coclass implementującej interfejs [ICorRuntimeHost](icorruntimehost-interface.md) lub [ICLRRuntimeHost](iclrruntimehost-interface.md) . Obsługiwane wartości to CLSID_CorRuntimeHost lub CLSID_CLRRuntimeHost.  
  
 `riid`  
 podczas Żądanego `IID` interfejsu. Obsługiwane wartości to IID_ICorRuntimeHost lub IID_ICLRRuntimeHost.  
  
 `ppv`  
 określoną Zwrócony wskaźnik interfejsu.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).  
  
 **Nagłówek:** MSCorEE. h  
  
 **Biblioteka:** MSCorEE. dll  
  
 **.NET Framework wersje:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [CorBindToRuntime, funkcja](corbindtoruntime-function.md)
- [CorBindToRuntimeByCfg — Funkcja](corbindtoruntimebycfg-function.md)
- [CorBindToRuntimeEx, funkcja](corbindtoruntimeex-function.md)
- [CorBindToRuntimeHost — Funkcja](corbindtoruntimehost-function.md)
- [ICorRuntimeHost, interfejs](icorruntimehost-interface.md)
- [Przestarzałe funkcje hostingu środowiska CLR](deprecated-clr-hosting-functions.md)
