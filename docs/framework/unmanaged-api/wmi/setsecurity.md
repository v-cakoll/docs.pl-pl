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
ms.openlocfilehash: 6d27779bcfc97e1c4156b8782896e83d4754491b
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73120225"
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
określoną Gdy funkcja zwraca, zawiera wskaźnik do `boolean`, który wskazuje, czy token powinien być resetowany przez wywołanie funkcji [ResetSecurity](resetsecurity.md) .

`token`\
określoną Gdy funkcja zwraca, zawiera wskaźnik do uchwytu tokenu personifikacji skojarzonego z bieżącym wątkiem. Jej wartość może być `null`, jeśli nie ma tokenu skojarzonego z bieżącym wątkiem. 

## <a name="return-value"></a>Wartość zwracana

Jeśli funkcja się powiedzie, wartość zwracana jest `S_OK` (0).

Jeśli funkcja się nie powiedzie, wartość zwracana jest kodem błędu o wartości innej niż zero. Aby uzyskać rozszerzone informacje o błędzie, wywołaj funkcję [GetErrorInfo](geterrorinfo.md) .

## <a name="requirements"></a>Wymagania

 **Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).

 **Nagłówek:** WMINet_Utils. idl

 **Wersje .NET Framework:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]

## <a name="see-also"></a>Zobacz także

- [WMI i liczniki wydajności (niezarządzana dokumentacja interfejsu API)](index.md)
