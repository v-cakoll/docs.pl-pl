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
- mscorsvr.dll
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
ms.openlocfilehash: 2a28b33f80299ae6fce34f9de66b6f7f1bc70ef6
ms.sourcegitcommit: 155012a8a826ee8ab6aa49b1b3a3b532e7b7d9bd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2019
ms.locfileid: "66490568"
---
# <a name="corexitprocess-function"></a>CorExitProcess — Funkcja
Zamyka bieżący proces niezarządzany.  
  
 Ta funkcja jest przestarzała w programie .NET Framework 4. Użyj [iclrmetahost::exitprocess —](../../../../docs/framework/unmanaged-api/hosting/iclrmetahost-exitprocess-method.md) metody zamiast tego.  
  
## <a name="syntax"></a>Składnia  
  
```  
void STDMETHODCALLTYPE CorExitProcess (   
  int  exitCode  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `exitCode`  
 Liczba całkowita, która określa kod zakończenia procesu.  
  
## <a name="remarks"></a>Uwagi  
  
> [!NOTE]
>  Począwszy od programu .NET Framework 4, `CorExitProcess` kończy działanie każdej wprowadzenie środowiska uruchomieniowego w procesie, a nie tylko środowiska uruchomieniowego, powiązana starszych interfejsów API.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** MSCorEE.h  
  
 **Biblioteka:** MSCorEE.dll  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [Przestarzałe funkcje hostingu środowiska CLR](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
