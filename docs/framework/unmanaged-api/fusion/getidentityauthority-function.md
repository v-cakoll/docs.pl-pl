---
title: GetIdentityAuthority — Funkcja
ms.date: 03/30/2017
api_name:
- GetIdentityAuthority
api_location:
- fusion.dll
- clr.dll
api_type:
- COM
f1_keywords:
- GetIdentityAuthority
helpviewer_keywords:
- GetIdentityAuthority function [.NET Framework fusion]
ms.assetid: 843cd5ab-d2b7-4ff6-86bd-e68c7a91c098
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 3090887d3c670b2784b7b40c7d63832715596c3b
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59141521"
---
# <a name="getidentityauthority-function"></a>GetIdentityAuthority — Funkcja
Pobiera wskaźnik do [iidentityauthority —](../../../../docs/framework/unmanaged-api/fusion/iidentityauthority-interface.md) wystąpienie, które zarządza kluczami obiektów kodu.  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT GetIdentityAuthority (  
    [out] IIdentityAuthority   **ppIIdentityAuthority  
 );  
```  
  
## <a name="parameters"></a>Parametry  
 `ppIIdentityAuthority`  
 [out] Zwrócony `IIdentityAuthority` wskaźnika.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** Isolation.h  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [IIdentityAuthority, interfejs](../../../../docs/framework/unmanaged-api/fusion/iidentityauthority-interface.md)
- [Łączenie statycznych funkcji globalnych](../../../../docs/framework/unmanaged-api/fusion/fusion-global-static-functions.md)
