---
title: "CallFunctionShim — Funkcja"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: CallFunctionShim
api_location: mscoree.dll
api_type: DLLExport
f1_keywords: CallFunctionShim
helpviewer_keywords: CallfunctionShim function [.NET Framework hosting]
ms.assetid: 37118465-ddf3-41f0-bf27-335b72777e63
topic_type: apiref
caps.latest.revision: "13"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 0e6e2e237887ff273ba73e2568c84d2aaaa38383
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="callfunctionshim-function"></a>CallFunctionShim — Funkcja
Wykonuje wywołanie funkcji, które ma określoną nazwę i parametrów w określonej bibliotece.  
  
 Ta funkcja jest przestarzała w [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)].  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT CallFunctionShim (  
    [in] LPCWSTR     szDllName,  
    [in] LPCSTR      szFunctionName,  
    [in] LPVOID      lpvArgument1,  
    [in] LPVOID      lpvArgument2,  
    [in] LPCWSTR     szVersion,  
    [in] LPVOID      pvReserved  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `szDllName`  
 [in] Nazwa biblioteki zawierający funkcję.  
  
 `szFunctionName`  
 [in] Nazwa funkcji.  
  
 `lpvArgument1`  
 [in] Pierwszy argument do przekazania do funkcji.  
  
 `lpvArgument2`  
 [in] Drugi argument można przekazać do funkcji.  
  
 `szVersion`  
 [in] Wersja biblioteki, która zawiera funkcję.  
  
 `pvReserved`  
 [in] Zarezerwowane do użytku w przyszłości. Przekaż zero w tym parametrze.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** MSCorEE.h  
  
 **Biblioteka:** biblioteki MSCorEE.dll  
  
 **Wersje programu .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Zobacz też  
 [Przestarzałe funkcje hostingu środowiska CLR.](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
