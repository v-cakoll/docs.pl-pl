---
title: "IHostAssemblyManager::GetNonHostStoreAssemblies — Metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IHostAssemblyManager.GetNonHostStoreAssemblies
api_location: mscoree.dll
api_type: COM
f1_keywords: IHostAssemblyManager::GetNonHostStoreAssemblies
helpviewer_keywords:
- IHostAssemblyManager::GetNonHostStoreAssemblies method [.NET Framework hosting]
- GetNonHostStoreAssemblies method [.NET Framework hosting]
ms.assetid: d2250b38-c76a-40ce-80c8-ba45149886e8
topic_type: apiref
caps.latest.revision: "10"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 35e22e186b290cc4242275976f5109b73e2cf068
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="ihostassemblymanagergetnonhoststoreassemblies-method"></a>IHostAssemblyManager::GetNonHostStoreAssemblies — Metoda
Pobiera wskaźnika interfejsu do [ICLRAssemblyReferenceList](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyreferencelist-interface.md) reprezentujący listę zestawów, które host oczekuje środowisko uruchomieniowe języka wspólnego (CLR) do załadowania.  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT GetNonHostStoreAssemblies (  
    [out] ICLRAssemblyReferenceList **ppReferenceList  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `ppReferenceList`  
 [out] Wskaźnik do adresu `ICLRAssemblyReferenceList` zawierający listę odwołań do zestawów, które host oczekuje można załadować środowiska CLR.  
  
## <a name="return-value"></a>Wartość zwracana  
  
|HRESULT|Opis|  
|-------------|-----------------|  
|S_OK|`GetNonHostStoreAssemblies`zwrócona pomyślnie.|  
|HOST_E_CLRNOTAVAILABLE|Środowisko CLR nie został załadowany do procesu lub CLR jest w stanie, w którym nie można uruchamiać kodu zarządzanego lub pomyślnie przetworzyć wywołania.|  
|HOST_E_TIMEOUT|Upłynął limit czasu wywołania.|  
|HOST_E_NOT_OWNER|Obiekt wywołujący nie jest właścicielem blokady.|  
|HOST_E_ABANDONED|Zdarzenie zostało anulowane podczas zablokowanych wątku lub włókna oczekiwał na nim.|  
|E_FAIL|Wystąpił nieznany błąd krytyczny. Gdy metoda zwróci wartość E_FAIL, CLR nie jest już możliwe w ramach procesu. Kolejne wywołania metody hosting zwracać HOST_E_CLRNOTAVAILABLE.|  
|E_OUTOFMEMORY|Za mało pamięci była dostępna utworzyć listę odwołania dla żądanego `ICLRAssemblyReferenceList`.|  
  
## <a name="remarks"></a>Uwagi  
 Środowisko CLR rozpoznaje odwołań za pomocą zestawu następujących wytycznych:  
  
-   Najpierw należy go sprawdza listy odwołania do zestawów zwrócony przez `GetNonHostStoreAssemblies`.  
  
-   Jeśli zestaw znajduje się na liście, CLR powiązanie go normalnie.  
  
-   Jeśli zestaw nie ma na liście, a host udostępnił implementacja [IHostAssemblyStore](../../../../docs/framework/unmanaged-api/hosting/ihostassemblystore-interface.md), wywołania CLR [IHostAssemblyStore::ProvideAssembly](../../../../docs/framework/unmanaged-api/hosting/ihostassemblystore-provideassembly-method.md) umożliwia hosta do dostarczania zestaw do powiązania.  
  
-   W przeciwnym razie wartość CLR nie może powiązać zestawu.  
  
 Jeśli host ustawia `ppReferenceList` równej null, sond pierwszy CLR wywołuje globalnej pamięci podręcznej zestawów, `ProvideAssembly`, a następnie sondy baza aplikacji można rozpoznać odwołania do zestawu.  
  
> [!NOTE]
>  Po zainicjowaniu, wywołuje CLR `GetNonHostStoreAssemblies` tylko raz. Metoda nie zostanie ponownie wywołany.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** MSCorEE.h  
  
 **Biblioteka:** uwzględnione jako zasób w MSCorEE.dll  
  
 **Wersje programu .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Zobacz też  
 [ICLRAssemblyReferenceList — interfejs](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyreferencelist-interface.md)  
 [IHostAssemblyManager — interfejs](../../../../docs/framework/unmanaged-api/hosting/ihostassemblymanager-interface.md)  
 [IHostAssemblyStore — interfejs](../../../../docs/framework/unmanaged-api/hosting/ihostassemblystore-interface.md)
