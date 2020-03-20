---
title: VerifyClientKey, funkcja (odwołanie do interfejsu API niezarządzanego)
description: VerifyClientKey Funkcja zapewnia klucz klienta ma poprawne zabezpieczenia.
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
ms.openlocfilehash: ebb794240494deb0c831b50e95461ec52017a215
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79176711"
---
# <a name="verifyclientkey-function"></a>VerifyClientKey, funkcja
Zapewnia, że klucz klienta ma odpowiednie zabezpieczenia.  
  
[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
  
## <a name="syntax"></a>Składnia  
  
```cpp  
LONG VerifyClientKey();
```  

## <a name="return-value"></a>Wartość zwracana

Jeśli funkcja powiedzie się, `ERROR_SUCCESS` zwracana wartość wynosi (0).

Jeśli funkcja nie powiedzie się, zwracana wartość jest kodem błędu niezerowego zdefiniowanym w *pliku WinError.h*.

## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [Wymagania systemowe](../../get-started/system-requirements.md).  
  
 **Nagłówek:** WMINet_Utils.def  
  
 **Wersje programu .NET Framework:**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]  
  
## <a name="see-also"></a>Zobacz też

- [Liczniki wydajności WMI i (niezarządzane odwołanie interfejsu API)](index.md)
