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
ms.openlocfilehash: b1f96b6285911b12d72ac136127d736b75d44023
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73127389"
---
# <a name="initialize-function"></a><span data-ttu-id="cdd1a-103">Initialize — funkcja</span><span class="sxs-lookup"><span data-stu-id="cdd1a-103">Initialize function</span></span>

<span data-ttu-id="cdd1a-104">Wykonuje inicjalizację WMI.</span><span class="sxs-lookup"><span data-stu-id="cdd1a-104">Performs WMI initialization.</span></span>

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]

## <a name="syntax"></a><span data-ttu-id="cdd1a-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="cdd1a-105">Syntax</span></span>

```cpp
HRESULT Initialize(
   [in] boolean bAllowIManagementObjectQI
);
```

## <a name="parameters"></a><span data-ttu-id="cdd1a-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="cdd1a-106">Parameters</span></span>

`bAllowIManagementObjectQI`

<span data-ttu-id="cdd1a-107">[in] `true`, aby wskazać, że wywołania funkcji QueryInterface w obiektach usługi WMI są dozwolone; `false` w przeciwnym razie.</span><span class="sxs-lookup"><span data-stu-id="cdd1a-107">[in] `true` to indicate that calls to QueryInterface on WMI objects are allowed; `false` otherwise.</span></span>

## <a name="return-value"></a><span data-ttu-id="cdd1a-108">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="cdd1a-108">Return value</span></span>

<span data-ttu-id="cdd1a-109">Funkcja zawsze zwraca `S_OK` (0).</span><span class="sxs-lookup"><span data-stu-id="cdd1a-109">The function always returns `S_OK` (0).</span></span>

## <a name="requirements"></a><span data-ttu-id="cdd1a-110">Wymagania</span><span class="sxs-lookup"><span data-stu-id="cdd1a-110">Requirements</span></span>

<span data-ttu-id="cdd1a-111">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="cdd1a-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>

<span data-ttu-id="cdd1a-112">**Nagłówek:** WMINet_Utils. def</span><span class="sxs-lookup"><span data-stu-id="cdd1a-112">**Header:** WMINet_Utils.def</span></span>

<span data-ttu-id="cdd1a-113">**Wersje .NET Framework:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="cdd1a-113">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="cdd1a-114">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="cdd1a-114">See also</span></span>

- [<span data-ttu-id="cdd1a-115">WMI i liczniki wydajności (niezarządzana dokumentacja interfejsu API)</span><span class="sxs-lookup"><span data-stu-id="cdd1a-115">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
