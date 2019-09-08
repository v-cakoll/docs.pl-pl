---
title: Setsecurity — funkcja (niezarządzana dokumentacja interfejsu API)
description: Funkcja setsecurity pobiera token personifikacji bieżącego wątku.
ms.date: 11/06/2017
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
ms.openlocfilehash: 94c76213acb66116105d181e9961a33976047ee7
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/07/2019
ms.locfileid: "70798240"
---
# <a name="setsecurity-function"></a>Funkcja setsecurity

Pobiera token personifikacji skojarzony z bieżącym wątkiem. 

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]

## <a name="syntax"></a>Składnia

```cpp
HRESULT SetSecurity (
   [out] boolean* pNeedToReset, 
   [out] HANDLE* pCurrentThreadToken
); 
```

## <a name="parameters"></a>Parametry

`pNeedToReset`\
określoną Gdy funkcja zwraca, zawiera wskaźnik do elementu `boolean` , który wskazuje, czy token powinien być resetowany przez wywołanie funkcji [ResetSecurity](resetsecurity.md) .

`token`\
określoną Gdy funkcja zwraca, zawiera wskaźnik do uchwytu tokenu personifikacji skojarzonego z bieżącym wątkiem. Jej wartość może być `null` , jeśli nie istnieje token skojarzony z bieżącym wątkiem. 

## <a name="return-value"></a>Wartość zwracana

Jeśli funkcja się powiedzie, zwracaną wartością jest `S_OK` (0).

Jeśli funkcja się nie powiedzie, wartość zwracana jest kodem błędu o wartości innej niż zero. Aby uzyskać rozszerzone informacje o błędzie, wywołaj funkcję [GetErrorInfo](geterrorinfo.md) .

## <a name="requirements"></a>Wymagania

 **Poszczególnych** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).

 **Nagłówki** WMINet_Utils.idl

 **.NET Framework wersje:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]

## <a name="see-also"></a>Zobacz także

- [WMI i liczniki wydajności (niezarządzana dokumentacja interfejsu API)](index.md)
