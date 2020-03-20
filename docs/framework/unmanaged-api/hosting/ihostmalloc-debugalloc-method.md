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
ms.openlocfilehash: 20ad5485b8603cc7de1c27c00d53c8939871d525
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79178034"
---
# <a name="ihostmallocdebugalloc-method"></a>IHostMAlloc::DebugAlloc — Metoda
Żąda, aby host przydzielić określoną ilość pamięci ze sterty i dodatkowo śledzić, gdzie pamięć została przydzielona.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
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
 [w] Rozmiar w bajtach bieżącego żądania alokacji pamięci.  
  
 `dwCriticalLevel`  
 [w] Jedna z [wartości EMemoryCriticalLevel,](../../../../docs/framework/unmanaged-api/hosting/ememorycriticallevel-enumeration.md) wskazująca wpływ błędu alokacji.  
  
 `pszFileName`  
 [w] Plik kodu pliku wykonywalnego jest debugowany.  
  
 `iLineNo`  
 [w] Numer wiersza `pszFileName` w miejscu, w którym zażądano alokacji.  
  
 `ppMem`  
 [na zewnątrz] Wskaźnik do przydzielonej pamięci lub null, jeśli nie można ukończyć żądania.  
  
## <a name="return-value"></a>Wartość zwracana  
  
|HRESULT|Opis|  
|-------------|-----------------|  
|S_OK|`DebugAlloc`zwrócono pomyślnie.|  
|HOST_E_CLRNOTAVAILABLE|Clr nie został załadowany do procesu lub CLR jest w stanie, w którym nie można uruchomić kod zarządzany lub proces wywołania pomyślnie.|  
|HOST_E_TIMEOUT|Limit czasu połączenia.|  
|HOST_E_NOT_OWNER|Wywołujący nie jest właścicielem blokady.|  
|HOST_E_ABANDONED|Zdarzenie zostało anulowane, gdy czekał na niego zablokowany wątek lub włókno.|  
|E_fail|Doszło do nieznanej katastrofalnej awarii. Gdy metoda zwraca E_FAIL, CLR nie jest już użyteczny w ramach procesu. Kolejne wywołania metod hostingu zwracają HOST_E_CLRNOTAVAILABLE.|  
|E_outofmemory|Za mało pamięci było dostępne, aby zakończyć żądanie alokacji.|  
  
## <a name="remarks"></a>Uwagi  
 CLR pobiera wskaźnik interfejsu do [wystąpienia IHostMalloc](../../../../docs/framework/unmanaged-api/hosting/ihostmalloc-interface.md) wywołując [IHostMemoryManager::CreateMalloc](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-createmalloc-method.md) metody. `DebugAlloc`umożliwia środowisko wykonawcze, aby uzyskać informacje o pliku kodu do użycia podczas debugowania.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [Wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** MSCorEE.h  
  
 **Biblioteka:** Uwzględnione jako zasób w pliku MSCorEE.dll  
  
 **Wersje programu .NET Framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Zobacz też

- [IHostMemoryManager, interfejs](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-interface.md)
- [IHostMalloc, interfejs](../../../../docs/framework/unmanaged-api/hosting/ihostmalloc-interface.md)
