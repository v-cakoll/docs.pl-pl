---
title: "Funkcja VerifyClientKey (niezarządzany wykaz interfejsów API)"
description: "Funkcja VerifyClientKey gwarantuje, że klucz klienta ma poprawne zabezpieczeń."
ms.date: 11/06/2017
ms.prod: .net-framework
ms.technology: dotnet-clr
ms.topic: reference
api_name: VerifyClientKey
api_location: WMINet_Utils.dll
api_type: DLLExport
f1_keywords: VerifyClientKey
helpviewer_keywords: VerifyClientKey function [.NET WMI and performance counters]
topic_type: Reference
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: cce10e3dd5536a85b4dee62cc7f6e9e8e73929cb
ms.sourcegitcommit: a53799f81351ad9afb3007cd68846ce6aeeb10cb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/15/2017
---
# <a name="verifyclientkey-function"></a>Funkcja VerifyClientKey
Zapewnia, że klucz klienta ma poprawnych zabezpieczeń.  
  
[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
  
## <a name="syntax"></a>Składnia  
  
```  
LONG VerifyClientKey(); 
```  

## <a name="return-value"></a>Wartość zwracana

Jeśli funkcja zakończy się powodzeniem, jest zwracana wartość `ERROR_SUCCESS` (0).

Jeśli funkcja nie powiedzie się, wartość zwracana jest kodu zera błąd zdefiniowany w *pliku WinError.h*.

## <a name="requirements"></a>Wymagania  
 **Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** WMINet_Utils.def  
  
 **Wersje programu .NET framework:**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]  
  
## <a name="see-also"></a>Zobacz także  
[Liczniki wydajności (niezarządzany wykaz interfejsów API) i usługi WMI](index.md)
