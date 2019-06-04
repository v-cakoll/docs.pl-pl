---
title: ICLRRuntimeInfo::IsStarted — Metoda
ms.date: 03/30/2017
api_name:
- ICLRRuntimeInfo.IsStarted
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRRuntimeInfo::IsStarted
helpviewer_keywords:
- IsStarted method [.NET Framework hosting]
- ICLRRuntimeInfo::IsStarted method [.NET Framework hosting]
ms.assetid: ef6f2662-323b-4534-aa82-6d1afb7b9309
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 432de909e1b8166f6d8923889382d9408fb6c62d
ms.sourcegitcommit: 155012a8a826ee8ab6aa49b1b3a3b532e7b7d9bd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2019
ms.locfileid: "66490259"
---
# <a name="iclrruntimeinfoisstarted-method"></a>ICLRRuntimeInfo::IsStarted — Metoda
Wskazuje, czy środowisko uruchomieniowe zostało rozpoczęte (oznacza to, czy [iclrruntimehost::Start — metoda](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-start-method.md) została wywołana i zakończyła się pomyślnie).  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT IsStarted(  
        [out] BOOL     *pbStarted,  
        [out] DWORD    *pdwStartupFlags);  
```  
  
## <a name="parameters"></a>Parametry  
 `pbStarted`  
 [out] `true` Jeżeli to środowisko wykonawcze jest wprowadzenie; w przeciwnym razie `false`.  
  
 `pdwStartupFlags`  
 [out] Zwraca wartość flagi, które były używane do uruchamiania w środowisku uruchomieniowym.  
  
## <a name="return-value"></a>Wartość zwracana  
 Ta metoda zwraca następujące specyficzne wyniki HRESULT, a także HRESULT błędów wskazujących Niepowodzenie metody.  
  
|HRESULT|Opis|  
|-------------|-----------------|  
|S_OK|Metoda została ukończona pomyślnie.|  
|E_NOTIMPL|Typowe wersję środowiska uruchomieniowego języka (wspólnego CLR) jest wcześniejsza niż wersja środowiska CLR programu .NET Framework 4.|  
  
## <a name="remarks"></a>Uwagi  
 Ta metoda nie działa z wersjami środowiska CLR wcześniejsze niż wersja środowiska CLR programu .NET Framework 4.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** MetaHost.h  
  
 **Biblioteka:** Dołączony jako zasób w MSCorEE.dll  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [ICLRRuntimeInfo, interfejs](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md)
- [Hosting, interfejsy](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
- [Hosting](../../../../docs/framework/unmanaged-api/hosting/index.md)
