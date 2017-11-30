---
title: "IHostMAlloc::DebugAlloc — Metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IHostMAlloc.DebugAlloc
api_location: mscoree.dll
api_type: COM
f1_keywords: IHostMAlloc::DebugAlloc
helpviewer_keywords:
- DebugAlloc method [.NET Framework hosting]
- IHostMAlloc::DebugAlloc method [.NET Framework hosting]
ms.assetid: 0bfbc527-bea2-43ce-b041-69186f4440dd
topic_type: apiref
caps.latest.revision: "13"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 18759aa319bf39c49418e3b9388d96829ed52f7f
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="ihostmallocdebugalloc-method"></a>IHostMAlloc::DebugAlloc — Metoda
Żąda przydzielić określoną ilością pamięci sterty hosta, a ponadto śledzić, gdzie została przydzielona pamięć.  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT DebugAlloc (  
    [in]  SIZE_T  cbSize,   
    [in]  EMemoryCriticalLevel dwCriticalLevel,   
    [in]  char*   pszFileName,   
    [in]  int     iLineNo,   
    [out] void**  ppMem  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `cbSize`  
 [in] Rozmiar w bajtach, bieżącego żądania alokacji pamięci.  
  
 `dwCriticalLevel`  
 [in] Jeden z [EMemoryCriticalLevel](../../../../docs/framework/unmanaged-api/hosting/ememorycriticallevel-enumeration.md) wartości i wskazujący wpływ błąd alokacji.  
  
 `pszFileName`  
 [in] Plik kodu wykonywalnego debugowany.  
  
 `iLineNo`  
 [in] Numer wiersza w `pszFileName` których alokacji zażądano.  
  
 `ppMem`  
 [out] Wskaźnik do alokacji pamięci lub wartość null, jeśli nie można ukończyć żądania.  
  
## <a name="return-value"></a>Wartość zwracana  
  
|HRESULT|Opis|  
|-------------|-----------------|  
|S_OK|`DebugAlloc`zwrócona pomyślnie.|  
|HOST_E_CLRNOTAVAILABLE|Środowisko CLR nie został załadowany do procesu lub CLR jest w stanie, w którym nie można uruchamiać kodu zarządzanego lub pomyślnie przetworzyć wywołania.|  
|HOST_E_TIMEOUT|Upłynął limit czasu wywołania.|  
|HOST_E_NOT_OWNER|Obiekt wywołujący nie jest właścicielem blokady.|  
|HOST_E_ABANDONED|Zdarzenie zostało anulowane podczas zablokowanych wątku lub włókna oczekiwał na nim.|  
|E_FAIL|Wystąpił nieznany błąd krytyczny. Gdy metoda zwróci wartość E_FAIL, CLR nie jest już możliwe w ramach procesu. Kolejne wywołania metody hosting zwracać HOST_E_CLRNOTAVAILABLE.|  
|E_OUTOFMEMORY|Za mało pamięci nie była dostępna do wykonania żądania alokacji.|  
  
## <a name="remarks"></a>Uwagi  
 Środowisko CLR pobiera wskaźnika interfejsu do [IHostMalloc](../../../../docs/framework/unmanaged-api/hosting/ihostmalloc-interface.md) wystąpienia przez wywołanie metody [IHostMemoryManager::CreateMalloc](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-createmalloc-method.md) metody. `DebugAlloc`Umożliwia środowiska wykonawczego uzyskać informacje o pliku kodu do użycia podczas debugowania.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** MSCorEE.h  
  
 **Biblioteka:** uwzględnione jako zasób w MSCorEE.dll  
  
 **Wersje programu .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Zobacz też  
 [IHostMemoryManager — interfejs](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-interface.md)  
 [IHostMalloc — interfejs](../../../../docs/framework/unmanaged-api/hosting/ihostmalloc-interface.md)
