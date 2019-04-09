---
title: IHostAssemblyStore — Interfejs
ms.date: 03/30/2017
api_name:
- IHostAssemblyStore
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostAssemblyStore
helpviewer_keywords:
- IHostAssemblyStore interface [.NET Framework hosting]
ms.assetid: cccb650f-abe0-41e2-9fd1-b383788eb1f6
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: d4067c1fbcf99c903c892eaec58262d95569114b
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59173423"
---
# <a name="ihostassemblystore-interface"></a>IHostAssemblyStore — Interfejs
Udostępnia metody, które umożliwiają hosta można załadować zestawów i modułów, niezależnie od środowisko uruchomieniowe języka wspólnego (CLR).  
  
## <a name="methods"></a>Metody  
  
|Metoda|Opis|  
|------------|-----------------|  
|[ProvideAssembly, metoda](../../../../docs/framework/unmanaged-api/hosting/ihostassemblystore-provideassembly-method.md)|Pobiera odwołanie do zestawu, który nie odwołuje się [iclrassemblyreferencelist —](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyreferencelist-interface.md) zwrócony z wywołania do [ihostassemblymanager::getnonhoststoreassemblies —](../../../../docs/framework/unmanaged-api/hosting/ihostassemblymanager-getnonhoststoreassemblies-method.md).|  
|[ProvideModule, metoda](../../../../docs/framework/unmanaged-api/hosting/ihostassemblystore-providemodule-method.md)|Rozpoznaje modułu w obrębie zestawu lub plik połączony zasób (nie embedded).|  
  
## <a name="remarks"></a>Uwagi  
 `IHostAssemblyStore` oferuje hosta można załadować zestawów, efektywnie oparte na tożsamości zestawu. Host ładuje zestawy, zwracając `IStream` wystąpień, które wskazują bezpośrednio na bajty.  
  
 Środowisko CLR określa, czy host ma zaimplementowane `IHostAssemblyStore` przez wywołanie metody `IHostAssemblyManager::GetNonHostAssemblyStores` po zainicjowaniu. Dzięki temu hosta, na przykład kontrolować powiązania do zestawów użytkownika, ale zależą od środowiska uruchomieniowego do powiązania do zestawów .NET Framework.  
  
> [!NOTE]
>  W dostarczaniu implementację `IHostAssemblyStore`, host Określa zamiar Rozwiąż wszystkie zestawy, które nie są przywoływane przez `ICLRAssemblyReferenceList` zwróciło `IHostAssemblyManager::GetNonHostStoreAssemblies`.  
  
> [!NOTE]
>  .NET Framework w wersji 2.0 zapewnia możliwości dla hosta, który można załadować obrazu natywnego zestawu, zgodnie z informacjami od [Native Image Generator (Ngen.exe)](../../../../docs/framework/tools/ngen-exe-native-image-generator.md) narzędzia.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** MSCorEE.h  
  
 **Biblioteka:** Dołączony jako zasób w MSCorEE.dll  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [ICLRAssemblyReferenceList — Interfejs](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyreferencelist-interface.md)
- [IHostAssemblyManager — Interfejs](../../../../docs/framework/unmanaged-api/hosting/ihostassemblymanager-interface.md)
- [Hosting — Interfejsy](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
