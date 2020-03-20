---
title: ResetSecurity, funkcja (odwołanie do niezarządzanego interfejsu API)
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
ms.openlocfilehash: ce74494455c6cc7fe382a4ea4ef2ff0c4e98c61b
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79174865"
---
# <a name="resetsecurity-function"></a>ResetSecurity, funkcja
Przypisuje dostarczony token personifikacji do bieżącego wątku.
  
[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT ResetSecurity (
   [in] HANDLE token
);
```  

## <a name="parameters"></a>Parametry

`token`  
[w] Token personifikacji do skojarzenia z bieżącym wątkiem. Jego wartość `null`może być .

## <a name="return-value"></a>Wartość zwracana

Jeśli funkcja powiedzie się, `S_OK` zwracana wartość wynosi (0).

Jeśli funkcja nie powiedzie się, zwracana wartość jest kodem błędu niezerowego. Aby uzyskać rozszerzone informacje o błędzie, należy wywołać funkcję [GetErrorInfo.](geterrorinfo.md)
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [Wymagania systemowe](../../get-started/system-requirements.md).  
  
 **Nagłówek:** WMINet_Utils.idl  
  
 **Wersje programu .NET Framework:**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]  
  
## <a name="see-also"></a>Zobacz też

- [Liczniki wydajności WMI i (niezarządzane odwołanie interfejsu API)](index.md)
