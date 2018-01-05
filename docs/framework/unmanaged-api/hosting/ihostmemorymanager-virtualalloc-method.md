---
title: "IHostMemoryManager::VirtualAlloc — Metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IHostMemoryManager.VirtualAlloc
api_location: mscoree.dll
api_type: COM
f1_keywords: IHostMemoryManager::VirtualAlloc
helpviewer_keywords:
- VirtualAlloc method [.NET Framework hosting]
- IHostMemoryManager::VirtualAlloc method [.NET Framework hosting]
ms.assetid: 4dff3646-a050-4bd9-ac31-fe307e8637ec
topic_type: apiref
caps.latest.revision: "14"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 761958c44ad374d522a52826929e320e65957ffa
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="ihostmemorymanagervirtualalloc-method"></a>IHostMemoryManager::VirtualAlloc — Metoda
Służy jako otoka logiczne dla odpowiedniej funkcji Win32. Implementacja Win32 `VirtualAlloc` rezerwuje lub zatwierdza region stron w wirtualnej przestrzeni adresowej procesu wywołującego.  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT VirtualAlloc (  
    [in]  void*   pAddress,  
    [in]  SIZE_T  dwSize,  
    [in]  DWORD   flAllocationType,  
    [in]  DWORD   flProtect,  
    [in]  EMemoryCriticalLevel dwCriticalLevel,  
    [out] void**  ppMem  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `pAddress`  
 [in] Wskaźnik do regionu przydzielić adres początkowy.  
  
 `dwSize`  
 [in] Rozmiar w bajtach regionu.  
  
 `flAllocationType`  
 [in] Typ alokacji pamięci.  
  
 `flProtect`  
 [in] Ochrona pamięci dla regionu stron do przydzielenia.  
  
 `dwCriticalLevel`  
 [in] [EMemoryCriticalLevel](../../../../docs/framework/unmanaged-api/hosting/ememorycriticallevel-enumeration.md) wartość, która wskazuje wpływ błąd alokacji.  
  
 `ppMem`  
 [out] Wskaźnik do adres początkowy alokacji pamięci lub wartość null, jeśli nie można spełnić żądania.  
  
## <a name="return-value"></a>Wartość zwracana  
  
|HRESULT|Opis|  
|-------------|-----------------|  
|S_OK|`VirtualAlloc`zwrócona pomyślnie.|  
|HOST_E_CLRNOTAVAILABLE|Środowisko uruchomieniowe języka wspólnego (CLR) nie został załadowany do procesu lub CLR jest w stanie, w którym nie można uruchamiać kodu zarządzanego lub pomyślnie przetworzyć wywołania.|  
|HOST_E_TIMEOUT|Upłynął limit czasu wywołania.|  
|HOST_E_NOT_OWNER|Obiekt wywołujący nie jest właścicielem blokady.|  
|HOST_E_ABANDONED|Zdarzenie zostało anulowane podczas zablokowanych wątku lub włókna oczekiwał na nim.|  
|E_FAIL|Wystąpił nieznany błąd krytyczny. Gdy metoda zwróci wartość E_FAIL, CLR nie jest już możliwe w ramach procesu. Kolejne wywołania metody hosting zwracać HOST_E_CLRNOTAVAILABLE.|  
|E_OUTOFMEMORY|Za mało pamięci był dostępny do wykonania żądania alokacji|  
  
## <a name="remarks"></a>Uwagi  
 Zarezerwować region przestrzeni adresowej procesu, wywołując `VirtualAlloc`. `pAddress` Parametr zawiera początkowy adres ma bloku pamięci. Ten parametr jest zwykle ustawiana na wartość null. System operacyjny jest rejestrowana zakresy wolnego adresu dostępne dla procesu. A `pAddress` wartość null powoduje, że system do zarezerwowania region wszędzie tam, gdzie za stosowny. Alternatywnie możesz podać określony adres początkowy dla bloku pamięci. W obu przypadkach parametr wyjściowy `ppMem` jest zwracana jako wskaźnik do alokacji pamięci. Ta funkcja zwraca wartość HRESULT.  
  
 Win32 `VirtualAlloc` funkcja nie ma `ppMem` parametr, a zamiast tego zwraca wskaźnik do alokacji pamięci. Aby uzyskać więcej informacji zobacz dokumentację platformy systemu Windows.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** MSCorEE.h  
  
 **Biblioteka:** uwzględnione jako zasób w MSCorEE.dll  
  
 **Wersje programu .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Zobacz też  
 [IHostMemoryManager, interfejs](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-interface.md)
