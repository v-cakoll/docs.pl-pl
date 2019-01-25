---
title: HOST_TYPE — Wyliczenie
ms.date: 03/30/2017
api_name:
- HOST_TYPE
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- HOST_TYPE
helpviewer_keywords:
- HOST_TYPE enumeration [.NET Framework hosting]
ms.assetid: 51f848be-84c5-4036-9839-c762c576bbf5
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 6a2db1aea04ae060623bc39a52ed6990f6137f82
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54606453"
---
# <a name="hosttype-enumeration"></a>HOST_TYPE — Wyliczenie
Zawiera wartości, które określają typ hosta, który uruchamia aplikację.  
  
## <a name="syntax"></a>Składnia  
  
```  
typedef enum {  
    HOST_TYPE_DEFAULT     = 0x0,  
    HOST_TYPE_APPLAUNCH   = 0x1,  
    HOST_TYPE_CORFLAG     = 0x2  
} HOST_TYPE;  
```  
  
## <a name="members"></a>Elementy członkowskie  
  
|Element członkowski|Opis|  
|------------|-----------------|  
|`HOST_TYPE_APPLAUNCH`|Uruchom aplikację z AppLaunch.exe.<br /><br /> Użyj tej wartości dla częściowo zaufanych aplikacji.|  
|`HOST_TYPE_CORFLAG`|Uruchom aplikację bezpośrednio. Oznacza to uruchom aplikację w jej własnym pliku .exe.<br /><br /> Ta wartość służy do w pełni zaufane aplikacje.|  
|`HOST_TYPE_DEFAULT`|Taka sama jak HOST_TYPE_APPLAUNCH.|  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** MSCorEE.h  
  
 **Biblioteka:** MSCorEE.dll  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także
- [Hosting — wyliczenia](../../../../docs/framework/unmanaged-api/hosting/hosting-enumerations.md)
