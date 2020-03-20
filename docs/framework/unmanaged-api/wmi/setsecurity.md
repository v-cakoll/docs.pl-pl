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
# <a name="setsecurity-function"></a><span data-ttu-id="36498-103">SetSecurity, funkcja</span><span class="sxs-lookup"><span data-stu-id="36498-103">SetSecurity function</span></span>

<span data-ttu-id="36498-104">Pobiera token personifikacji skojarzony z bieżącym wątkiem.</span><span class="sxs-lookup"><span data-stu-id="36498-104">Retrieves the impersonation token associated with the current thread.</span></span>

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]

## <a name="syntax"></a><span data-ttu-id="36498-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="36498-105">Syntax</span></span>

```cpp
HRESULT SetSecurity (
   [out] boolean* pNeedToReset,
   [out] HANDLE* pCurrentThreadToken
);
```

## <a name="parameters"></a><span data-ttu-id="36498-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="36498-106">Parameters</span></span>

`pNeedToReset`\
<span data-ttu-id="36498-107">[na zewnątrz] Po powrocie funkcja, zawiera `boolean` wskaźnik do, który wskazuje, czy token powinien zostać zresetowany przez wywołanie [ResetSecurity](resetsecurity.md) funkcji.</span><span class="sxs-lookup"><span data-stu-id="36498-107">[out] When the function returns, contains a pointer to a `boolean` that indicates whether the token should be reset by calling the [ResetSecurity](resetsecurity.md) function.</span></span>

`token`\
<span data-ttu-id="36498-108">[na zewnątrz] Gdy funkcja zwraca, zawiera wskaźnik do dojścia token personifikacji skojarzone z bieżącym wątku.</span><span class="sxs-lookup"><span data-stu-id="36498-108">[out] When the function returns, contains a pointer to the handle of the impersonation token associated with the current thread.</span></span> <span data-ttu-id="36498-109">Jego wartość `null` może być, jeśli nie ma tokenu skojarzone z bieżącego wątku.</span><span class="sxs-lookup"><span data-stu-id="36498-109">Its value can be `null` if there is no token associated with the current thread.</span></span>

## <a name="return-value"></a><span data-ttu-id="36498-110">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="36498-110">Return value</span></span>

<span data-ttu-id="36498-111">Jeśli funkcja powiedzie się, `S_OK` zwracana wartość wynosi (0).</span><span class="sxs-lookup"><span data-stu-id="36498-111">If the function succeeds, the return value is `S_OK` (0).</span></span>

<span data-ttu-id="36498-112">Jeśli funkcja nie powiedzie się, zwracana wartość jest kodem błędu niezerowego.</span><span class="sxs-lookup"><span data-stu-id="36498-112">If the function fails, the return value is a non-zero error code.</span></span> <span data-ttu-id="36498-113">Aby uzyskać rozszerzone informacje o błędzie, należy wywołać funkcję [GetErrorInfo.](geterrorinfo.md)</span><span class="sxs-lookup"><span data-stu-id="36498-113">To get extended error information, call the [GetErrorInfo](geterrorinfo.md) function.</span></span>

## <a name="requirements"></a><span data-ttu-id="36498-114">Wymagania</span><span class="sxs-lookup"><span data-stu-id="36498-114">Requirements</span></span>

 <span data-ttu-id="36498-115">**Platformy:** Zobacz [Wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="36498-115">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>

 <span data-ttu-id="36498-116">**Nagłówek:** WMINet_Utils.idl</span><span class="sxs-lookup"><span data-stu-id="36498-116">**Header:** WMINet_Utils.idl</span></span>

 <span data-ttu-id="36498-117">**Wersje programu .NET Framework:**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="36498-117">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="36498-118">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="36498-118">See also</span></span>

- [<span data-ttu-id="36498-119">Liczniki wydajności WMI i (niezarządzane odwołanie interfejsu API)</span><span class="sxs-lookup"><span data-stu-id="36498-119">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
