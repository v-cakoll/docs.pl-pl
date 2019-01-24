---
title: FExecuteInAppDomainCallback — Wskaźnik funkcji
ms.date: 03/30/2017
api_name:
- FExecuteInAppDomainCallback
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- FExecuteInAppDomainCallback
helpviewer_keywords:
- FExecuteInAppDomainCallback function pointer [.NET Framework hosting]
ms.assetid: 2709f18f-3eee-497f-bc33-3ab7a485599b
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: e3031ce0eb6f23fdf5e5366d33ff075ea7816b0b
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54649547"
---
# <a name="fexecuteinappdomaincallback-function-pointer"></a>FExecuteInAppDomainCallback — Wskaźnik funkcji
Wskazuje funkcję, która jest wywoływana przez środowisko uruchomieniowe języka wspólnego (CLR) do wykonywania kodu zarządzanego.  
  
 Ten wskaźnik funkcji jest przestarzała w [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)].  
  
## <a name="syntax"></a>Składnia  
  
```  
typedef HRESULT (__stdcall *FExecuteInAppDomainCallback) (  
    [in] void  *cookie  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `cookie`  
 [in] Wskaźnik do nieprzezroczyste pamięci przydzielonej przez obiekt wywołujący, zawierający kod zarządzany do wykonania.  
  
 Alokacji i okresie istnienia tej pamięci są kontrolowane przez obiekt wywołujący (CLR). Nie jest to pamięć sterty zarządzanej CLR.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** MSCorEE.h  
  
 **Biblioteka:** MSCorWks.dll  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także
- [Przestarzałe funkcje hostingu środowiska CLR](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
