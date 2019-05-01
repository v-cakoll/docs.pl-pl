---
title: Funkcja ResetSecurity (niezarządzany wykaz interfejsów API)
description: Funkcja ResetSecurity przypisuje tokenu personifikacji w bieżącym wątku.
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: e937690c184d810549e8ab11ef1fc2273a45c5f5
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62049248"
---
# <a name="resetsecurity-function"></a>ResetSecurity — funkcja
Przypisuje token personifikacji dostarczony do bieżącego wątku.   
  
[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT ResetSecurity (
   [in] HANDLE token
); 
```  

## <a name="parameters"></a>Parametry

`token`  
[in] Token personifikacji do skojarzenia z bieżącym wątkiem. Wartość może być `null`. 

## <a name="return-value"></a>Wartość zwracana

Jeśli funkcja się powiedzie, wartość zwracana jest `S_OK` (0).

Jeśli funkcja zawiedzie, wartość zwracana jest kod błędu różny od zera. Aby uzyskać rozszerzone informacje o błędzie, należy wywołać [geterrorinfo —](geterrorinfo.md) funkcji.
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** WMINet_Utils.idl  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]  
  
## <a name="see-also"></a>Zobacz także

- [Usługi WMI i liczniki wydajności (niezarządzany wykaz interfejsów API)](index.md)
