---
title: "RunDll32ShimW — Funkcja"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: RunDll32ShimW
api_location: mscoree.dll
api_type: DLLExport
f1_keywords: RunDll32ShimW
helpviewer_keywords: RunDll32ShimW function [.NET Framework hosting]
ms.assetid: 9ea07b57-96e2-44df-8711-8fe6c119087f
topic_type: apiref
caps.latest.revision: "13"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 3effcdfb8e418d638f4023746be1f0646eceb8d7
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="rundll32shimw-function"></a>RunDll32ShimW — Funkcja
Wykonuje określone polecenie.  
  
 Ta funkcja jest przestarzała w [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)].  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT RunDll32ShimW (  
    [in] HWND        hwnd,  
    [in] HINSTANCE   hinst,  
    [in] LPCWSTR     lpszCmdLine,  
    [in] int         nCmdShow  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `hwnd`  
 [in] Dojście do okna, w którym będzie wyświetlana w wynikach polecenia.  
  
 `hinst`  
 [in] Dojście do biblioteki, który zawiera polecenie.  
  
 `lpszCmdLine`  
 [in] Ciąg, który określa polecenie do wykonania.  
  
 `nCmdShow`  
 [in] Liczba całkowita, która określa tryb wyświetlania w oknie danych wyjściowych.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** MSCorEE.h  
  
 **Biblioteka:** biblioteki MSCorEE.dll  
  
 **Wersje programu .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Zobacz też  
 [Przestarzałe funkcje hostingu środowiska CLR.](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
