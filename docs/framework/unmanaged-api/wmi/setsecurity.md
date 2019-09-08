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
# <a name="setsecurity-function"></a><span data-ttu-id="15c7b-103">Funkcja setsecurity</span><span class="sxs-lookup"><span data-stu-id="15c7b-103">SetSecurity function</span></span>

<span data-ttu-id="15c7b-104">Pobiera token personifikacji skojarzony z bieżącym wątkiem.</span><span class="sxs-lookup"><span data-stu-id="15c7b-104">Retrieves the impersonation token associated with the current thread.</span></span> 

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]

## <a name="syntax"></a><span data-ttu-id="15c7b-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="15c7b-105">Syntax</span></span>

```cpp
HRESULT SetSecurity (
   [out] boolean* pNeedToReset, 
   [out] HANDLE* pCurrentThreadToken
); 
```

## <a name="parameters"></a><span data-ttu-id="15c7b-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="15c7b-106">Parameters</span></span>

`pNeedToReset`\
<span data-ttu-id="15c7b-107">określoną Gdy funkcja zwraca, zawiera wskaźnik do elementu `boolean` , który wskazuje, czy token powinien być resetowany przez wywołanie funkcji [ResetSecurity](resetsecurity.md) .</span><span class="sxs-lookup"><span data-stu-id="15c7b-107">[out] When the function returns, contains a pointer to a `boolean` that indicates whether the token should be reset by calling the [ResetSecurity](resetsecurity.md) function.</span></span>

`token`\
<span data-ttu-id="15c7b-108">określoną Gdy funkcja zwraca, zawiera wskaźnik do uchwytu tokenu personifikacji skojarzonego z bieżącym wątkiem.</span><span class="sxs-lookup"><span data-stu-id="15c7b-108">[out] When the function returns, contains a pointer to the handle of the impersonation token associated with the current thread.</span></span> <span data-ttu-id="15c7b-109">Jej wartość może być `null` , jeśli nie istnieje token skojarzony z bieżącym wątkiem.</span><span class="sxs-lookup"><span data-stu-id="15c7b-109">Its value can be `null` if there is no token associated with the current thread.</span></span> 

## <a name="return-value"></a><span data-ttu-id="15c7b-110">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="15c7b-110">Return value</span></span>

<span data-ttu-id="15c7b-111">Jeśli funkcja się powiedzie, zwracaną wartością jest `S_OK` (0).</span><span class="sxs-lookup"><span data-stu-id="15c7b-111">If the function succeeds, the return value is `S_OK` (0).</span></span>

<span data-ttu-id="15c7b-112">Jeśli funkcja się nie powiedzie, wartość zwracana jest kodem błędu o wartości innej niż zero.</span><span class="sxs-lookup"><span data-stu-id="15c7b-112">If the function fails, the return value is a non-zero error code.</span></span> <span data-ttu-id="15c7b-113">Aby uzyskać rozszerzone informacje o błędzie, wywołaj funkcję [GetErrorInfo](geterrorinfo.md) .</span><span class="sxs-lookup"><span data-stu-id="15c7b-113">To get extended error information, call the [GetErrorInfo](geterrorinfo.md) function.</span></span>

## <a name="requirements"></a><span data-ttu-id="15c7b-114">Wymagania</span><span class="sxs-lookup"><span data-stu-id="15c7b-114">Requirements</span></span>

 <span data-ttu-id="15c7b-115">**Poszczególnych** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="15c7b-115">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>

 <span data-ttu-id="15c7b-116">**Nagłówki** WMINet_Utils.idl</span><span class="sxs-lookup"><span data-stu-id="15c7b-116">**Header:** WMINet_Utils.idl</span></span>

 <span data-ttu-id="15c7b-117">**.NET Framework wersje:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="15c7b-117">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="15c7b-118">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="15c7b-118">See also</span></span>

- [<span data-ttu-id="15c7b-119">WMI i liczniki wydajności (niezarządzana dokumentacja interfejsu API)</span><span class="sxs-lookup"><span data-stu-id="15c7b-119">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
