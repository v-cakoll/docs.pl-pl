---
title: LockClrVersion — Funkcja
ms.date: 03/30/2017
api_name:
- LockClrVersion
api_location:
- mscoree.dll
- mscoreei.dll
api_type:
- DLLExport
f1_keywords:
- LockClrVersion
helpviewer_keywords:
- LockClrVersion function [.NET Framework hosting]
ms.assetid: 1318ee37-c43b-40eb-bbe8-88fc46453d74
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 91bb1a9416e577dbb5cc96e8be87033c53232811
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59336697"
---
# <a name="lockclrversion-function"></a>LockClrVersion — Funkcja
Umożliwia hostowi na określenie, która wersja środowiska uruchomieniowego języka wspólnego (CLR), będą używane w ramach procesu przed jawnym zainicjowaniem środowiska CLR.  
  
 Ta funkcja jest przestarzała w [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)].  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT LockClrVersion (  
    [in] FLockClrVersionCallback   hostCallback,  
    [in] FLockClrVersionCallback  *pBeginHostSetup,  
    [in] FLockClrVersionCallback  *pEndHostSetup  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `hostCallback`  
 [in] Funkcja, która ma zostać wywołana przez środowisko CLR po zainicjowaniu.  
  
 `pBeginHostSetup`  
 [in] Funkcja wywoływana przez hosta w celu poinformowania środowiska CLR, że inicjowanie jest uruchamiana.  
  
 `pEndHostSetup`  
 [in] Funkcja wywoływana przez hosta w celu poinformowania środowiska CLR, że Inicjowanie zostało ukończone.  
  
## <a name="return-value"></a>Wartość zwracana  
 Ta metoda zwraca standardowe kody błędu modelu COM, zgodnie z definicją w pliku WinError.h oprócz następujących wartości.  
  
|Kod powrotu|Opis|  
|-----------------|-----------------|  
|S_OK|Metoda została ukończona pomyślnie.|  
|E_INVALIDARG|Co najmniej jeden z argumentów ma wartość null.|  
  
## <a name="remarks"></a>Uwagi  
 Wywołania hosta `LockClrVersion` przed zainicjowaniem środowiska CLR. `LockClrVersion` przyjmuje trzy parametry, które są wywołania zwrotne typu [FLockClrVersionCallback](../../../../docs/framework/unmanaged-api/hosting/flockclrversioncallback-function-pointer.md). Ten typ jest zdefiniowany w następujący sposób.  
  
```  
typedef HRESULT ( __stdcall *FLockClrVersionCallback ) ();  
```  
  
 Po zainicjowaniu środowiska uruchomieniowego są wykonywane następujące kroki:  
  
1. Wywołania hosta [CorBindToRuntimeEx](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md) lub jednego z innych funkcji inicjowania środowiska uruchomieniowego. Alternatywnie hosta można zainicjować aparatu plików wykonywalnych przy użyciu aktywowanie obiektu COM.  
  
2. Środowisko wykonawcze wywołuje funkcji określonej przez `hostCallback` parametru.  
  
3. Funkcji określonej przez `hostCallback` następnie sprawia, że następująca sekwencja wywołań:  
  
    -   Funkcji określonej przez `pBeginHostSetup` parametru.  
  
    -   `CorBindToRuntimeEx` (lub inną funkcję inicjowania środowiska uruchomieniowego).  
  
    -   [ICLRRuntimeHost::SetHostControl](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-sethostcontrol-method.md).  
  
    -   [Iclrruntimehost::Start —](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-start-method.md).  
  
    -   Funkcji określonej przez `pEndHostSetup` parametru.  
  
 Wszystkie wywołania z `pBeginHostSetup` do `pEndHostSetup` musi przypadać na jednym wątku lub włókna, z tym samym stosie logiczne. Ten wątek może różnić się od wątku, na którym `hostCallback` jest wywoływana.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** MSCorEE.h  
  
 **Biblioteka:** MSCorEE.dll  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [Przestarzałe funkcje hostingu środowiska CLR](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
