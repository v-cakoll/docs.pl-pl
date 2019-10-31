---
title: ICLRRuntimeInfo — Interfejs
ms.date: 03/30/2017
api_name:
- ICLRRuntimeInfo
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRRuntimeInfo
helpviewer_keywords:
- ICLRRuntimeInfo interface [.NET Framework hosting]
ms.assetid: 287e5ede-b3a7-4ef8-a756-4fca3f285a82
topic_type:
- apiref
ms.openlocfilehash: f6608b03df80fa37ebf5049b53bce46da3e155e0
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73120363"
---
# <a name="iclrruntimeinfo-interface"></a>ICLRRuntimeInfo — Interfejs
Dostarcza metody, które zwracają informacje o konkretnym środowisku uruchomieniowym języka wspólnego (CLR), w tym o wersji, katalogu i stanie ładowania. Ten interfejs zapewnia również funkcje specyficzne dla środowiska uruchomieniowego bez inicjalizacji środowiska uruchomieniowego. Obejmuje metodę [LoadLibrary](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-loadlibrary-method.md) względną dla środowiska uruchomieniowego, metodę [GetProcAddress](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-getprocaddress-method.md) specyficzną dla modułu środowiska uruchomieniowego i interfejsy dostarczone przez środowisko uruchomieniowe za pomocą metody [GetInterface](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-getinterface-method.md) .  
  
## <a name="methods"></a>Metody  
  
|Metoda|Opis|  
|------------|-----------------|  
|[BindAsLegacyV2Runtime, metoda](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-bindaslegacyv2runtime-method.md)|Tworzy powiązanie tego środowiska uruchomieniowego ze wszystkimi starszymi decyzjami zasad aktywacji środowiska CLR w wersji 2.|  
|[GetDefaultStartupFlags, metoda](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-getdefaultstartupflags-method.md)|Pobiera flagi uruchamiania środowiska CLR i plik konfiguracji hosta.|  
|[GetInterface, metoda](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-getinterface-method.md)|Ładuje środowisko CLR do bieżącego procesu i zwraca wskaźniki interfejsu środowiska uruchomieniowego, takie jak [ICLRRuntimeHost](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-interface.md), [ICLRStrongName](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md) i [IMetaDataDispenser](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenser-interface.md). Ta metoda zastępuje wszystkie funkcje `CorBindTo*`.|  
|[GetProcAddress, metoda](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-getprocaddress-method.md)|Pobiera adres określonej funkcji, która została wyeksportowana z CLR skojarzonej z tym interfejsem. Ta metoda zastępuje metodę [GetRealProcAddress —](../../../../docs/framework/unmanaged-api/hosting/getrealprocaddress-function.md) .|  
|[GetRuntimeDirectory, metoda](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-getruntimedirectory-method.md)|Pobiera katalog instalacji środowiska CLR skojarzonego z tym interfejsem. Ta metoda zastępuje metodę [GetCORSystemDirectory —](../../../../docs/framework/unmanaged-api/hosting/getcorsystemdirectory-function.md) .|  
|[GetVersionString, metoda](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-getversionstring-method.md)|Pobiera informacje o wersji środowiska uruchomieniowego języka wspólnego (CLR) skojarzone z danym interfejsem [ICLRRuntimeInfo](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md) . Ta metoda zastępuje metody [GetRequestedRuntimeInfo —](../../../../docs/framework/unmanaged-api/hosting/getrequestedruntimeinfo-function.md) i [GetRequestedRuntimeVersion —](../../../../docs/framework/unmanaged-api/hosting/getrequestedruntimeversion-function.md) .|  
|[IsLoadable, metoda](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-isloadable-method.md)|Wskazuje, czy środowisko uruchomieniowe skojarzone z tym interfejsem może zostać załadowane do bieżącego procesu, biorąc pod uwagę inne środowiska uruchomieniowe, które mogły już zostać załadowane do procesu.|  
|[IsLoaded, metoda](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-isloaded-method.md)|Wskazuje, czy środowisko CLR skojarzone z interfejsem [ICLRRuntimeInfo](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md) jest załadowane do procesu.|  
|[IsStarted, metoda](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-isstarted-method.md)|Wskazuje, czy środowisko CLR skojarzone z interfejsem [ICLRRuntimeInfo](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md) zostało uruchomione.|  
|[LoadErrorString, metoda](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-loaderrorstring-method.md)|Tłumaczy wartość HRESULT na odpowiedni komunikat o błędzie dla określonej kultury. Ta metoda zastępuje metody [LoadStringRC —](../../../../docs/framework/unmanaged-api/hosting/loadstringrc-function.md) i [LoadStringRCEx —](../../../../docs/framework/unmanaged-api/hosting/loadstringrcex-function.md) .|  
|[LoadLibrary, metoda](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-loadlibrary-method.md)|Ładuje bibliotekę z katalogu struktury środowiska CLR reprezentowanej przez interfejs [ICLRRuntimeInfo](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md) . Ta metoda zastępuje metodę [LoadLibraryShim —](../../../../docs/framework/unmanaged-api/hosting/loadlibraryshim-function.md) .|  
|[SetDefaultStartupFlags, metoda](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-setdefaultstartupflags-method.md)|Ustawia flagi uruchamiania środowiska CLR i plik konfiguracji hosta.|  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** Obiekt ServiceHost. h  
  
 **Biblioteka:** Uwzględnione jako zasób w bibliotece MSCorEE. dll  
  
 **Wersje .NET Framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [Hosting, interfejsy](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
- [Hosting](../../../../docs/framework/unmanaged-api/hosting/index.md)
