---
title: VerifyClientKey — funkcja (niezarządzana dokumentacja interfejsu API)
description: Funkcja VerifyClientKey gwarantuje, że klucz klienta ma poprawne zabezpieczenia.
ms.date: 11/06/2017
api_name:
- VerifyClientKey
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- VerifyClientKey
helpviewer_keywords:
- VerifyClientKey function [.NET WMI and performance counters]
topic_type:
- Reference
ms.openlocfilehash: 0a0680651eb192e2798ede00048599c5130e63f1
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73107361"
---
# <a name="verifyclientkey-function"></a>VerifyClientKey, funkcja
Zapewnia, że klucz klienta ma poprawne zabezpieczenia.  
  
[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
  
## <a name="syntax"></a>Składnia  
  
```cpp  
LONG VerifyClientKey(); 
```  

## <a name="return-value"></a>Wartość zwracana

Jeśli funkcja się powiedzie, wartość zwracana jest `ERROR_SUCCESS` (0).

Jeśli funkcja się nie powiedzie, wartość zwracana jest kodem błędu o wartości innej niż zero zdefiniowanym w *Winerror. h*.

## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).  
  
 **Nagłówek:** WMINet_Utils. def  
  
 **Wersje .NET Framework:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]  
  
## <a name="see-also"></a>Zobacz także

- [WMI i liczniki wydajności (niezarządzana dokumentacja interfejsu API)](index.md)
