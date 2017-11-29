---
title: "CorExitProcess — Funkcja"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: CorExitProcess
api_location:
- mscoree.dll
- clr.dll
- mscorwks.dll
- mscoreei.dll
api_type: DLLExport
f1_keywords: CorExitProcess
helpviewer_keywords: CorExitProcess function [.NET Framework hosting]
ms.assetid: a5cab4c6-990e-47f3-8798-cf422b791015
topic_type: apiref
caps.latest.revision: "21"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 75b35631bad5de46d48ed818c6f929f25a5f7e66
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="corexitprocess-function"></a>CorExitProcess — Funkcja
Zamyka bieżący proces niezarządzany.  
  
 Ta funkcja jest przestarzała w [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)]. Użyj [ICLRMetaHost::ExitProcess](../../../../docs/framework/unmanaged-api/hosting/iclrmetahost-exitprocess-method.md) metody zamiast tego.  
  
## <a name="syntax"></a>Składnia  
  
```  
void STDMETHODCALLTYPE CorExitProcess (   
  int  exitCode  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `exitCode`  
 Liczba całkowita określająca kod zakończenia procesu.  
  
## <a name="remarks"></a>Uwagi  
  
> [!NOTE]
>  Począwszy od [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)], `CorExitProcess` opuszcza co uruchomiono środowiska uruchomieniowego w procesie, a nie tylko środowiska uruchomieniowego, które są powiązane starszych interfejsów API.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** MSCorEE.h  
  
 **Biblioteka:** biblioteki MSCorEE.dll  
  
 **Wersje programu .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Zobacz też  
 [Przestarzałe funkcje hostingu środowiska CLR.](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
