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
# <a name="initialize-function"></a><span data-ttu-id="d0ddf-103">Initialize — funkcja</span><span class="sxs-lookup"><span data-stu-id="d0ddf-103">Initialize function</span></span>

<span data-ttu-id="d0ddf-104">Wykonuje inicjalizację WMI.</span><span class="sxs-lookup"><span data-stu-id="d0ddf-104">Performs WMI initialization.</span></span>

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]

## <a name="syntax"></a><span data-ttu-id="d0ddf-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="d0ddf-105">Syntax</span></span>

```cpp
HRESULT Initialize(
   [in] boolean bAllowIManagementObjectQI
);
```

## <a name="parameters"></a><span data-ttu-id="d0ddf-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="d0ddf-106">Parameters</span></span>

`bAllowIManagementObjectQI`

<span data-ttu-id="d0ddf-107">podczas `true` aby wskazać, że wywołania funkcji QueryInterface w obiektach usługi WMI są dozwolone; `false` w przeciwnym razie.</span><span class="sxs-lookup"><span data-stu-id="d0ddf-107">[in] `true` to indicate that calls to QueryInterface on WMI objects are allowed; `false` otherwise.</span></span>

## <a name="return-value"></a><span data-ttu-id="d0ddf-108">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="d0ddf-108">Return value</span></span>

<span data-ttu-id="d0ddf-109">Funkcja zawsze zwraca wartość `S_OK` (0).</span><span class="sxs-lookup"><span data-stu-id="d0ddf-109">The function always returns `S_OK` (0).</span></span>

## <a name="requirements"></a><span data-ttu-id="d0ddf-110">Wymagania</span><span class="sxs-lookup"><span data-stu-id="d0ddf-110">Requirements</span></span>

<span data-ttu-id="d0ddf-111">**Poszczególnych** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d0ddf-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>

<span data-ttu-id="d0ddf-112">**Nagłówki** WMINet_Utils.def</span><span class="sxs-lookup"><span data-stu-id="d0ddf-112">**Header:** WMINet_Utils.def</span></span>

<span data-ttu-id="d0ddf-113">**.NET Framework wersje:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="d0ddf-113">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="d0ddf-114">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="d0ddf-114">See also</span></span>

- [<span data-ttu-id="d0ddf-115">WMI i liczniki wydajności (niezarządzana dokumentacja interfejsu API)</span><span class="sxs-lookup"><span data-stu-id="d0ddf-115">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
