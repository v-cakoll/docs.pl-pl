---
title: "IHostAssemblyStore — Interfejs"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IHostAssemblyStore
api_location: mscoree.dll
api_type: COM
f1_keywords: IHostAssemblyStore
helpviewer_keywords: IHostAssemblyStore interface [.NET Framework hosting]
ms.assetid: cccb650f-abe0-41e2-9fd1-b383788eb1f6
topic_type: apiref
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 284afbe73bea28a0aafe8d5e9e030c43be94aea4
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="ihostassemblystore-interface"></a>IHostAssemblyStore — Interfejs
Udostępnia metody umożliwiające hosta można załadować zestawów i modułów, niezależnie od środowisko uruchomieniowe języka wspólnego (CLR).  
  
## <a name="methods"></a>Metody  
  
|Metoda|Opis|  
|------------|-----------------|  
|[ProvideAssembly — metoda](../../../../docs/framework/unmanaged-api/hosting/ihostassemblystore-provideassembly-method.md)|Pobiera odwołanie do zestawu, który nie jest wywoływany przez [ICLRAssemblyReferenceList](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyreferencelist-interface.md) zwrócone w wyniku wywołania [IHostAssemblyManager::GetNonHostStoreAssemblies](../../../../docs/framework/unmanaged-api/hosting/ihostassemblymanager-getnonhoststoreassemblies-method.md).|  
|[ProvideModule — metoda](../../../../docs/framework/unmanaged-api/hosting/ihostassemblystore-providemodule-method.md)|Rozpoznaje modułu w ramach zestawu lub połączonego pliku zasobów (nie embedded).|  
  
## <a name="remarks"></a>Uwagi  
 `IHostAssemblyStore`Umożliwia ładowanie zestawów wydajnie oparte na tożsamości zestawu hosta. Host ładuje zestawy zwracając `IStream` wystąpień, które wskazują bezpośrednio na bajty.  
  
 Środowisko CLR określa, czy host ma zaimplementowany `IHostAssemblyStore` przez wywołanie metody `IHostAssemblyManager::GetNonHostAssemblyStores` po zainicjowaniu. Dzięki temu hosta, na przykład kontrolować powiązania zestawów użytkownika, ale zależą od środowiska wykonawczego, aby powiązać zestawy .NET Framework.  
  
> [!NOTE]
>  Dostarczając implementację `IHostAssemblyStore`, host Określa chęć rozwiązać wszystkie zestawy, których nie odwołuje się `ICLRAssemblyReferenceList` zwrócony z `IHostAssemblyManager::GetNonHostStoreAssemblies`.  
  
> [!NOTE]
>  .NET Framework w wersji 2.0 nie umożliwiają na załadowanie obrazu macierzystego zestawu hosta dostarczone przez [Generator obrazu natywnego (Ngen.exe)](../../../../docs/framework/tools/ngen-exe-native-image-generator.md) narzędzia.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** MSCorEE.h  
  
 **Biblioteka:** uwzględnione jako zasób w MSCorEE.dll  
  
 **Wersje programu .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Zobacz też  
 [ICLRAssemblyReferenceList — interfejs](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyreferencelist-interface.md)  
 [IHostAssemblyManager — interfejs](../../../../docs/framework/unmanaged-api/hosting/ihostassemblymanager-interface.md)  
 [Hosting — interfejsy](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
