---
title: IHostSecurityManager::OpenThreadToken — Metoda
ms.date: 03/30/2017
api_name:
- IHostSecurityManager.OpenThreadToken
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostSecurityManager::OpenThreadToken
helpviewer_keywords:
- IHostSecurityManager::OpenThreadToken method [.NET Framework hosting]
- OpenThreadToken method [.NET Framework hosting]
ms.assetid: d5999052-8bf0-4a9e-8621-da6284406b18
topic_type:
- apiref
ms.openlocfilehash: 11d042ea9eecc8d428761da6eaa15f7c2907ebd8
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79176269"
---
# <a name="ihostsecuritymanageropenthreadtoken-method"></a>IHostSecurityManager::OpenThreadToken — Metoda
Otwiera token dostępu uznaniowego skojarzony z aktualnie wykonywanym wątkiem.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT OpenThreadToken (  
    [in]  DWORD    dwDesiredAccess,
    [in]  BOOL     bOpenAsSelf,
    [out] HANDLE   *phThreadToken  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `dwDesiredAccess`  
 [w] Maska wartości dostępu, które określają żądane typy dostępu do tokenu wątku. Wartości te są zdefiniowane `OpenThreadToken` w funkcji Win32. Żądane typy dostępu są uzgadniane z listy kontroli dostępu (DACL) tokenu, aby określić, które typy dostępu do udzielenia lub odmowy.  
  
 `bOpenAsSelf`  
 [w] `true` określenie, że kontrola dostępu powinna być przeprowadzana przy użyciu kontekstu zabezpieczeń procesu dla wątku wywołującego; `false` , aby określić, że sprawdzanie dostępu powinny być wykonywane przy użyciu kontekstu zabezpieczeń dla samego wątku wywołującego. Jeśli wątek personifikuje klienta, kontekst zabezpieczeń może być kontekstu procesu klienta.  
  
 `phThreadToken`  
 [na zewnątrz] Wskaźnik do nowo otwartego tokenu dostępu.  
  
## <a name="return-value"></a>Wartość zwracana  
  
|HRESULT|Opis|  
|-------------|-----------------|  
|S_OK|`OpenThreadToken`zwrócono pomyślnie.|  
|HOST_E_CLRNOTAVAILABLE|Środowisko uruchomieniowe języka wspólnego (CLR) nie został załadowany do procesu lub CLR jest w stanie, w którym nie można uruchomić kod zarządzany lub proces wywołania pomyślnie.|  
|HOST_E_TIMEOUT|Limit czasu połączenia.|  
|HOST_E_NOT_OWNER|Wywołujący nie jest właścicielem blokady.|  
|HOST_E_ABANDONED|Zdarzenie zostało anulowane, gdy czekał na niego zablokowany wątek lub włókno.|  
|E_fail|Doszło do nieznanej katastrofalnej awarii. Gdy metoda zwraca E_FAIL, CLR nie jest już użyteczny w ramach procesu. Kolejne wywołania metod hostingu zwracają HOST_E_CLRNOTAVAILABLE.|  
  
## <a name="remarks"></a>Uwagi  
 `IHostSecurityManager::OpenThreadToken`zachowuje się podobnie do odpowiedniej funkcji Win32 o tej samej nazwie, z tą różnicą, że funkcja Win32 umożliwia obiektowi wywołującemu przekazywanie w dojściu do dowolnego wątku, podczas gdy `IHostSecurityManager::OpenThreadToken` otwiera tylko token skojarzony z wątkiem wywołującym.  
  
 Typ `HANDLE` nie jest zgodny z com, oznacza to, że jego rozmiar jest specyficzny dla systemu operacyjnego i wymaga niestandardowego organizowania. W związku z tym ten token jest do użytku tylko w ramach procesu, między CLR i hosta.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [Wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** MSCorEE.h  
  
 **Biblioteka:** Uwzględnione jako zasób w pliku MSCorEE.dll  
  
 **Wersje programu .NET Framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Zobacz też

- [IHostSecurityContext — Interfejs](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritycontext-interface.md)
- [IHostSecurityManager, interfejs](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritymanager-interface.md)
