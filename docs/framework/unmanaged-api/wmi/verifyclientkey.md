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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: b674e959ab93cf76b84e2af41e875a50b7d115f4
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/07/2019
ms.locfileid: "70798191"
---
# <a name="verifyclientkey-function"></a>VerifyClientKey, funkcja
Zapewnia, że klucz klienta ma poprawne zabezpieczenia.  
  
[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
  
## <a name="syntax"></a>Składnia  
  
```cpp  
LONG VerifyClientKey(); 
```  

## <a name="return-value"></a>Wartość zwracana

Jeśli funkcja się powiedzie, zwracaną wartością jest `ERROR_SUCCESS` (0).

Jeśli funkcja się nie powiedzie, wartość zwracana jest kodem błędu o wartości innej niż zero zdefiniowanym w *Winerror. h*.

## <a name="requirements"></a>Wymagania  
 **Poszczególnych** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).  
  
 **Nagłówki** WMINet_Utils.def  
  
 **.NET Framework wersje:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]  
  
## <a name="see-also"></a>Zobacz także

- [WMI i liczniki wydajności (niezarządzana dokumentacja interfejsu API)](index.md)
