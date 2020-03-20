---
title: SetSecurity, funkcja (odwołanie do niezarządzanego interfejsu API)
description: Funkcja SetSecurity pobiera token personifikacji bieżącego wątku.
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
ms.openlocfilehash: 809f6a95fdd6854b3a591b496877838c48d52199
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79176737"
---
# <a name="setsecurity-function"></a>SetSecurity, funkcja

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
[na zewnątrz] Po powrocie funkcja, zawiera `boolean` wskaźnik do, który wskazuje, czy token powinien zostać zresetowany przez wywołanie [ResetSecurity](resetsecurity.md) funkcji.

`token`\
[na zewnątrz] Gdy funkcja zwraca, zawiera wskaźnik do dojścia token personifikacji skojarzone z bieżącym wątku. Jego wartość `null` może być, jeśli nie ma tokenu skojarzone z bieżącego wątku.

## <a name="return-value"></a>Wartość zwracana

Jeśli funkcja powiedzie się, `S_OK` zwracana wartość wynosi (0).

Jeśli funkcja nie powiedzie się, zwracana wartość jest kodem błędu niezerowego. Aby uzyskać rozszerzone informacje o błędzie, należy wywołać funkcję [GetErrorInfo.](geterrorinfo.md)

## <a name="requirements"></a>Wymagania

 **Platformy:** Zobacz [Wymagania systemowe](../../get-started/system-requirements.md).

 **Nagłówek:** WMINet_Utils.idl

 **Wersje programu .NET Framework:**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]

## <a name="see-also"></a>Zobacz też

- [Liczniki wydajności WMI i (niezarządzane odwołanie interfejsu API)](index.md)
