---
title: CallFunctionShim — Funkcja
ms.date: 03/30/2017
api_name:
- CallFunctionShim
api_location:
- mscoree.dll
api_type:
- DLLExport
f1_keywords:
- CallFunctionShim
helpviewer_keywords:
- CallfunctionShim function [.NET Framework hosting]
ms.assetid: 37118465-ddf3-41f0-bf27-335b72777e63
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 31d93ac427ec67726c9456d623aeb683c9029ccd
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/10/2019
ms.locfileid: "67773763"
---
# <a name="callfunctionshim-function"></a>CallFunctionShim — Funkcja
Wywołuje funkcję, która ma określoną nazwę i parametry w określonej bibliotece.  
  
 Ta funkcja jest przestarzała w programie .NET Framework 4.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT CallFunctionShim (  
    [in] LPCWSTR     szDllName,  
    [in] LPCSTR      szFunctionName,  
    [in] LPVOID      lpvArgument1,  
    [in] LPVOID      lpvArgument2,  
    [in] LPCWSTR     szVersion,  
    [in] LPVOID      pvReserved  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `szDllName`  
 [in] Nazwa biblioteki zawierający funkcję.  
  
 `szFunctionName`  
 [in] Nazwa funkcji.  
  
 `lpvArgument1`  
 [in] Pierwszy argument do przekazania do funkcji.  
  
 `lpvArgument2`  
 [in] Drugi argument do przekazania do funkcji.  
  
 `szVersion`  
 [in] Wersja biblioteki, która zawiera funkcję.  
  
 `pvReserved`  
 [in] Zarezerwowane do użytku w przyszłości. Należy przekazać wartość zero, w tym parametrze.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** MSCorEE.h  
  
 **Biblioteka:** MSCorEE.dll  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [Przestarzałe funkcje hostingu środowiska CLR](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
