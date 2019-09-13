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
ms.openlocfilehash: 9035d9a53c4b0c8822b79e641aef092b4a48c418
ms.sourcegitcommit: 5ae5a1a9520b8b8b6164ad728d396717f30edafc
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/11/2019
ms.locfileid: "70895035"
---
# <a name="_efn_stacktrace-function"></a><span data-ttu-id="c5bf8-102">\_Funkcja\_EFN ślad stosu</span><span class="sxs-lookup"><span data-stu-id="c5bf8-102">\_EFN\_StackTrace Function</span></span>
<span data-ttu-id="c5bf8-103">Przedstawia tekstową reprezentację zarządzanego śledzenia stosu i tablicę `CONTEXT` rekordów, jeden dla każdego przejścia między niezarządzanym i zarządzanym kodem.</span><span class="sxs-lookup"><span data-stu-id="c5bf8-103">Provides a text representation of a managed stack trace and an array of `CONTEXT` records, one for each transition between unmanaged and managed code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c5bf8-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="c5bf8-104">Syntax</span></span>  
  
```cpp  
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
  
## <a name="parameters"></a><span data-ttu-id="c5bf8-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="c5bf8-105">Parameters</span></span>  
 `Client`  
 <span data-ttu-id="c5bf8-106">podczas Debugowany klient.</span><span class="sxs-lookup"><span data-stu-id="c5bf8-106">[in] The client being debugged.</span></span>  
  
 `wszTextOut`  
 <span data-ttu-id="c5bf8-107">określoną Tekstowa reprezentacja śladu stosu.</span><span class="sxs-lookup"><span data-stu-id="c5bf8-107">[out] The text representation of the stack trace.</span></span>  
  
 `puiTextLength`  
 <span data-ttu-id="c5bf8-108">określoną Wskaźnik do liczby znaków w `wszTextOut`.</span><span class="sxs-lookup"><span data-stu-id="c5bf8-108">[out] A pointer to the number of characters in `wszTextOut`.</span></span>  
  
 `pTransitionContexts`  
 <span data-ttu-id="c5bf8-109">określoną Tablica kontekstów przejścia.</span><span class="sxs-lookup"><span data-stu-id="c5bf8-109">[out] The array of transition contexts.</span></span>  
  
 `puiTransitionContextCount`  
 <span data-ttu-id="c5bf8-110">określoną Wskaźnik do liczby kontekstów przejścia w tablicy.</span><span class="sxs-lookup"><span data-stu-id="c5bf8-110">[out] A pointer to the number of transition contexts in the array.</span></span>  
  
 `uiSizeOfContext`  
 <span data-ttu-id="c5bf8-111">podczas Rozmiar struktury kontekstu.</span><span class="sxs-lookup"><span data-stu-id="c5bf8-111">[in] The size of the context structure.</span></span>  
  
 `Flags`  
 <span data-ttu-id="c5bf8-112">podczas Ustaw wartość 0 lub SOS_STACKTRACE_SHOWADDRESSES (0x01), aby pokazać rejestr EBP i wskaźnik wprowadzania stosu (ESP) przed każdym `module!functionname` wierszem.</span><span class="sxs-lookup"><span data-stu-id="c5bf8-112">[in] Set to either 0 or SOS_STACKTRACE_SHOWADDRESSES (0x01) to show the EBP register and the enter stack pointer (ESP) in front of each `module!functionname` line.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="c5bf8-113">Uwagi</span><span class="sxs-lookup"><span data-stu-id="c5bf8-113">Remarks</span></span>  
 <span data-ttu-id="c5bf8-114">`_EFN_StackTrace` Strukturę można wywołać z interfejsu programistycznego WinDbg.</span><span class="sxs-lookup"><span data-stu-id="c5bf8-114">The `_EFN_StackTrace` structure can be called from a WinDbg programmatic interface.</span></span> <span data-ttu-id="c5bf8-115">Parametry są używane w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="c5bf8-115">Parameters are used as follows:</span></span>  
  
- <span data-ttu-id="c5bf8-116">Jeśli `wszTextOut` ma wartość null `puiTextLength` i nie ma wartości null, funkcja zwraca długość ciągu w `puiTextLength`.</span><span class="sxs-lookup"><span data-stu-id="c5bf8-116">If `wszTextOut` is null and `puiTextLength` is not null, the function returns the string length in `puiTextLength`.</span></span>  
  
- <span data-ttu-id="c5bf8-117">Jeśli `wszTextOut` wartość nie jest równa null, funkcja przechowuje `wszTextOut` tekst w do lokalizacji wskazanej `puiTextLength`przez.</span><span class="sxs-lookup"><span data-stu-id="c5bf8-117">If `wszTextOut` is not null, the function stores text in `wszTextOut` up to the location indicated by `puiTextLength`.</span></span> <span data-ttu-id="c5bf8-118">Pomyślnie zwraca wartość, jeśli w buforze było wystarczająco dużo miejsca lub jeśli bufor nie był wystarczająco długi.</span><span class="sxs-lookup"><span data-stu-id="c5bf8-118">It returns successfully if there was enough room in the buffer, or returns E_OUTOFMEMORY if the buffer was not long enough.</span></span>  
  
- <span data-ttu-id="c5bf8-119">Część przejścia funkcji jest ignorowana, jeśli `pTransitionContexts` i `puiTransitionContextCount` ma wartość null.</span><span class="sxs-lookup"><span data-stu-id="c5bf8-119">The transition portion of the function is ignored if `pTransitionContexts` and `puiTransitionContextCount` are both null.</span></span> <span data-ttu-id="c5bf8-120">W takim przypadku funkcja udostępnia obiekty wywołujące z tekstem wyjściowym tylko nazw funkcji.</span><span class="sxs-lookup"><span data-stu-id="c5bf8-120">In this case, the function provides callers with text output of only the function names.</span></span>  
  
- <span data-ttu-id="c5bf8-121">Jeśli `pTransitionContexts` ma wartość null `puiTransitionContextCount` i nie ma wartości null, funkcja zwraca wymaganą liczbę wpisów kontekstu w `puiTransitionContextCount`.</span><span class="sxs-lookup"><span data-stu-id="c5bf8-121">If `pTransitionContexts` is null and `puiTransitionContextCount` is not null, the function returns the necessary number of context entries in `puiTransitionContextCount`.</span></span>  
  
- <span data-ttu-id="c5bf8-122">Jeśli `pTransitionContexts` wartość nie jest równa null, funkcja traktuje ją jako tablicę struktur `puiTransitionContextCount`długości.</span><span class="sxs-lookup"><span data-stu-id="c5bf8-122">If `pTransitionContexts` is not null, the function treats it as an array of structures of length `puiTransitionContextCount`.</span></span> <span data-ttu-id="c5bf8-123">Rozmiar struktury jest określony przez `uiSizeOfContext`i musi być rozmiarem [SimpleContext](../../../../docs/framework/unmanaged-api/debugging/stacktrace-simplecontext-structure.md) lub `CONTEXT` architekturą.</span><span class="sxs-lookup"><span data-stu-id="c5bf8-123">The structure size is given by `uiSizeOfContext`, and must be the size of [SimpleContext](../../../../docs/framework/unmanaged-api/debugging/stacktrace-simplecontext-structure.md) or `CONTEXT` for the architecture.</span></span>  
  
- <span data-ttu-id="c5bf8-124">`wszTextOut`jest zapisywana w następującym formacie:</span><span class="sxs-lookup"><span data-stu-id="c5bf8-124">`wszTextOut` is written in the following format:</span></span>  
  
    ```output  
    "<ModuleName>!<Function Name>[+<offset in hex>]  
    ...  
    (TRANSITION)  
    ..."  
    ```  
  
- <span data-ttu-id="c5bf8-125">Jeśli przesunięcie w postaci szesnastkowej jest 0x0, przesunięcie nie jest zapisywane.</span><span class="sxs-lookup"><span data-stu-id="c5bf8-125">If the offset in hex is 0x0, no offset is written.</span></span>  
  
- <span data-ttu-id="c5bf8-126">Jeśli w wątku nie ma żadnego kodu zarządzanego, funkcja zwraca SOS_E_NOMANAGEDCODE.</span><span class="sxs-lookup"><span data-stu-id="c5bf8-126">If there is no managed code on the thread currently in context, the function returns SOS_E_NOMANAGEDCODE.</span></span>  
  
- <span data-ttu-id="c5bf8-127">Parametr ma wartość 0 lub SOS_STACKTRACE_SHOWADDRESSES, aby zobaczyć EBP i ESP przed każdym `module!functionname` wierszem. `Flags`</span><span class="sxs-lookup"><span data-stu-id="c5bf8-127">The `Flags` parameter is either 0 or SOS_STACKTRACE_SHOWADDRESSES to see EBP and ESP in front of each `module!functionname` line.</span></span> <span data-ttu-id="c5bf8-128">Domyślnie jest to 0.</span><span class="sxs-lookup"><span data-stu-id="c5bf8-128">By default, it is 0.</span></span>  
  
    ```cpp  
    #define SOS_STACKTRACE_SHOWADDRESSES   0x00000001  
    ```  
  
## <a name="requirements"></a><span data-ttu-id="c5bf8-129">Wymagania</span><span class="sxs-lookup"><span data-stu-id="c5bf8-129">Requirements</span></span>  
 <span data-ttu-id="c5bf8-130">**Poszczególnych** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c5bf8-130">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c5bf8-131">**Nagłówki** SOS_Stacktrace.h</span><span class="sxs-lookup"><span data-stu-id="c5bf8-131">**Header:** SOS_Stacktrace.h</span></span>  
  
 <span data-ttu-id="c5bf8-132">**.NET Framework wersje:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c5bf8-132">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c5bf8-133">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="c5bf8-133">See also</span></span>

- [<span data-ttu-id="c5bf8-134">Debugowanie statycznych funkcji globalnych</span><span class="sxs-lookup"><span data-stu-id="c5bf8-134">Debugging Global Static Functions</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-global-static-functions.md)
