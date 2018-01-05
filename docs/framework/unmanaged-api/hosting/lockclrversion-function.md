---
title: "LockClrVersion — Funkcja"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: LockClrVersion
api_location:
- mscoree.dll
- mscoreei.dll
api_type: DLLExport
f1_keywords: LockClrVersion
helpviewer_keywords: LockClrVersion function [.NET Framework hosting]
ms.assetid: 1318ee37-c43b-40eb-bbe8-88fc46453d74
topic_type: apiref
caps.latest.revision: "15"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: a58d7e99f545026f6f133901ef35a1f9b9fabc7d
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="lockclrversion-function"></a>LockClrVersion — Funkcja
Umożliwia hosta określić, która wersja środowisko uruchomieniowe języka wspólnego (CLR) będzie używany w ramach procesu przed jawnie inicjowania CLR.  
  
 Ta funkcja jest przestarzała w [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)].  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT LockClrVersion (  
    [in] FLockClrVersionCallback   hostCallback,  
    [in] FLockClrVersionCallback  *pBeginHostSetup,  
    [in] FLockClrVersionCallback  *pEndHostSetup  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `hostCallback`  
 [in] Funkcja wywoływana przez środowisko CLR po zainicjowaniu.  
  
 `pBeginHostSetup`  
 [in] Funkcja wywoływana przez hosta CLR informują tego inicjowania jest uruchamiana.  
  
 `pEndHostSetup`  
 [in] Funkcja wywoływana przez hosta CLR informują tego inicjowania jest ukończona.  
  
## <a name="return-value"></a>Wartość zwracana  
 Ta metoda zwraca standardowe kody błędów COM, zgodnie z definicją w pliku WinError.h oprócz następujących wartości.  
  
|Kod powrotu|Opis|  
|-----------------|-----------------|  
|S_OK|Metoda została ukończona pomyślnie.|  
|E_INVALIDARG|Co najmniej jeden z argumentów ma wartość null.|  
  
## <a name="remarks"></a>Uwagi  
 Wywołania hosta `LockClrVersion` przed inicjowania CLR. `LockClrVersion`przyjmuje trzy parametry, które są wywołania zwrotne typu [flockclrversioncallback —](../../../../docs/framework/unmanaged-api/hosting/flockclrversioncallback-function-pointer.md). Ten typ jest zdefiniowany w następujący sposób.  
  
```  
typedef HRESULT ( __stdcall *FLockClrVersionCallback ) ();  
```  
  
 Po zainicjowaniu środowiska uruchomieniowego są wykonywane następujące czynności:  
  
1.  Wywołania hosta [CorBindToRuntimeEx](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md) lub jednego z innych funkcji inicjowania środowiska uruchomieniowego. Alternatywnie hosta można zainicjować za pomocą aktywacji obiektu COM środowiska uruchomieniowego.  
  
2.  Środowisko uruchomieniowe wywołania funkcji określonej przez `hostCallback` parametru.  
  
3.  Funkcji określonej przez `hostCallback` następnie sprawia, że następująca sekwencja wywołania:  
  
    -   Funkcji określonej przez `pBeginHostSetup` parametru.  
  
    -   `CorBindToRuntimeEx`(lub inną funkcję inicjowania środowiska uruchomieniowego).  
  
    -   [ICLRRuntimeHost::SetHostControl](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-sethostcontrol-method.md).  
  
    -   [ICLRRuntimeHost::Start](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-start-method.md).  
  
    -   Funkcji określonej przez `pEndHostSetup` parametru.  
  
 Wszystkie wywołania z `pBeginHostSetup` do `pEndHostSetup` musi występować w jednym wątku lub włókna, z tym samym stosie logiczne. Ten wątek może być inny niż wątek, na którym `hostCallback` jest wywoływana.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** MSCorEE.h  
  
 **Biblioteka:** biblioteki MSCorEE.dll  
  
 **Wersje programu .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Zobacz też  
 [Przestarzałe funkcje hostingu środowiska CLR](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
