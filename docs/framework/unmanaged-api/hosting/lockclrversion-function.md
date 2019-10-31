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
ms.openlocfilehash: 216852f8f051440b2814619b843a1f25013e4042
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73133776"
---
# <a name="lockclrversion-function"></a>LockClrVersion — Funkcja
Umożliwia hostowi określenie, która wersja środowiska uruchomieniowego języka wspólnego (CLR) zostanie użyta w procesie przed jawnym inicjalizacją środowiska CLR.  
  
 Ta funkcja jest przestarzała w .NET Framework 4.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT LockClrVersion (  
    [in] FLockClrVersionCallback   hostCallback,  
    [in] FLockClrVersionCallback  *pBeginHostSetup,  
    [in] FLockClrVersionCallback  *pEndHostSetup  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `hostCallback`  
 podczas Funkcja, która ma zostać wywołana przez środowisko CLR po inicjacji.  
  
 `pBeginHostSetup`  
 podczas Funkcja, która ma zostać wywołana przez hosta w celu poinformowania o uruchamianiu CLR.  
  
 `pEndHostSetup`  
 podczas Funkcja, która ma zostać wywołana przez hosta w celu poinformowania środowiska CLR o ukończeniu inicjalizacji.  
  
## <a name="return-value"></a>Wartość zwracana  
 Ta metoda zwraca standardowe kody błędów COM, jak zdefiniowano w WinError. h, oprócz następujących wartości.  
  
|Kod powrotu|Opis|  
|-----------------|-----------------|  
|S_OK|Metoda została ukończona pomyślnie.|  
|E_INVALIDARG|Co najmniej jeden argument ma wartość null.|  
  
## <a name="remarks"></a>Uwagi  
 Host wywołuje `LockClrVersion` przed zainicjowaniem środowiska CLR. `LockClrVersion` pobiera trzy parametry, z których wszystkie są wywołaniami zwrotnymi typu [FLockClrVersionCallback —](../../../../docs/framework/unmanaged-api/hosting/flockclrversioncallback-function-pointer.md). Ten typ jest definiowany w następujący sposób.  
  
```cpp  
typedef HRESULT ( __stdcall *FLockClrVersionCallback ) ();  
```  
  
 Następujące kroki są wykonywane po zainicjowaniu środowiska uruchomieniowego:  
  
1. Host wywołuje [CorBindToRuntimeEx](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md) lub jedną z innych funkcji inicjalizacji środowiska uruchomieniowego. Alternatywnie host może zainicjować środowisko uruchomieniowe przy użyciu funkcji aktywacji obiektów COM.  
  
2. Środowisko uruchomieniowe wywołuje funkcję określoną przez parametr `hostCallback`.  
  
3. Funkcja określona przez `hostCallback` następnie wykonuje następującą sekwencję wywołań:  
  
    - Funkcja określona przez parametr `pBeginHostSetup`.  
  
    - `CorBindToRuntimeEx` (lub inna funkcja inicjacji środowiska uruchomieniowego).  
  
    - [ICLRRuntimeHost:: SetHostControl —](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-sethostcontrol-method.md).  
  
    - [ICLRRuntimeHost:: Start](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-start-method.md).  
  
    - Funkcja określona przez parametr `pEndHostSetup`.  
  
 Wszystkie wywołania z `pBeginHostSetup` do `pEndHostSetup` muszą wystąpić w pojedynczym wątku lub włókna przy użyciu tego samego logicznego stosu. Ten wątek może się różnić od wątku, w którym wywołano `hostCallback`.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** MSCorEE. h  
  
 **Biblioteka:** MSCorEE. dll  
  
 **Wersje .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [Przestarzałe funkcje hostingu środowiska CLR](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
