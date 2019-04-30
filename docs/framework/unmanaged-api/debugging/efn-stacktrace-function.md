---
title: _EFN_StackTrace — Funkcja
ms.date: 03/30/2017
api_name:
- _EFN_StackTrace
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- _EFN_StackTrace
helpviewer_keywords:
- _EFN_StackTrace function [.NET Framework debugging]
ms.assetid: caea7754-867c-4360-a65c-5ced4408fd9d
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: dfbdbb389f9945ffeea649bcddd45bee8caf2496
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61698320"
---
# <a name="efnstacktrace-function"></a><span data-ttu-id="fcf86-102">_EFN_StackTrace — Funkcja</span><span class="sxs-lookup"><span data-stu-id="fcf86-102">_EFN_StackTrace Function</span></span>
<span data-ttu-id="fcf86-103">Zawiera tekst reprezentujący śledzenia stosu z zarządzanego i tablicę `CONTEXT` rejestruje, jeden dla każdego przejścia między niezarządzane, a kod zarządzany.</span><span class="sxs-lookup"><span data-stu-id="fcf86-103">Provides a text representation of a managed stack trace and an array of `CONTEXT` records, one for each transition between unmanaged and managed code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fcf86-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="fcf86-104">Syntax</span></span>  
  
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
  
## <a name="parameters"></a><span data-ttu-id="fcf86-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="fcf86-105">Parameters</span></span>  
 `Client`  
 <span data-ttu-id="fcf86-106">[in] Klient debugowane.</span><span class="sxs-lookup"><span data-stu-id="fcf86-106">[in] The client being debugged.</span></span>  
  
 `wszTextOut`  
 <span data-ttu-id="fcf86-107">[out] Tekstowa reprezentacja ślad stosu.</span><span class="sxs-lookup"><span data-stu-id="fcf86-107">[out] The text representation of the stack trace.</span></span>  
  
 `puiTextLength`  
 <span data-ttu-id="fcf86-108">[out] Wskaźnik do liczby znaków `wszTextOut`.</span><span class="sxs-lookup"><span data-stu-id="fcf86-108">[out] A pointer to the number of characters in `wszTextOut`.</span></span>  
  
 `pTransitionContexts`  
 <span data-ttu-id="fcf86-109">[out] Tablica kontekstów przejścia.</span><span class="sxs-lookup"><span data-stu-id="fcf86-109">[out] The array of transition contexts.</span></span>  
  
 `puiTransitionContextCount`  
 <span data-ttu-id="fcf86-110">[out] Wskaźnik do liczby kontekstów przejścia w tablicy.</span><span class="sxs-lookup"><span data-stu-id="fcf86-110">[out] A pointer to the number of transition contexts in the array.</span></span>  
  
 `uiSizeOfContext`  
 <span data-ttu-id="fcf86-111">[in] Rozmiar struktury kontekstu.</span><span class="sxs-lookup"><span data-stu-id="fcf86-111">[in] The size of the context structure.</span></span>  
  
 `Flags`  
 <span data-ttu-id="fcf86-112">[in] Ustaw na wartość 0 lub SOS_STACKTRACE_SHOWADDRESSES (0x01) aby wyświetlić rejestr EBP i wskaźnik stosu enter (ESP) przed każdym `module!functionname` wiersza.</span><span class="sxs-lookup"><span data-stu-id="fcf86-112">[in] Set to either 0 or SOS_STACKTRACE_SHOWADDRESSES (0x01) to show the EBP register and the enter stack pointer (ESP) in front of each `module!functionname` line.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="fcf86-113">Uwagi</span><span class="sxs-lookup"><span data-stu-id="fcf86-113">Remarks</span></span>  
 <span data-ttu-id="fcf86-114">`_EFN_StackTrace` Struktury mogą być wywoływane z interfejsu programowego WinDbg.</span><span class="sxs-lookup"><span data-stu-id="fcf86-114">The `_EFN_StackTrace` structure can be called from a WinDbg programmatic interface.</span></span> <span data-ttu-id="fcf86-115">Parametry są używane w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="fcf86-115">Parameters are used as follows:</span></span>  
  
- <span data-ttu-id="fcf86-116">Jeśli `wszTextOut` ma wartość null i `puiTextLength` jest inna niż null, funkcja zwraca długość ciągu w `puiTextLength`.</span><span class="sxs-lookup"><span data-stu-id="fcf86-116">If `wszTextOut` is null and `puiTextLength` is not null, the function returns the string length in `puiTextLength`.</span></span>  
  
- <span data-ttu-id="fcf86-117">Jeśli `wszTextOut` jest inna niż null, funkcja przechowuje tekst w `wszTextOut` do lokalizacji wskazanej przez `puiTextLength`.</span><span class="sxs-lookup"><span data-stu-id="fcf86-117">If `wszTextOut` is not null, the function stores text in `wszTextOut` up to the location indicated by `puiTextLength`.</span></span> <span data-ttu-id="fcf86-118">Zwraca ona pomyślnie, jeśli było wystarczająco dużo miejsca w buforze lub zwraca E_OUTOFMEMORY Jeśli bufor nie jest wystarczająco długie.</span><span class="sxs-lookup"><span data-stu-id="fcf86-118">It returns successfully if there was enough room in the buffer, or returns E_OUTOFMEMORY if the buffer was not long enough.</span></span>  
  
- <span data-ttu-id="fcf86-119">Przejście część funkcji jest ignorowana, jeśli `pTransitionContexts` i `puiTransitionContextCount` mają obie wartość null.</span><span class="sxs-lookup"><span data-stu-id="fcf86-119">The transition portion of the function is ignored if `pTransitionContexts` and `puiTransitionContextCount` are both null.</span></span> <span data-ttu-id="fcf86-120">W takim przypadku funkcja zapewnia wywołań przy użyciu tekstu wyjściowego tylko nazwy funkcji.</span><span class="sxs-lookup"><span data-stu-id="fcf86-120">In this case, the function provides callers with text output of only the function names.</span></span>  
  
- <span data-ttu-id="fcf86-121">Jeśli `pTransitionContexts` ma wartość null i `puiTransitionContextCount` jest inna niż null, funkcja zwraca niezbędne liczba wpisów kontekstu w `puiTransitionContextCount`.</span><span class="sxs-lookup"><span data-stu-id="fcf86-121">If `pTransitionContexts` is null and `puiTransitionContextCount` is not null, the function returns the necessary number of context entries in `puiTransitionContextCount`.</span></span>  
  
- <span data-ttu-id="fcf86-122">Jeśli `pTransitionContexts` jest inna niż null, funkcja traktuje je jako tablicę struktury o długości `puiTransitionContextCount`.</span><span class="sxs-lookup"><span data-stu-id="fcf86-122">If `pTransitionContexts` is not null, the function treats it as an array of structures of length `puiTransitionContextCount`.</span></span> <span data-ttu-id="fcf86-123">Rozmiar struktury jest nadawana przez `uiSizeOfContext`, a musi być rozmiar [SimpleContext](../../../../docs/framework/unmanaged-api/debugging/stacktrace-simplecontext-structure.md) lub `CONTEXT` dla architektury.</span><span class="sxs-lookup"><span data-stu-id="fcf86-123">The structure size is given by `uiSizeOfContext`, and must be the size of [SimpleContext](../../../../docs/framework/unmanaged-api/debugging/stacktrace-simplecontext-structure.md) or `CONTEXT` for the architecture.</span></span>  
  
- <span data-ttu-id="fcf86-124">`wszTextOut` są zapisywane w następującym formacie:</span><span class="sxs-lookup"><span data-stu-id="fcf86-124">`wszTextOut` is written in the following format:</span></span>  
  
    ```  
    "<ModuleName>!<Function Name>[+<offset in hex>]  
    ...  
    (TRANSITION)  
    ..."  
    ```  
  
- <span data-ttu-id="fcf86-125">Jeśli Przesunięcie szesnastkowo 0x0, przesunięcie nie są zapisywane.</span><span class="sxs-lookup"><span data-stu-id="fcf86-125">If the offset in hex is 0x0, no offset is written.</span></span>  
  
- <span data-ttu-id="fcf86-126">Jeśli żaden kod zarządzany w wątku obecnie występuje w kontekście, funkcja zwraca SOS_E_NOMANAGEDCODE.</span><span class="sxs-lookup"><span data-stu-id="fcf86-126">If there is no managed code on the thread currently in context, the function returns SOS_E_NOMANAGEDCODE.</span></span>  
  
- <span data-ttu-id="fcf86-127">`Flags` Parametr jest równa 0 lub SOS_STACKTRACE_SHOWADDRESSES, aby zobaczyć EBP i ESP przed każdym `module!functionname` wiersza.</span><span class="sxs-lookup"><span data-stu-id="fcf86-127">The `Flags` parameter is either 0 or SOS_STACKTRACE_SHOWADDRESSES to see EBP and ESP in front of each `module!functionname` line.</span></span> <span data-ttu-id="fcf86-128">Domyślnie to 0.</span><span class="sxs-lookup"><span data-stu-id="fcf86-128">By default, it is 0.</span></span>  
  
    ```  
    #define SOS_STACKTRACE_SHOWADDRESSES   0x00000001  
    ```  
  
## <a name="requirements"></a><span data-ttu-id="fcf86-129">Wymagania</span><span class="sxs-lookup"><span data-stu-id="fcf86-129">Requirements</span></span>  
 <span data-ttu-id="fcf86-130">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="fcf86-130">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="fcf86-131">**Nagłówek:** SOS_Stacktrace.h</span><span class="sxs-lookup"><span data-stu-id="fcf86-131">**Header:** SOS_Stacktrace.h</span></span>  
  
 <span data-ttu-id="fcf86-132">**Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="fcf86-132">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fcf86-133">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="fcf86-133">See also</span></span>

- [<span data-ttu-id="fcf86-134">Debugowanie statycznych funkcji globalnych</span><span class="sxs-lookup"><span data-stu-id="fcf86-134">Debugging Global Static Functions</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-global-static-functions.md)
