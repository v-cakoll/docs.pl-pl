---
title: ICLRReferenceAssemblyEnum::Get — Metoda
ms.date: 03/30/2017
api_name:
- ICLRReferenceAssemblyEnum.Get
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRReferenceAssemblyEnum::Get
helpviewer_keywords:
- ICLRReferenceAssemblyEnum::Get method [.NET Framework hosting]
- Get method, ICLRReferenceAssemblyEnum interface [.NET Framework hosting]
ms.assetid: f21c1612-9c5d-4abc-a337-577086d29c17
topic_type:
- apiref
ms.openlocfilehash: 5afa7b37b804b6a11a894e0e6c7708c7787a20ae
ms.sourcegitcommit: 0926684d8d34f4c6b5acce58d2193db093cb9cf2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/20/2020
ms.locfileid: "83703365"
---
# <a name="iclrreferenceassemblyenumget-method"></a>ICLRReferenceAssemblyEnum::Get — Metoda
Pobiera tożsamość zestawu przy użyciu podanego indeksu.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT Get (  
    [in] DWORD dwIndex,  
    [out, size_is(*pcchBufferSize)] LPWSTR pwzBuffer,  
    [in, out] DWORD *pcchBufferSize  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `dwIndex`  
 podczas Indeks (liczony od zera) tożsamości zestawu do zwrócenia.  
  
 `pwzBuffer`  
 określoną Bufor zawierający dane tożsamości zestawu.  
  
 `pcchBufferSize`  
 [in. out] Rozmiar `pwzBuffer` buforu.  
  
## <a name="return-value"></a>Wartość zwracana  
  
|HRESULT|Opis|  
|-------------|-----------------|  
|S_OK|`Get`pomyślnie zwrócono.|  
|ERROR_INSUFFICIENT_BUFFER|`pwzBuffer`jest za mała.|  
|ERROR_NO_MORE_ITEMS|Wyliczenie nie zawiera żadnych elementów.|  
|HOST_E_CLRNOTAVAILABLE|Środowisko uruchomieniowe języka wspólnego (CLR) nie zostało załadowane do procesu lub środowisko CLR znajduje się w stanie, w którym nie można uruchomić kodu zarządzanego lub przetworzyć wywołania pomyślnie.|  
|HOST_E_TIMEOUT|Upłynął limit czasu połączenia.|  
|HOST_E_NOT_OWNER|Obiekt wywołujący nie jest właocicielem blokady.|  
|HOST_E_ABANDONED|Zdarzenie zostało anulowane podczas oczekiwania na niego zablokowanego wątku lub włókna.|  
|E_FAIL|Wystąpił nieznany błąd krytyczny. Jeśli metoda zwraca E_FAIL, środowisko CLR nie będzie już można używać w procesie. Kolejne wywołania metod hostingu zwracają HOST_E_CLRNOTAVAILABLE.|  
  
## <a name="remarks"></a>Uwagi  
 `Get`jest zazwyczaj wywoływana dwukrotnie. Pierwsze wywołanie dostarcza wartość null dla `pwzBuffer` i ustawia `pcchBufferSize` rozmiar odpowiedni dla `pwzBuffer` . Drugie wywołanie dostarcza odpowiedni rozmiar `pwzBuffer` i zawiera dane tożsamości zestawu kanonicznego po zakończeniu.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).  
  
 **Nagłówek:** MSCorEE. h  
  
 **Biblioteka:** Uwzględnione jako zasób w bibliotece MSCorEE. dll  
  
 **.NET Framework wersje:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [ICLRAssemblyReferenceList — Interfejs](iclrassemblyreferencelist-interface.md)
- [ICLRReferenceAssemblyEnum, interfejs](iclrreferenceassemblyenum-interface.md)
