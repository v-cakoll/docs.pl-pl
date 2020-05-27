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
ms.openlocfilehash: 09bcebfdcfea3d5728d404cdb6b5fb170a5432c3
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/27/2020
ms.locfileid: "84008498"
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
 Host wywołuje `LockClrVersion` przed zainicjowaniem środowiska CLR. `LockClrVersion`Pobiera trzy parametry, z których wszystkie są wywołaniami zwrotnymi typu [FLockClrVersionCallback —](flockclrversioncallback-function-pointer.md). Ten typ jest definiowany w następujący sposób.  
  
```cpp  
typedef HRESULT ( __stdcall *FLockClrVersionCallback ) ();  
```  
  
 Następujące kroki są wykonywane po zainicjowaniu środowiska uruchomieniowego:  
  
1. Host wywołuje [CorBindToRuntimeEx](corbindtoruntimeex-function.md) lub jedną z innych funkcji inicjalizacji środowiska uruchomieniowego. Alternatywnie host może zainicjować środowisko uruchomieniowe przy użyciu funkcji aktywacji obiektów COM.  
  
2. Środowisko uruchomieniowe wywołuje funkcję określoną przez `hostCallback` parametr.  
  
3. Funkcja określona przez `hostCallback` then wykonuje następującą sekwencję wywołań:  
  
    - Funkcja określona przez `pBeginHostSetup` parametr.  
  
    - `CorBindToRuntimeEx`(lub inna funkcja inicjacji środowiska uruchomieniowego).  
  
    - [ICLRRuntimeHost:: SetHostControl —](iclrruntimehost-sethostcontrol-method.md).  
  
    - [ICLRRuntimeHost:: Start](iclrruntimehost-start-method.md).  
  
    - Funkcja określona przez `pEndHostSetup` parametr.  
  
 Wszystkie wywołania z `pBeginHostSetup` programu `pEndHostSetup` muszą odbywać się w pojedynczym wątku lub włókna przy użyciu tego samego stosu logicznego. Ten wątek może się różnić od wątku, w którym `hostCallback` jest wywoływana.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).  
  
 **Nagłówek:** MSCorEE. h  
  
 **Biblioteka:** MSCorEE. dll  
  
 **.NET Framework wersje:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Zobacz też

- [Przestarzałe funkcje hostingu środowiska CLR](deprecated-clr-hosting-functions.md)
