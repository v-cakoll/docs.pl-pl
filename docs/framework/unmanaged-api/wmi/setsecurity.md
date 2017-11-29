---
title: "Funkcja SetSecurity (niezarządzany wykaz interfejsów API)"
description: "Funkcja SetSecurity pobiera token personifikacji bieżącego wątku."
ms.date: 11/06/2017
ms.prod: .net-framework
ms.technology: dotnet-clr
ms.topic: reference
api_name: SetSecurity
api_location: WMINet_Utils.dll
api_type: DLLExport
f1_keywords: SetSecurity
helpviewer_keywords: SetSecurity function [.NET WMI and performance counters]
topic_type: Reference
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 4fd7ccb0cfb25773da7e489f9ce4d6332b80a616
ms.sourcegitcommit: a53799f81351ad9afb3007cd68846ce6aeeb10cb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/15/2017
---
# <a name="setsecurity-function"></a><span data-ttu-id="352af-103">Funkcja SetSecurity</span><span class="sxs-lookup"><span data-stu-id="352af-103">SetSecurity function</span></span>
<span data-ttu-id="352af-104">Pobiera token personifikacji skojarzone z bieżącego wątku.</span><span class="sxs-lookup"><span data-stu-id="352af-104">Retrieves the impersonation token associated with the current thread.</span></span>   
  
[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
  
## <a name="syntax"></a><span data-ttu-id="352af-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="352af-105">Syntax</span></span>  
  
```  
HRESULT SetSecurity (
   [out] boolean* pNeedToReset, 
   [out] HANDLE* pCurrentThreadToken
); 
```  

## <a name="parameters"></a><span data-ttu-id="352af-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="352af-106">Parameters</span></span>

<span data-ttu-id="352af-107">`pNeedToReset`[out] Po powrocie z funkcji zawiera wskaźnik do `boolean` wskazująca, czy token powinni resetować wywołując [ResetSecurity](resetsecurity.md) funkcji.</span><span class="sxs-lookup"><span data-stu-id="352af-107">`pNeedToReset` [out] When the function returns, contains a pointer to a `boolean` that indicates whether the token should be reset by calling the [ResetSecurity](resetsecurity.md) function.</span></span>  

`token`  
<span data-ttu-id="352af-108">[out] Po powrocie z funkcji zawiera wskaźnik do dojścia token personifikacji skojarzone z bieżącego wątku.</span><span class="sxs-lookup"><span data-stu-id="352af-108">[out] When the function returns, contains a pointer to the handle of the impersonation token associated with the current thread.</span></span> <span data-ttu-id="352af-109">Wartość może być `null` Jeśli jest nie tokenu skojarzonego z bieżącego wątku.</span><span class="sxs-lookup"><span data-stu-id="352af-109">Its value can be `null` if there is no token associated with the current thread.</span></span> 

## <a name="return-value"></a><span data-ttu-id="352af-110">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="352af-110">Return value</span></span>

<span data-ttu-id="352af-111">Jeśli funkcja zakończy się powodzeniem, jest zwracana wartość `S_OK` (0).</span><span class="sxs-lookup"><span data-stu-id="352af-111">If the function succeeds, the return value is `S_OK` (0).</span></span>

<span data-ttu-id="352af-112">Jeśli funkcja nie powiedzie się, wartość zwracana jest kodu zera błędu.</span><span class="sxs-lookup"><span data-stu-id="352af-112">If the function fails, the return value is a non-zero error code.</span></span> <span data-ttu-id="352af-113">Aby uzyskać rozszerzone informacje o błędzie, należy wywołać [GetErrorInfo](geterrorinfo.md) funkcji.</span><span class="sxs-lookup"><span data-stu-id="352af-113">To get extended error information, call the [GetErrorInfo](geterrorinfo.md) function.</span></span>
  
## <a name="requirements"></a><span data-ttu-id="352af-114">Wymagania</span><span class="sxs-lookup"><span data-stu-id="352af-114">Requirements</span></span>  
 <span data-ttu-id="352af-115">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="352af-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="352af-116">**Nagłówek:** WMINet_Utils.idl</span><span class="sxs-lookup"><span data-stu-id="352af-116">**Header:** WMINet_Utils.idl</span></span>  
  
 <span data-ttu-id="352af-117">**Wersje programu .NET framework:**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="352af-117">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="352af-118">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="352af-118">See also</span></span>  
[<span data-ttu-id="352af-119">Liczniki wydajności (niezarządzany wykaz interfejsów API) i usługi WMI</span><span class="sxs-lookup"><span data-stu-id="352af-119">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
