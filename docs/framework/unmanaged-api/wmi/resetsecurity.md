---
title: ResetSecurity — funkcja (niezarządzana dokumentacja interfejsu API)
description: Funkcja ResetSecurity przypisuje token personifikacji do bieżącego wątku.
ms.date: 11/06/2017
api_name:
- ResetSecurity
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- ResetSecurity
helpviewer_keywords:
- ResetSecurity function [.NET WMI and performance counters]
topic_type:
- Reference
ms.openlocfilehash: 95d91eac21e82e55af2f5e9ab181b770832f5ad0
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73120209"
---
# <a name="resetsecurity-function"></a>ResetSecurity, funkcja
Przypisuje podany token personifikacji do bieżącego wątku.   
  
[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT ResetSecurity (
   [in] HANDLE token
); 
```  

## <a name="parameters"></a>Parametry

`token`  
podczas Token personifikacji do skojarzenia z bieżącym wątkiem. Jej wartość może być `null`. 

## <a name="return-value"></a>Wartość zwracana

Jeśli funkcja się powiedzie, wartość zwracana jest `S_OK` (0).

Jeśli funkcja się nie powiedzie, wartość zwracana jest kodem błędu o wartości innej niż zero. Aby uzyskać rozszerzone informacje o błędzie, wywołaj funkcję [GetErrorInfo](geterrorinfo.md) .
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).  
  
 **Nagłówek:** WMINet_Utils. idl  
  
 **Wersje .NET Framework:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]  
  
## <a name="see-also"></a>Zobacz także

- [WMI i liczniki wydajności (niezarządzana dokumentacja interfejsu API)](index.md)
