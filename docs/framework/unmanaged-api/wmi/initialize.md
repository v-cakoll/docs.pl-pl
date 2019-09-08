---
title: Initialize — funkcja (niezarządzana dokumentacja interfejsu API)
description: Funkcja Initialize wykonuje inicjowanie WMI.
ms.date: 11/06/2017
api_name:
- Initialize
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- Initialize
helpviewer_keywords:
- Initialize function [.NET WMI and performance counters]
topic_type:
- Reference
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 1bc3688b30180bdcde0a87027955a789de749f90
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/07/2019
ms.locfileid: "70798444"
---
# <a name="initialize-function"></a>Initialize — funkcja

Wykonuje inicjalizację WMI.

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]

## <a name="syntax"></a>Składnia

```cpp
HRESULT Initialize(
   [in] boolean bAllowIManagementObjectQI
);
```

## <a name="parameters"></a>Parametry

`bAllowIManagementObjectQI`

podczas `true` aby wskazać, że wywołania funkcji QueryInterface w obiektach usługi WMI są dozwolone; `false` w przeciwnym razie.

## <a name="return-value"></a>Wartość zwracana

Funkcja zawsze zwraca wartość `S_OK` (0).

## <a name="requirements"></a>Wymagania

**Poszczególnych** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).

**Nagłówki** WMINet_Utils.def

**.NET Framework wersje:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]

## <a name="see-also"></a>Zobacz także

- [WMI i liczniki wydajności (niezarządzana dokumentacja interfejsu API)](index.md)
