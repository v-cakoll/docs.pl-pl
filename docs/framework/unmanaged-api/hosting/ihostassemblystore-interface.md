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
ms.openlocfilehash: 87fe0b10f0a1eefa8154c40d39b54285990c410c
ms.sourcegitcommit: d223616e7e6fe2139079052e6fcbe25413fb9900
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/22/2020
ms.locfileid: "83805033"
---
# <a name="ihostassemblystore-interface"></a>IHostAssemblyStore — Interfejs
Zapewnia metody, które pozwalają hostowi ładować zestawy i moduły niezależnie od środowiska uruchomieniowego języka wspólnego (CLR).  
  
## <a name="methods"></a>Metody  
  
|Metoda|Opis|  
|------------|-----------------|  
|[ProvideAssembly, metoda](../../../../docs/framework/unmanaged-api/hosting/ihostassemblystore-provideassembly-method.md)|Pobiera odwołanie do zestawu, do którego nie odwołuje się [ICLRAssemblyReferenceList](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyreferencelist-interface.md) zwrócone z wywołania [IHostAssemblyManager:: GetNonHostStoreAssemblies —](ihostassemblymanager-getnonhoststoreassemblies-method.md).|  
|[ProvideModule, metoda](ihostassemblystore-providemodule-method.md)|Rozwiązuje moduł w zestawie lub połączonym (nieosadzonym) pliku zasobów.|  
  
## <a name="remarks"></a>Uwagi  
 `IHostAssemblyStore`umożliwia hostowi wydajne ładowanie zestawów w oparciu o tożsamość zestawu. Host ładuje zestawy, zwracając `IStream` wystąpienia bezpośrednio w bajtach.  
  
 Środowisko CLR określa, czy host został zaimplementowany `IHostAssemblyStore` przez wywołanie przy `IHostAssemblyManager::GetNonHostAssemblyStores` inicjacji. Dzięki temu host może na przykład kontrolować powiązania z zestawami użytkowników, ale w celu utworzenia powiązania z zestawami .NET Framework.  
  
> [!NOTE]
> W przypadku wdrażania programu `IHostAssemblyStore` host określa jego zamiar, aby rozpoznać wszystkie zestawy, do których nie odwołują się `ICLRAssemblyReferenceList` zwrócone z `IHostAssemblyManager::GetNonHostStoreAssemblies` .  
  
> [!NOTE]
> .NET Framework wersja 2,0 nie umożliwia hostowi załadowania obrazu natywnego zestawu, zgodnie z opisem w narzędziu [Native Image Generator (Ngen. exe)](../../tools/ngen-exe-native-image-generator.md) .  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).  
  
 **Nagłówek:** MSCorEE. h  
  
 **Biblioteka:** Uwzględnione jako zasób w bibliotece MSCorEE. dll  
  
 **.NET Framework wersje:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Zobacz też

- [ICLRAssemblyReferenceList — Interfejs](iclrassemblyreferencelist-interface.md)
- [IHostAssemblyManager, interfejs](ihostassemblymanager-interface.md)
- [Hosting, interfejsy](hosting-interfaces.md)
