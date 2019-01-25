---
title: CorExitProcess — Funkcja
ms.date: 03/30/2017
api_name:
- CorExitProcess
api_location:
- mscoree.dll
- clr.dll
- mscorwks.dll
- mscoreei.dll
api_type:
- DLLExport
f1_keywords:
- CorExitProcess
helpviewer_keywords:
- CorExitProcess function [.NET Framework hosting]
ms.assetid: a5cab4c6-990e-47f3-8798-cf422b791015
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 17143a6cac750e20c1e6ebb7874e10fb64e37edc
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54587492"
---
# <a name="corexitprocess-function"></a>CorExitProcess — Funkcja
Zamyka bieżący proces niezarządzany.  
  
 Ta funkcja jest przestarzała w [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)]. Użyj [iclrmetahost::exitprocess —](../../../../docs/framework/unmanaged-api/hosting/iclrmetahost-exitprocess-method.md) metody zamiast tego.  
  
## <a name="syntax"></a>Składnia  
  
```  
void STDMETHODCALLTYPE CorExitProcess (   
  int  exitCode  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `exitCode`  
 Liczba całkowita, która określa kod zakończenia procesu.  
  
## <a name="remarks"></a>Uwagi  
  
> [!NOTE]
>  Począwszy od [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)], `CorExitProcess` kończy działanie każdej wprowadzenie środowiska uruchomieniowego w procesie, a nie tylko środowiska uruchomieniowego, powiązana starszych interfejsów API.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** MSCorEE.h  
  
 **Biblioteka:** MSCorEE.dll  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także
- [Przestarzałe funkcje hostingu środowiska CLR](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
