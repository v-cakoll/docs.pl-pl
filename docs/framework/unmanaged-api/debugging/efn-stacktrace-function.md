---
title: "_EFN_StackTrace — Funkcja"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: _EFN_StackTrace
api_location: mscordbi.dll
api_type: COM
f1_keywords: _EFN_StackTrace
helpviewer_keywords: _EFN_StackTrace function [.NET Framework debugging]
ms.assetid: caea7754-867c-4360-a65c-5ced4408fd9d
topic_type: apiref
caps.latest.revision: "10"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 031812b2c286c5647afb9c88882f22e2c7c3addf
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="efnstacktrace-function"></a><span data-ttu-id="22306-102">_EFN_StackTrace — Funkcja</span><span class="sxs-lookup"><span data-stu-id="22306-102">_EFN_StackTrace Function</span></span>
<span data-ttu-id="22306-103">Udostępnia reprezentację tekst ślad stosu zarządzanych i tablicę `CONTEXT` rejestruje, jeden dla każdego przejścia między niezarządzanych i kod zarządzany.</span><span class="sxs-lookup"><span data-stu-id="22306-103">Provides a text representation of a managed stack trace and an array of `CONTEXT` records, one for each transition between unmanaged and managed code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="22306-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="22306-104">Syntax</span></span>  
  
```  
HRESULT CALLBACK _EFN_StackTrace(  
    [in]  PDEBUG_CLIENT  Client,  
    [out] WCHAR          wszTextOut[],  
    [out] size_t         *puiTextLength,  
    [out] LPVOID         pTransitionContexts,  
    [out] size_t         *puiTransitionContextCount,  
    [in]  size_t         uiSizeOfContext,  
    [in]  DWORD          Flags  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="22306-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="22306-105">Parameters</span></span>  
 `Client`  
 <span data-ttu-id="22306-106">[in] Klient debugowany.</span><span class="sxs-lookup"><span data-stu-id="22306-106">[in] The client being debugged.</span></span>  
  
 `wszTextOut`  
 <span data-ttu-id="22306-107">[out] Reprezentacja tekstowa typu ślad stosu.</span><span class="sxs-lookup"><span data-stu-id="22306-107">[out] The text representation of the stack trace.</span></span>  
  
 `puiTextLength`  
 <span data-ttu-id="22306-108">[out] Wskaźnik do liczba znaków w `wszTextOut`.</span><span class="sxs-lookup"><span data-stu-id="22306-108">[out] A pointer to the number of characters in `wszTextOut`.</span></span>  
  
 `pTransitionContexts`  
 <span data-ttu-id="22306-109">[out] Tablica kontekstów przejścia.</span><span class="sxs-lookup"><span data-stu-id="22306-109">[out] The array of transition contexts.</span></span>  
  
 `puiTransitionContextCount`  
 <span data-ttu-id="22306-110">[out] Wskaźnik do różnych kontekstach przejścia w tablicy.</span><span class="sxs-lookup"><span data-stu-id="22306-110">[out] A pointer to the number of transition contexts in the array.</span></span>  
  
 `uiSizeOfContext`  
 <span data-ttu-id="22306-111">[in] Rozmiar struktury kontekstu.</span><span class="sxs-lookup"><span data-stu-id="22306-111">[in] The size of the context structure.</span></span>  
  
 `Flags`  
 <span data-ttu-id="22306-112">[in] Wartość 0 lub SOS_STACKTRACE_SHOWADDRESSES (0x01) do wyświetlenia rejestru EBP i wprowadź wskaźnik stosu (ESP) przed każdym `module!functionname` wiersza.</span><span class="sxs-lookup"><span data-stu-id="22306-112">[in] Set to either 0 or SOS_STACKTRACE_SHOWADDRESSES (0x01) to show the EBP register and the enter stack pointer (ESP) in front of each `module!functionname` line.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="22306-113">Uwagi</span><span class="sxs-lookup"><span data-stu-id="22306-113">Remarks</span></span>  
 <span data-ttu-id="22306-114">`_EFN_StackTrace` Struktury może zostać wywołana z interfejsu programowego WinDbg.</span><span class="sxs-lookup"><span data-stu-id="22306-114">The `_EFN_StackTrace` structure can be called from a WinDbg programmatic interface.</span></span> <span data-ttu-id="22306-115">Parametry są używane w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="22306-115">Parameters are used as follows:</span></span>  
  
-   <span data-ttu-id="22306-116">Jeśli `wszTextOut` ma wartość null i `puiTextLength` jest niezerowa, funkcja zwraca długość ciągu w `puiTextLength`.</span><span class="sxs-lookup"><span data-stu-id="22306-116">If `wszTextOut` is null and `puiTextLength` is not null, the function returns the string length in `puiTextLength`.</span></span>  
  
-   <span data-ttu-id="22306-117">Jeśli `wszTextOut` jest niezerowa, funkcja przechowuje tekst w `wszTextOut` do lokalizacji wskazanej przez `puiTextLength`.</span><span class="sxs-lookup"><span data-stu-id="22306-117">If `wszTextOut` is not null, the function stores text in `wszTextOut` up to the location indicated by `puiTextLength`.</span></span> <span data-ttu-id="22306-118">Zwraca go pomyślnie, jeśli było wystarczająco dużo miejsca w buforze lub zwraca E_OUTOFMEMORY Jeśli bufor nie był wystarczająco długi.</span><span class="sxs-lookup"><span data-stu-id="22306-118">It returns successfully if there was enough room in the buffer, or returns E_OUTOFMEMORY if the buffer was not long enough.</span></span>  
  
-   <span data-ttu-id="22306-119">Przejście część funkcji jest ignorowana, jeśli `pTransitionContexts` i `puiTransitionContextCount` są obie wartości null.</span><span class="sxs-lookup"><span data-stu-id="22306-119">The transition portion of the function is ignored if `pTransitionContexts` and `puiTransitionContextCount` are both null.</span></span> <span data-ttu-id="22306-120">W takim przypadku funkcja udostępnia wywołań z tekst wyjściowy tylko nazwy funkcji.</span><span class="sxs-lookup"><span data-stu-id="22306-120">In this case, the function provides callers with text output of only the function names.</span></span>  
  
-   <span data-ttu-id="22306-121">Jeśli `pTransitionContexts` ma wartość null i `puiTransitionContextCount` jest niezerowa, funkcja zwraca niezbędne liczbę wpisów kontekstu w `puiTransitionContextCount`.</span><span class="sxs-lookup"><span data-stu-id="22306-121">If `pTransitionContexts` is null and `puiTransitionContextCount` is not null, the function returns the necessary number of context entries in `puiTransitionContextCount`.</span></span>  
  
-   <span data-ttu-id="22306-122">Jeśli `pTransitionContexts` jest niezerowa, funkcja traktuje ją jako tablica struktury o długości `puiTransitionContextCount`.</span><span class="sxs-lookup"><span data-stu-id="22306-122">If `pTransitionContexts` is not null, the function treats it as an array of structures of length `puiTransitionContextCount`.</span></span> <span data-ttu-id="22306-123">Rozmiar struktury jest określany przez `uiSizeOfContext`, a musi być rozmiar [simplecontext —](../../../../docs/framework/unmanaged-api/debugging/stacktrace-simplecontext-structure.md) lub `CONTEXT` dla architektury.</span><span class="sxs-lookup"><span data-stu-id="22306-123">The structure size is given by `uiSizeOfContext`, and must be the size of [SimpleContext](../../../../docs/framework/unmanaged-api/debugging/stacktrace-simplecontext-structure.md) or `CONTEXT` for the architecture.</span></span>  
  
-   <span data-ttu-id="22306-124">`wszTextOut`są zapisywane w następującym formacie:</span><span class="sxs-lookup"><span data-stu-id="22306-124">`wszTextOut` is written in the following format:</span></span>  
  
    ```  
    "<ModuleName>!<Function Name>[+<offset in hex>]  
    ...  
    (TRANSITION)  
    ..."  
    ```  
  
-   <span data-ttu-id="22306-125">Jeśli Przesunięcie szesnastkowo 0x0, przesunięcie nie są zapisywane.</span><span class="sxs-lookup"><span data-stu-id="22306-125">If the offset in hex is 0x0, no offset is written.</span></span>  
  
-   <span data-ttu-id="22306-126">Jeśli istnieje żadnego kodu zarządzanego w wątku aktualnie w kontekście, funkcja zwraca SOS_E_NOMANAGEDCODE.</span><span class="sxs-lookup"><span data-stu-id="22306-126">If there is no managed code on the thread currently in context, the function returns SOS_E_NOMANAGEDCODE.</span></span>  
  
-   <span data-ttu-id="22306-127">`Flags` Parametr ma wartość 0 lub SOS_STACKTRACE_SHOWADDRESSES, aby wyświetlić EBP i ESP przed każdym `module!functionname` wiersza.</span><span class="sxs-lookup"><span data-stu-id="22306-127">The `Flags` parameter is either 0 or SOS_STACKTRACE_SHOWADDRESSES to see EBP and ESP in front of each `module!functionname` line.</span></span> <span data-ttu-id="22306-128">Domyślnie jest 0.</span><span class="sxs-lookup"><span data-stu-id="22306-128">By default, it is 0.</span></span>  
  
    ```  
    #define SOS_STACKTRACE_SHOWADDRESSES   0x00000001  
    ```  
  
## <a name="requirements"></a><span data-ttu-id="22306-129">Wymagania</span><span class="sxs-lookup"><span data-stu-id="22306-129">Requirements</span></span>  
 <span data-ttu-id="22306-130">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="22306-130">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="22306-131">**Nagłówek:** SOS_Stacktrace.h</span><span class="sxs-lookup"><span data-stu-id="22306-131">**Header:** SOS_Stacktrace.h</span></span>  
  
 <span data-ttu-id="22306-132">**Wersje programu .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="22306-132">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="22306-133">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="22306-133">See Also</span></span>  
 [<span data-ttu-id="22306-134">Statyczne funkcje globalne debugowania</span><span class="sxs-lookup"><span data-stu-id="22306-134">Debugging Global Static Functions</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-global-static-functions.md)
