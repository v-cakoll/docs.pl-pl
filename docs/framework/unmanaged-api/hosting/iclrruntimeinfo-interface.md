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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: cc8225b6612c7bf07d220b20d515f64a346b9691
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33436471"
---
# <a name="iclrruntimeinfo-interface"></a>ICLRRuntimeInfo — Interfejs
Udostępnia metody, które zwracają informacje o określonych środowisko uruchomieniowe języka wspólnego (CLR), w tym wersja, katalogu i stanie obciążenia. Ten interfejs udostępnia funkcje środowiska uruchomieniowego bez podczas inicjowania środowiska uruchomieniowego. Obejmuje ona względna środowiska uruchomieniowego [LoadLibrary](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-loadlibrary-method.md) metoda, środowiska wykonawczego specyficzne dla modułu [GetProcAddress](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-getprocaddress-method.md) — metoda i wprowadzone do środowiska wykonawczego interfejsy za pośrednictwem [GetInterface](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-getinterface-method.md)metody.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Opis|  
|------------|-----------------|  
|[BindAsLegacyV2Runtime, metoda](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-bindaslegacyv2runtime-method.md)|Wiąże się to środowisko uruchomieniowe dla wszystkich starszej wersji środowiska CLR w wersji 2 aktywacji decyzji dotyczących zasad.|  
|[GetDefaultStartupFlags, metoda](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-getdefaultstartupflags-method.md)|Pobiera flagi uruchamiania CLR i pliku konfiguracji hosta.|  
|[GetInterface, metoda](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-getinterface-method.md)|Ładuje środowiska CLR do bieżącego procesu i zwraca środowiska uruchomieniowego wskaźniki interfejsu, takich jak [ICLRRuntimeHost](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-interface.md), [ICLRStrongName](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md) i [IMetaDataDispenser](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenser-interface.md). Ta metoda zastępuje wszystkie `CorBindTo*` funkcji.|  
|[GetProcAddress, metoda](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-getprocaddress-method.md)|Pobiera adresu określonej funkcji, który został wyeksportowany z CLR skojarzony z tym interfejsem. Ta metoda zastępuje [GetRealProcAddress](../../../../docs/framework/unmanaged-api/hosting/getrealprocaddress-function.md) metody.|  
|[GetRuntimeDirectory, metoda](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-getruntimedirectory-method.md)|Pobiera katalog instalacyjny środowiska CLR skojarzony z tym interfejsem. Ta metoda zastępuje [GetCORSystemDirectory](../../../../docs/framework/unmanaged-api/hosting/getcorsystemdirectory-function.md) metody.|  
|[GetVersionString, metoda](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-getversionstring-method.md)|Pobiera wspólnego języka środowiska uruchomieniowego (języka wspólnego CLR) informacje o wersji skojarzone z danym [ICLRRuntimeInfo](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md) interfejsu. Ta metoda zastępuje [GetRequestedRuntimeInfo](../../../../docs/framework/unmanaged-api/hosting/getrequestedruntimeinfo-function.md) i [GetRequestedRuntimeVersion](../../../../docs/framework/unmanaged-api/hosting/getrequestedruntimeversion-function.md) metody.|  
|[IsLoadable, metoda](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-isloadable-method.md)|Wskazuje, czy środowisko uruchomieniowe skojarzone z tym interfejsem, mogą zostać załadowane do bieżącego procesu, biorąc pod uwagę innych środowisk uruchomieniowych, który może być już załadowany do procesu.|  
|[IsLoaded, metoda](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-isloaded-method.md)|Wskazuje, czy CLR skojarzony z [ICLRRuntimeInfo](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md) interfejsu jest załadowany do procesu.|  
|[IsStarted, metoda](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-isstarted-method.md)|Wskazuje, czy CLR, która jest skojarzona z [ICLRRuntimeInfo](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md) interfejsu została uruchomiona.|  
|[LoadErrorString, metoda](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-loaderrorstring-method.md)|Tłumaczy wartość HRESULT na odpowiedni komunikat o błędzie dla określonej kultury. Ta metoda zastępuje [LoadStringRC](../../../../docs/framework/unmanaged-api/hosting/loadstringrc-function.md) i [LoadStringRCEx](../../../../docs/framework/unmanaged-api/hosting/loadstringrcex-function.md) metody.|  
|[LoadLibrary, metoda](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-loadlibrary-method.md)|Ładuje bibliotekę z katalogu framework CLR reprezentowany przez [ICLRRuntimeInfo](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md) interfejsu. Ta metoda zastępuje [LoadLibraryShim](../../../../docs/framework/unmanaged-api/hosting/loadlibraryshim-function.md) metody.|  
|[SetDefaultStartupFlags, metoda](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-setdefaultstartupflags-method.md)|Ustawia flagi uruchamiania CLR i hosta pliku konfiguracji.|  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** MetaHost.h  
  
 **Biblioteka:** uwzględnione jako zasób w MSCorEE.dll  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Zobacz też  
 [Hosting, interfejsy](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)  
 [Hosting](../../../../docs/framework/unmanaged-api/hosting/index.md)
