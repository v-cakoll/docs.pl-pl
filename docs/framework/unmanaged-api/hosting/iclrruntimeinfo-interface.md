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
ms.openlocfilehash: 71e2c7f6790f29872c051bb5cea50755068057e9
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/08/2020
ms.locfileid: "84504046"
---
# <a name="iclrruntimeinfo-interface"></a>ICLRRuntimeInfo — Interfejs
Dostarcza metody, które zwracają informacje o konkretnym środowisku uruchomieniowym języka wspólnego (CLR), w tym o wersji, katalogu i stanie ładowania. Ten interfejs zapewnia również funkcje specyficzne dla środowiska uruchomieniowego bez inicjalizacji środowiska uruchomieniowego. Obejmuje metodę [LoadLibrary](iclrruntimeinfo-loadlibrary-method.md) względną dla środowiska uruchomieniowego, metodę [GetProcAddress](iclrruntimeinfo-getprocaddress-method.md) specyficzną dla modułu środowiska uruchomieniowego i interfejsy dostarczone przez środowisko uruchomieniowe za pomocą metody [GetInterface](iclrruntimeinfo-getinterface-method.md) .  
  
## <a name="methods"></a>Metody  
  
|Metoda|Opis|  
|------------|-----------------|  
|[BindAsLegacyV2Runtime, metoda](iclrruntimeinfo-bindaslegacyv2runtime-method.md)|Tworzy powiązanie tego środowiska uruchomieniowego ze wszystkimi starszymi decyzjami zasad aktywacji środowiska CLR w wersji 2.|  
|[GetDefaultStartupFlags, metoda](iclrruntimeinfo-getdefaultstartupflags-method.md)|Pobiera flagi uruchamiania środowiska CLR i plik konfiguracji hosta.|  
|[GetInterface, metoda](iclrruntimeinfo-getinterface-method.md)|Ładuje środowisko CLR do bieżącego procesu i zwraca wskaźniki interfejsu środowiska uruchomieniowego, takie jak [ICLRRuntimeHost](iclrruntimehost-interface.md), [ICLRStrongName](iclrstrongname-interface.md) i [IMetaDataDispenser](../metadata/imetadatadispenser-interface.md). Ta metoda zastępuje wszystkie `CorBindTo*` funkcje.|  
|[GetProcAddress, metoda](iclrruntimeinfo-getprocaddress-method.md)|Pobiera adres określonej funkcji, która została wyeksportowana z CLR skojarzonej z tym interfejsem. Ta metoda zastępuje metodę [GetRealProcAddress —](getrealprocaddress-function.md) .|  
|[GetRuntimeDirectory, metoda](iclrruntimeinfo-getruntimedirectory-method.md)|Pobiera katalog instalacji środowiska CLR skojarzonego z tym interfejsem. Ta metoda zastępuje metodę [GetCORSystemDirectory —](getcorsystemdirectory-function.md) .|  
|[GetVersionString — Metoda](iclrruntimeinfo-getversionstring-method.md)|Pobiera informacje o wersji środowiska uruchomieniowego języka wspólnego (CLR) skojarzone z danym interfejsem [ICLRRuntimeInfo](iclrruntimeinfo-interface.md) . Ta metoda zastępuje metody [GetRequestedRuntimeInfo —](getrequestedruntimeinfo-function.md) i [GetRequestedRuntimeVersion —](getrequestedruntimeversion-function.md) .|  
|[IsLoadable, metoda](iclrruntimeinfo-isloadable-method.md)|Wskazuje, czy środowisko uruchomieniowe skojarzone z tym interfejsem może zostać załadowane do bieżącego procesu, biorąc pod uwagę inne środowiska uruchomieniowe, które mogły już zostać załadowane do procesu.|  
|[IsLoaded, metoda](iclrruntimeinfo-isloaded-method.md)|Wskazuje, czy środowisko CLR skojarzone z interfejsem [ICLRRuntimeInfo](iclrruntimeinfo-interface.md) jest załadowane do procesu.|  
|[IsStarted, metoda](iclrruntimeinfo-isstarted-method.md)|Wskazuje, czy środowisko CLR skojarzone z interfejsem [ICLRRuntimeInfo](iclrruntimeinfo-interface.md) zostało uruchomione.|  
|[LoadErrorString, metoda](iclrruntimeinfo-loaderrorstring-method.md)|Tłumaczy wartość HRESULT na odpowiedni komunikat o błędzie dla określonej kultury. Ta metoda zastępuje metody [LoadStringRC —](loadstringrc-function.md) i [LoadStringRCEx —](loadstringrcex-function.md) .|  
|[LoadLibrary, metoda](iclrruntimeinfo-loadlibrary-method.md)|Ładuje bibliotekę z katalogu struktury środowiska CLR reprezentowanej przez interfejs [ICLRRuntimeInfo](iclrruntimeinfo-interface.md) . Ta metoda zastępuje metodę [LoadLibraryShim —](loadlibraryshim-function.md) .|  
|[SetDefaultStartupFlags, metoda](iclrruntimeinfo-setdefaultstartupflags-method.md)|Ustawia flagi uruchamiania środowiska CLR i plik konfiguracji hosta.|  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).  
  
 **Nagłówek:** Obiekt ServiceHost. h  
  
 **Biblioteka:** Uwzględnione jako zasób w bibliotece MSCorEE. dll  
  
 **.NET Framework wersje:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [Hosting, interfejsy](hosting-interfaces.md)
- [Hosting](index.md)
