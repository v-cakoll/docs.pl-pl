---
title: IHostMAlloc::DebugAlloc — Metoda
ms.date: 03/30/2017
api_name:
- IHostMAlloc.DebugAlloc
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostMAlloc::DebugAlloc
helpviewer_keywords:
- DebugAlloc method [.NET Framework hosting]
- IHostMAlloc::DebugAlloc method [.NET Framework hosting]
ms.assetid: 0bfbc527-bea2-43ce-b041-69186f4440dd
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 6e089d133374f112dea13e91f9bd571bd2b5af07
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59132928"
---
# <a name="ihostmallocdebugalloc-method"></a>IHostMAlloc::DebugAlloc — Metoda
Żąda hosta przydzielić określonej ilości pamięci sterty i dodatkowo Śledź, gdzie pamięć została alokowana.  
  
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
  
## <a name="parameters"></a>Parametry  
 `cbSize`  
 [in] Rozmiar w bajtach bieżąca żądania alokacji pamięci.  
  
 `dwCriticalLevel`  
 [in] Jedną z [ememorycriticallevel —](../../../../docs/framework/unmanaged-api/hosting/ememorycriticallevel-enumeration.md) wartości, wskazując wpływ wystąpił błąd alokacji.  
  
 `pszFileName`  
 [in] Plik kodu programu do debugowanego pliku wykonywalnego.  
  
 `iLineNo`  
 [in] Numer wiersza w `pszFileName` gdzie zażądano alokacji.  
  
 `ppMem`  
 [out] Wskaźnik do przydzielonej pamięć, lub wartość null, jeśli nie można ukończyć żądania.  
  
## <a name="return-value"></a>Wartość zwracana  
  
|HRESULT|Opis|  
|-------------|-----------------|  
|S_OK|`DebugAlloc` pomyślnie zwrócił.|  
|HOST_E_CLRNOTAVAILABLE|Środowisko CLR nie został załadowany do procesu lub środowisko CLR jest w stanie, w której nie można uruchomić kod zarządzany lub przetworzyć wywołania.|  
|HOST_E_TIMEOUT|Upłynął limit czasu wywołania.|  
|HOST_E_NOT_OWNER|Obiekt wywołujący nie posiada blokady.|  
|HOST_E_ABANDONED|Zdarzenie zostało anulowane podczas zablokowane wątki lub włókna oczekiwał na nim.|  
|E_FAIL|Wystąpił nieznany błąd krytyczny. Po powrocie z metody E_FAIL CLR nie jest już można używać w ramach procesu. Kolejne wywołania do hostowania metody zwracają HOST_E_CLRNOTAVAILABLE.|  
|E_OUTOFMEMORY|Za mało pamięci była dostępna do wykonania żądania alokacji.|  
  
## <a name="remarks"></a>Uwagi  
 Środowisko CLR pobiera wskaźnik interfejsu do [ihostmalloc —](../../../../docs/framework/unmanaged-api/hosting/ihostmalloc-interface.md) wystąpienia, wywołując [ihostmemorymanager::createmalloc —](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-createmalloc-method.md) metody. `DebugAlloc` Umożliwia środowiska uruchomieniowego uzyskać informacje o pliku kod do użycia podczas debugowania.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** MSCorEE.h  
  
 **Biblioteka:** Dołączony jako zasób w MSCorEE.dll  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [IHostMemoryManager, interfejs](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-interface.md)
- [IHostMalloc, interfejs](../../../../docs/framework/unmanaged-api/hosting/ihostmalloc-interface.md)
