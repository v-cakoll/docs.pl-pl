---
title: Initialize — funkcja (niezarządzany wykaz interfejsów API)
description: Funkcję inicjowania wykonuje inicjowania usługi WMI.
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
ms.openlocfilehash: 7c71b2b6d6f102d19d30d480ee9bafcac3c204be
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62049300"
---
# <a name="initialize-function"></a><span data-ttu-id="6b431-103">Initialize — funkcja</span><span class="sxs-lookup"><span data-stu-id="6b431-103">Initialize function</span></span>

<span data-ttu-id="6b431-104">Wykonuje inicjowania usługi WMI.</span><span class="sxs-lookup"><span data-stu-id="6b431-104">Performs WMI initialization.</span></span>

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]

## <a name="syntax"></a><span data-ttu-id="6b431-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="6b431-105">Syntax</span></span>

```cpp
HRESULT Initialize(
   [in] boolean bAllowIManagementObjectQI
);
```

## <a name="parameters"></a><span data-ttu-id="6b431-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="6b431-106">Parameters</span></span>

`bAllowIManagementObjectQI`

<span data-ttu-id="6b431-107">[in] `true` do wskazania, że wywołania QueryInterface obiektów WMI są dozwolone `false` inaczej.</span><span class="sxs-lookup"><span data-stu-id="6b431-107">[in] `true` to indicate that calls to QueryInterface on WMI objects are allowed; `false` otherwise.</span></span>

## <a name="return-value"></a><span data-ttu-id="6b431-108">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="6b431-108">Return value</span></span>

<span data-ttu-id="6b431-109">Funkcja zawsze zwraca `S_OK` (0).</span><span class="sxs-lookup"><span data-stu-id="6b431-109">The function always returns `S_OK` (0).</span></span>

## <a name="requirements"></a><span data-ttu-id="6b431-110">Wymagania</span><span class="sxs-lookup"><span data-stu-id="6b431-110">Requirements</span></span>

<span data-ttu-id="6b431-111">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6b431-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>

<span data-ttu-id="6b431-112">**Nagłówek:** WMINet_Utils.def</span><span class="sxs-lookup"><span data-stu-id="6b431-112">**Header:** WMINet_Utils.def</span></span>

<span data-ttu-id="6b431-113">**Wersje programu .NET framework:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="6b431-113">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="6b431-114">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="6b431-114">See also</span></span>

- [<span data-ttu-id="6b431-115">Usługi WMI i liczniki wydajności (niezarządzany wykaz interfejsów API)</span><span class="sxs-lookup"><span data-stu-id="6b431-115">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
