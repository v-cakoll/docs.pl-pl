---
title: "Funkcja SetSecurity (niezarządzany wykaz interfejsów API)"
description: "Funkcja SetSecurity pobiera token personifikacji bieżącego wątku."
ms.date: 11/06/2017
ms.prod: .net-framework
ms.technology:
- dotnet-clr
ms.topic: reference
api_name:
- SetSecurity
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- SetSecurity
helpviewer_keywords:
- SetSecurity function [.NET WMI and performance counters]
topic_type:
- Reference
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: abb716d64bde9b298203e54d862ff4f1b2bcd170
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="setsecurity-function"></a>Funkcja SetSecurity
Pobiera token personifikacji skojarzone z bieżącego wątku.   
  
[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT SetSecurity (
   [out] boolean* pNeedToReset, 
   [out] HANDLE* pCurrentThreadToken
); 
```  

## <a name="parameters"></a>Parametry

`pNeedToReset`[out] Po powrocie z funkcji zawiera wskaźnik do `boolean` wskazująca, czy token powinni resetować wywołując [ResetSecurity](resetsecurity.md) funkcji.  

`token`  
[out] Po powrocie z funkcji zawiera wskaźnik do dojścia token personifikacji skojarzone z bieżącego wątku. Wartość może być `null` Jeśli jest nie tokenu skojarzonego z bieżącego wątku. 

## <a name="return-value"></a>Wartość zwracana

Jeśli funkcja zakończy się powodzeniem, jest zwracana wartość `S_OK` (0).

Jeśli funkcja nie powiedzie się, wartość zwracana jest kodu zera błędu. Aby uzyskać rozszerzone informacje o błędzie, należy wywołać [GetErrorInfo](geterrorinfo.md) funkcji.
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** WMINet_Utils.idl  
  
 **Wersje programu .NET framework:**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]  
  
## <a name="see-also"></a>Zobacz także  
[Liczniki wydajności (niezarządzany wykaz interfejsów API) i usługi WMI](index.md)
