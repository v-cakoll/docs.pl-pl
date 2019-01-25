---
title: Funkcja VerifyClientKey (niezarządzany wykaz interfejsów API)
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
ms.openlocfilehash: 94d601125049f0c215b3b03bf8b13d2959872c3d
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54711762"
---
# <a name="verifyclientkey-function"></a>VerifyClientKey — funkcja
Zapewnia, że klucz klienta ma poprawne zabezpieczeń.  
  
[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
  
## <a name="syntax"></a>Składnia  
  
```  
LONG VerifyClientKey(); 
```  

## <a name="return-value"></a>Wartość zwracana

Jeśli funkcja się powiedzie, wartość zwracana jest `ERROR_SUCCESS` (0).

Jeśli funkcja zawiedzie, wartością zwracaną jest kod błędu różny od zera, zdefiniowany w *WinError.h*.

## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** WMINet_Utils.def  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]  
  
## <a name="see-also"></a>Zobacz także
- [Usługi WMI i liczniki wydajności (niezarządzany wykaz interfejsów API)](index.md)
