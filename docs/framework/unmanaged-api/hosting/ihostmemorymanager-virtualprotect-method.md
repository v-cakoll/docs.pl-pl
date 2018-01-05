---
title: "IHostMemoryManager::VirtualProtect — Metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IHostMemoryManager.VirtualProtect
api_location: mscoree.dll
api_type: COM
f1_keywords: IHostMemoryManager::VirtualProtect
helpviewer_keywords:
- IHostMemoryManager::VirtualProtect method [.NET Framework hosting]
- VirtualProtect method [.NET Framework hosting]
ms.assetid: 13be0299-df0d-4951-aabf-0676a30b385f
topic_type: apiref
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 77e8e163a16752934d0a1d826cc8463b3d3281bd
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="ihostmemorymanagervirtualprotect-method"></a>IHostMemoryManager::VirtualProtect — Metoda
Służy jako otoka logiczne dla odpowiedniej funkcji Win32. Implementacja Win32 `VirtualProtect` zmienia ochrony obszaru zatwierdzone stron w wirtualnej przestrzeni adresowej procesu wywołującego.  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT VirtualProtect (  
    [in]  void*   lpAddress,  
    [in]  SIZE_T  dwSize,  
    [in]  DWORD   flNewProtect,  
    [out] DWORD*  pflOldProtect  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `lpAddress`  
 [in] Wskaźnik do adresu podstawowego przestrzeni pamięci wirtualnej, w których atrybuty ochrony są zostanie zmieniony.  
  
 `dwSize`  
 [in] Rozmiar w bajtach obszaru pamięci stron zostać zmienione.  
  
 `flNewProtect`  
 [in] Typ ochrony pamięci do zastosowania.  
  
 `pflOldProtect`  
 [out] Wskaźnik do poprzedniej wartości ochrony pamięci.  
  
## <a name="return-value"></a>Wartość zwracana  
  
|HRESULT|Opis|  
|-------------|-----------------|  
|S_OK|`VirtualProtect`zwrócona pomyślnie.|  
|HOST_E_CLRNOTAVAILABLE|Środowisko uruchomieniowe języka wspólnego (CLR) nie został załadowany do procesu lub CLR jest w stanie, w którym nie można uruchamiać kodu zarządzanego lub pomyślnie przetworzyć wywołania.|  
|HOST_E_TIMEOUT|Upłynął limit czasu wywołania.|  
|HOST_E_NOT_OWNER|Obiekt wywołujący nie jest właścicielem blokady.|  
|HOST_E_ABANDONED|Zdarzenie zostało anulowane podczas zablokowanych wątku lub włókna oczekiwał na nim.|  
|E_FAIL|Wystąpił nieznany błąd krytyczny. Gdy metoda zwróci wartość E_FAIL, CLR nie jest już możliwe w ramach procesu. Kolejne wywołania metody hosting zwracać HOST_E_CLRNOTAVAILABLE.|  
  
## <a name="remarks"></a>Uwagi  
 Ta implementacja `VirtualProtect` zwraca wartość HRESULT, podczas gdy Win32 implementacja zwraca wartość inną niż zero, informując o powodzeniu i wartość zero do wskazania błędu. Aby uzyskać więcej informacji zobacz dokumentację platformy systemu Windows.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** MSCorEE.h  
  
 **Biblioteka:** uwzględnione jako zasób w MSCorEE.dll  
  
 **Wersje programu .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Zobacz też  
 [IHostMemoryManager, interfejs](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-interface.md)
