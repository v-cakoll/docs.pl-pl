---
title: StackOverflowType — Wyliczenie
ms.date: 03/30/2017
api_name:
- StackOverflowType
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- StackOverflowType
helpviewer_keywords:
- StackOverflowType enumeration [.NET Framework hosting]
ms.assetid: dab648ad-972b-479c-b129-b4c1dcbd932e
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 06c9119a2b842a0efcd4af752ba72dbfda03bf13
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54653868"
---
# <a name="stackoverflowtype-enumeration"></a>StackOverflowType — Wyliczenie
Zawiera wartości wskazujące podstawowych przyczyn zdarzenie przepełnienia stosu.  
  
## <a name="syntax"></a>Składnia  
  
```  
typedef enum {  
    SO_Managed,  
    SO_ClrEngine,  
    SO_Other  
} StackOverflowType;  
```  
  
## <a name="members"></a>Elementy członkowskie  
  
|Element członkowski|Opis|  
|------------|-----------------|  
|`SO_ClrEngine`|Przepełnienie stosu zostało spowodowane przez aparat wykonywania.|  
|`SO_Managed`|Przepełnienie stosu zostało spowodowane przez kod zarządzany.|  
|`SO_Other`|Przepełnienie stosu zostało spowodowane przez kod niezarządzany.|  
  
## <a name="remarks"></a>Uwagi  
 Te informacje są przesyłane do hosta za pomocą wywołania [iactiononclrevent::ONEVENT —](../../../../docs/framework/unmanaged-api/hosting/iactiononclrevent-onevent-method.md) metody.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** MSCorEE.h  
  
 **Biblioteka:** MSCorEE.dll  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także
- [Hosting — wyliczenia](../../../../docs/framework/unmanaged-api/hosting/hosting-enumerations.md)
