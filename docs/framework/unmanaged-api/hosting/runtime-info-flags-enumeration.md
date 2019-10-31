---
title: RUNTIME_INFO_FLAGS — Wyliczenie
ms.date: 03/30/2017
api_name:
- RUNTIME_INFO_FLAGS
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- RUNTIME_INFO_FLAGS
helpviewer_keywords:
- RUNTIME_INFO_FLAGS enumeration [.NET Framework hosting]
ms.assetid: adba37be-f775-4cdb-8919-5746ce694f33
topic_type:
- apiref
ms.openlocfilehash: 80643187045e7e96b9c18169c5e71287713d711f
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73106234"
---
# <a name="runtime_info_flags-enumeration"></a>RUNTIME_INFO_FLAGS — Wyliczenie
Zawiera wartości wskazujące, które informacje o środowisku uruchomieniowym języka wspólnego (CLR) powinny zostać zwrócone.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
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
|`RUNTIME_INFO_DONT_RETURN_DIRECTORY`|Wskazuje, że informacje o katalogu nie powinny być uwzględniane.|  
|`RUNTIME_INFO_DONT_RETURN_VERSION`|Wskazuje, że informacja o wersji nie powinna być uwzględniona.|  
|`RUNTIME_INFO_DONT_SHOW_ERROR_DIALOG`|Wskazuje, że w przypadku błędu nie powinno być wyświetlane okno dialogowe błędu.|  
|`RUNTIME_INFO_IGNORE_ERROR_MODE`|Wskazuje, że efekty wywołania funkcji [SetErrorMode](https://go.microsoft.com/fwlink/p/?LinkId=255242) z flagą SEM_FAILCRITICALERRORS powinny zostać zastąpione. Oznacza to, że w przypadku awarii zamiast pomijania należy wyświetlić okno dialogowe instalacji.|  
|`RUNTIME_INFO_REQUEST_AMD64`|Wskazuje żądanie informacji o wersji środowiska uruchomieniowego zgodnej z AMD-64.|  
|`RUNTIME_INFO_REQUEST_IA64`|Wskazuje żądanie informacji o wersji środowiska uruchomieniowego zgodnej z systemem IA-64.|  
|`RUNTIME_INFO_REQUEST_X86`|Wskazuje żądanie informacji o wersji środowiska uruchomieniowego zgodnej z architekturą x86.|  
|`RUNTIME_INFO_UPGRADE_VERSION`|Wskazuje, że należy uwzględnić informacje o uaktualnianiu wersji.|  
  
## <a name="remarks"></a>Uwagi  
 Poniższe flagi architektury platformy można określić tylko po jednej naraz i nie można ich łączyć:  
  
- RUNTIME_INFO_REQUEST_IA64  
  
- RUNTIME_INFO_REQUEST_AMD64  
  
- RUNTIME_INFO_REQUEST_X86  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** MSCorEE. h  
  
 **Biblioteka:** MSCorEE. dll  
  
 **Wersje .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [Hosting — wyliczenia](../../../../docs/framework/unmanaged-api/hosting/hosting-enumerations.md)
