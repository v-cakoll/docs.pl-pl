---
title: Funkcja SetSecurity (niezarządzany wykaz interfejsów API)
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: a2cb71263201c86a93ca0bfbd783f2b8512055e6
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/10/2019
ms.locfileid: "67783117"
---
# <a name="setsecurity-function"></a><span data-ttu-id="99909-103">SetSecurity — funkcja</span><span class="sxs-lookup"><span data-stu-id="99909-103">SetSecurity function</span></span>

<span data-ttu-id="99909-104">Pobiera token personifikacji skojarzone z bieżącym wątkiem.</span><span class="sxs-lookup"><span data-stu-id="99909-104">Retrieves the impersonation token associated with the current thread.</span></span> 

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]

## <a name="syntax"></a><span data-ttu-id="99909-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="99909-105">Syntax</span></span>

```cpp
HRESULT SetSecurity (
   [out] boolean* pNeedToReset, 
   [out] HANDLE* pCurrentThreadToken
); 
```

## <a name="parameters"></a><span data-ttu-id="99909-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="99909-106">Parameters</span></span>

`pNeedToReset`\
<span data-ttu-id="99909-107">[out] Po powrocie z tej funkcji zawiera wskaźnik do `boolean` oznacza to, czy token powinien być resetowany przez wywołanie metody [ResetSecurity](resetsecurity.md) funkcji.</span><span class="sxs-lookup"><span data-stu-id="99909-107">[out] When the function returns, contains a pointer to a `boolean` that indicates whether the token should be reset by calling the [ResetSecurity](resetsecurity.md) function.</span></span>

`token`\
<span data-ttu-id="99909-108">[out] Po powrocie z tej funkcji zawiera wskaźnik do uchwytu token personifikacji skojarzone z bieżącym wątkiem.</span><span class="sxs-lookup"><span data-stu-id="99909-108">[out] When the function returns, contains a pointer to the handle of the impersonation token associated with the current thread.</span></span> <span data-ttu-id="99909-109">Wartość może być `null` czy token nie jest skojarzony z bieżącym wątkiem.</span><span class="sxs-lookup"><span data-stu-id="99909-109">Its value can be `null` if there is no token associated with the current thread.</span></span> 

## <a name="return-value"></a><span data-ttu-id="99909-110">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="99909-110">Return value</span></span>

<span data-ttu-id="99909-111">Jeśli funkcja się powiedzie, wartość zwracana jest `S_OK` (0).</span><span class="sxs-lookup"><span data-stu-id="99909-111">If the function succeeds, the return value is `S_OK` (0).</span></span>

<span data-ttu-id="99909-112">Jeśli funkcja zawiedzie, wartość zwracana jest kod błędu różny od zera.</span><span class="sxs-lookup"><span data-stu-id="99909-112">If the function fails, the return value is a non-zero error code.</span></span> <span data-ttu-id="99909-113">Aby uzyskać rozszerzone informacje o błędzie, należy wywołać [geterrorinfo —](geterrorinfo.md) funkcji.</span><span class="sxs-lookup"><span data-stu-id="99909-113">To get extended error information, call the [GetErrorInfo](geterrorinfo.md) function.</span></span>

## <a name="requirements"></a><span data-ttu-id="99909-114">Wymagania</span><span class="sxs-lookup"><span data-stu-id="99909-114">Requirements</span></span>

 <span data-ttu-id="99909-115">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="99909-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>

 <span data-ttu-id="99909-116">**Nagłówek:** WMINet_Utils.idl</span><span class="sxs-lookup"><span data-stu-id="99909-116">**Header:** WMINet_Utils.idl</span></span>

 <span data-ttu-id="99909-117">**Wersje programu .NET framework:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="99909-117">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="99909-118">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="99909-118">See also</span></span>

- [<span data-ttu-id="99909-119">Usługi WMI i liczniki wydajności (niezarządzany wykaz interfejsów API)</span><span class="sxs-lookup"><span data-stu-id="99909-119">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
