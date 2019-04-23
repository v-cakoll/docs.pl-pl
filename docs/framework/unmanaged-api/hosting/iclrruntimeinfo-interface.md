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
ms.openlocfilehash: 213fa9fda6b154d4548b4163cc7b5890bfcfb49c
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59186995"
---
# <a name="iclrruntimeinfo-interface"></a>ICLRRuntimeInfo — Interfejs
Udostępnia metody, które zwracają informacji na temat określonych środowisko uruchomieniowe języka wspólnego (CLR), m.in. Wersja katalogu i stan obciążenia. Ten interfejs zapewnia również funkcje specyficzne dla środowiska uruchomieniowego bez inicjowania środowiska uruchomieniowego. Zawiera ona względna środowiska uruchomieniowego [LoadLibrary](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-loadlibrary-method.md) metody, środowisko uruchomieniowe specyficzne dla modułu [GetProcAddress](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-getprocaddress-method.md) metody i interfejsy dostarczane przez środowisko uruchomieniowe za pośrednictwem [getinterface —](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-getinterface-method.md)metody.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Opis|  
|------------|-----------------|  
|[BindAsLegacyV2Runtime, metoda](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-bindaslegacyv2runtime-method.md)|Wiąże się to środowisko uruchomieniowe dla wszystkich starszej wersji środowiska CLR w wersji 2 aktywacji decyzji dotyczących zasad.|  
|[GetDefaultStartupFlags, metoda](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-getdefaultstartupflags-method.md)|Pobiera flagi uruchamiania środowiska CLR i pliku konfiguracyjnego hosta.|  
|[GetInterface, metoda](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-getinterface-method.md)|Ładuje środowisko CLR do bieżący proces i zwraca środowiska uruchomieniowego, wskaźniki interfejsu, takich jak [ICLRRuntimeHost](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-interface.md), [iclrstrongname —](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md) i [imetadatadispenser —](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenser-interface.md). Ta metoda zastępuje wszystkie `CorBindTo*` funkcji.|  
|[GetProcAddress, metoda](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-getprocaddress-method.md)|Pobiera adres określonej funkcji, który został wyeksportowany ze środowiska CLR skojarzony z tym interfejsem. Ta metoda zastępuje [getrealprocaddress —](../../../../docs/framework/unmanaged-api/hosting/getrealprocaddress-function.md) metody.|  
|[GetRuntimeDirectory, metoda](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-getruntimedirectory-method.md)|Pobiera katalog instalacyjny środowiska CLR skojarzony z tym interfejsem. Ta metoda zastępuje [GetCORSystemDirectory](../../../../docs/framework/unmanaged-api/hosting/getcorsystemdirectory-function.md) metody.|  
|[GetVersionString, metoda](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-getversionstring-method.md)|Pobiera (CLR) wersja informacje CLR skojarzony z danym [ICLRRuntimeInfo](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md) interfejsu. Ta metoda zastępuje [getrequestedruntimeinfo —](../../../../docs/framework/unmanaged-api/hosting/getrequestedruntimeinfo-function.md) i [getrequestedruntimeversion —](../../../../docs/framework/unmanaged-api/hosting/getrequestedruntimeversion-function.md) metody.|  
|[IsLoadable, metoda](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-isloadable-method.md)|Wskazuje, czy środowisko uruchomieniowe skojarzona z tym interfejsem, może być załadowany do bieżącego procesu, biorąc pod uwagę innych środowisk wykonawczych, które mogą już być załadowany do procesu.|  
|[IsLoaded, metoda](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-isloaded-method.md)|Wskazuje, czy środowisko CLR skojarzony z [ICLRRuntimeInfo](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md) interfejsu jest załadowany do procesu.|  
|[IsStarted, metoda](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-isstarted-method.md)|Wskazuje, czy CLR, która jest skojarzona z [ICLRRuntimeInfo](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md) interfejs został uruchomiony.|  
|[LoadErrorString, metoda](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-loaderrorstring-method.md)|Tłumaczy wartość HRESULT do odpowiedniego komunikatu o błędzie dla określonej kultury. Ta metoda zastępuje [loadstringrc —](../../../../docs/framework/unmanaged-api/hosting/loadstringrc-function.md) i [loadstringrcex —](../../../../docs/framework/unmanaged-api/hosting/loadstringrcex-function.md) metody.|  
|[LoadLibrary, metoda](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-loadlibrary-method.md)|Ładuje bibliotekę z katalogu framework, CLR reprezentowany przez [ICLRRuntimeInfo](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md) interfejsu. Ta metoda zastępuje [LoadLibraryShim](../../../../docs/framework/unmanaged-api/hosting/loadlibraryshim-function.md) metody.|  
|[SetDefaultStartupFlags, metoda](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-setdefaultstartupflags-method.md)|Ustawia flagi uruchamiania środowiska CLR i hosta pliku konfiguracji.|  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** MetaHost.h  
  
 **Biblioteka:** Dołączony jako zasób w MSCorEE.dll  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [Hosting, interfejsy](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
- [Hosting](../../../../docs/framework/unmanaged-api/hosting/index.md)
