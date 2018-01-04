---
title: "RUNTIME_INFO_FLAGS — Wyliczenie"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: RUNTIME_INFO_FLAGS
api_location: mscoree.dll
api_type: COM
f1_keywords: RUNTIME_INFO_FLAGS
helpviewer_keywords: RUNTIME_INFO_FLAGS enumeration [.NET Framework hosting]
ms.assetid: adba37be-f775-4cdb-8919-5746ce694f33
topic_type: apiref
caps.latest.revision: "14"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: d050972857ba652ae0b40727260f681c383208b0
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="runtimeinfoflags-enumeration"></a>RUNTIME_INFO_FLAGS — Wyliczenie
Zawiera wartości, które wskazują, jakie informacje o środowisko uruchomieniowe języka wspólnego (CLR) ma zostać zwrócony.  
  
## <a name="syntax"></a>Składnia  
  
```  
typedef enum {  
  
    RUNTIME_INFO_UPGRADE_VERSION             = 0x01,  
    RUNTIME_INFO_REQUEST_IA64                = 0x02,  
    RUNTIME_INFO_REQUEST_AMD64               = 0x04,  
    RUNTIME_INFO_REQUEST_X86                 = 0x08,  
    RUNTIME_INFO_DONT_RETURN_DIRECTORY       = 0x10,  
    RUNTIME_INFO_DONT_RETURN_VERSION         = 0x20,  
    RUNTIME_INFO_DONT_SHOW_ERROR_DIALOG      = 0x40,  
    RUNTIME_INFO_IGNORE_ERROR_MODE           = 0x1000  
  
} RUNTIME_INFO_FLAGS;  
```  
  
## <a name="members"></a>Elementy członkowskie  
  
|Element członkowski|Opis|  
|------------|-----------------|  
|`RUNTIME_INFO_DONT_RETURN_DIRECTORY`|Wskazuje, czy informacji katalogowych nie powinny być dołączone.|  
|`RUNTIME_INFO_DONT_RETURN_VERSION`|Wskazuje, że informacje o wersji nie powinny być dołączone.|  
|`RUNTIME_INFO_DONT_SHOW_ERROR_DIALOG`|Wskazuje, że nie można wyświetlić okno dialogowe błędu w przypadku awarii.|  
|`RUNTIME_INFO_IGNORE_ERROR_MODE`|Oznacza to, że efekty wywołania metody [SetErrorMode](http://go.microsoft.com/fwlink/p/?LinkId=255242) funkcji przy użyciu flagi parametr SEM_FAILCRITICALERRORS powinna zostać zastąpiona. Oznacza to, że okno dialogowe instalacji powinny być wyświetlane w przypadku awarii, a nie są pomijane.|  
|`RUNTIME_INFO_REQUEST_AMD64`|Wskazuje żądanie informacji o wersji 64-zgodnej AMD środowiska uruchomieniowego.|  
|`RUNTIME_INFO_REQUEST_IA64`|Wskazuje żądanie informacji o wersji IA-64-compatible środowiska wykonawczego.|  
|`RUNTIME_INFO_REQUEST_X86`|Wskazuje żądanie informacji o x86 wersji zgodnej z funkcją środowiska uruchomieniowego.|  
|`RUNTIME_INFO_UPGRADE_VERSION`|Wskazuje, że informacje o uaktualnianiu wersji powinny być dołączone.|  
  
## <a name="remarks"></a>Uwagi  
 Następujące flagi architektura platformy, może być określony tylko jeden w czasie i nie można łączyć:  
  
-   RUNTIME_INFO_REQUEST_IA64  
  
-   RUNTIME_INFO_REQUEST_AMD64  
  
-   RUNTIME_INFO_REQUEST_X86  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** MSCorEE.h  
  
 **Biblioteka:** biblioteki MSCorEE.dll  
  
 **Wersje programu .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Zobacz też  
 [Hosting — wyliczenia](../../../../docs/framework/unmanaged-api/hosting/hosting-enumerations.md)
