---
title: ICLRGCManager2::SetGCStartupLimitsEx — Metoda
ms.date: 03/30/2017
api_name:
- ICLRGCManager2.SetGCStartupLimitsEx
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRGCManager2::SetCLRGCStartupLimitsEx
helpviewer_keywords:
- ICLRGCManager2::SetGCStartupLimitsEx method [.NET Framework hosting]
- SetGCStartupLimitsEx method, ICLRGCManager2 interface [.NET Framework hosting]
ms.assetid: 6c3a08a9-5d65-48d4-8bbf-2a86ed7d356a
topic_type:
- apiref
ms.openlocfilehash: 9885149a71147db6eef13958b8ef825caa1d6ec6
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79176386"
---
# <a name="iclrgcmanager2setgcstartuplimitsex-method"></a>ICLRGCManager2::SetGCStartupLimitsEx — Metoda
Ustawia rozmiar segmentu wyrzucania elementów bezużytecznych i maksymalny rozmiar generacji 0 systemu wyrzucania elementów bezużytecznych.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT SetGCStartupLimitsEx (  
    [in] SIZE_T SegmentSize,
    [in] SIZE_T MaxGen0Size  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `SegmentSize`  
 [w] Określony rozmiar segmentu wyrzucania elementów bezużytecznych.  
  
 Minimalny rozmiar segmentu to 4 MB. Segmenty można zwiększać w przyrostach co 1 MB lub większych.  
  
 `MaxGen0Size`  
 [w] Określony maksymalny rozmiar dla generacji 0.  
  
 Minimalna generacja 0 rozmiar jest 64 KB.  
  
## <a name="return-value"></a>Wartość zwracana  
  
|HRESULT|Opis|  
|-------------|-----------------|  
|S_OK|`SetGCStartupLimitsEx`zwrócono pomyślnie.|  
|HOST_E_CLRNOTAVAILABLE|Środowisko uruchomieniowe języka wspólnego (CLR) nie został załadowany do procesu lub CLR jest w stanie, w którym nie można uruchomić kod zarządzany lub proces wywołania pomyślnie.|  
|HOST_E_TIMEOUT|Limit czasu połączenia.|  
|HOST_E_NOT_OWNER|Wywołujący nie jest właścicielem blokady.|  
|HOST_E_ABANDONED|Zdarzenie zostało anulowane, gdy czekał na niego zablokowany wątek lub włókno.|  
|E_fail|Doszło do nieznanej katastrofalnej awarii. Po metoda zwraca E_FAIL, CLR nie jest już użyteczny w procesie. Kolejne wywołania metod hostingu zwracają HOST_E_CLRNOTAVAILABLE.|  
  
## <a name="remarks"></a>Uwagi  
 Wartości, `SetGCStartupLimitsEx` które ustawia można określić tylko przed rozpoczęciem hosta. Późniejsze `SetGCStartupLimitsEx` wywołania są ignorowane.  
  
 Aby ustawić jeden z tych parametrów bez wpływu na drugi, określ 0 (zero) dla parametru, którego nie chcesz zmienić.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [Wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** MSCorEE.h  
  
 **Biblioteka:** Uwzględnione jako zasób w pliku MSCorEE.dll  
  
 **Wersje programu .NET Framework:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>Zobacz też

- [Automatyczne zarządzanie pamięcią](../../../standard/automatic-memory-management.md)
- [Odzyskiwanie pamięci](../../../standard/garbage-collection/index.md)
- [ICLRControl — Interfejs](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-interface.md)
- [ICLRGCManager2 — Interfejs](../../../../docs/framework/unmanaged-api/hosting/iclrgcmanager2-interface.md)
