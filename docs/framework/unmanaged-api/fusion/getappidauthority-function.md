---
title: GetAppIdAuthority — Funkcja
ms.date: 03/30/2017
api_name:
- GetAppIdAuthority
api_location:
- fusion.dll
- clr.dll
api_type:
- COM
f1_keywords:
- GetAppIdAuthority
helpviewer_keywords:
- GetAppIdAuthority function [.NET Framework fusion]
ms.assetid: 9f968dad-0d09-47fb-bebc-94c39a0d16ad
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 274b91793cd51348c42661bf12a4e4385e17f630
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61697787"
---
# <a name="getappidauthority-function"></a>GetAppIdAuthority — Funkcja
Pobiera wskaźnik do [iappidauthority —](../../../../docs/framework/unmanaged-api/fusion/iappidauthority-interface.md) wystąpienie, które zarządza kluczami, dokumentacji i tożsamości aplikacji.  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT GetAppIdAuthority (  
    [out] IAppIdAuthority **ppIAppIdAuthority  
 );  
```  
  
## <a name="parameters"></a>Parametry  
 `ppIAppIdAuthority`  
 [out] Zwrócony `IAppIdAuthority` wskaźnika.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** Isolation.h  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [IAppIdAuthority, interfejs](../../../../docs/framework/unmanaged-api/fusion/iappidauthority-interface.md)
- [Łączenie statycznych funkcji globalnych](../../../../docs/framework/unmanaged-api/fusion/fusion-global-static-functions.md)
