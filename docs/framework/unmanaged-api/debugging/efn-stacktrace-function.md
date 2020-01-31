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
ms.openlocfilehash: cc5093a5ba0afcccaf960e9b8776f93a061cc2f5
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/28/2020
ms.locfileid: "76785670"
---
# <a name="_efn_stacktrace-function"></a><span data-ttu-id="34e41-102">\_EFN\_funkcja ślad stosu</span><span class="sxs-lookup"><span data-stu-id="34e41-102">\_EFN\_StackTrace Function</span></span>
<span data-ttu-id="34e41-103">Przedstawia tekstową reprezentację zarządzanego śledzenia stosu i tablicę `CONTEXT` rekordów, po jednym dla każdego przejścia między niezarządzanym i zarządzanym kodem.</span><span class="sxs-lookup"><span data-stu-id="34e41-103">Provides a text representation of a managed stack trace and an array of `CONTEXT` records, one for each transition between unmanaged and managed code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="34e41-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="34e41-104">Syntax</span></span>  
  
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
  
## <a name="parameters"></a><span data-ttu-id="34e41-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="34e41-105">Parameters</span></span>  
 `Client`  
 <span data-ttu-id="34e41-106">podczas Debugowany klient.</span><span class="sxs-lookup"><span data-stu-id="34e41-106">[in] The client being debugged.</span></span>  
  
 `wszTextOut`  
 <span data-ttu-id="34e41-107">określoną Tekstowa reprezentacja śladu stosu.</span><span class="sxs-lookup"><span data-stu-id="34e41-107">[out] The text representation of the stack trace.</span></span>  
  
 `puiTextLength`  
 <span data-ttu-id="34e41-108">określoną Wskaźnik do liczby znaków w `wszTextOut`.</span><span class="sxs-lookup"><span data-stu-id="34e41-108">[out] A pointer to the number of characters in `wszTextOut`.</span></span>  
  
 `pTransitionContexts`  
 <span data-ttu-id="34e41-109">określoną Tablica kontekstów przejścia.</span><span class="sxs-lookup"><span data-stu-id="34e41-109">[out] The array of transition contexts.</span></span>  
  
 `puiTransitionContextCount`  
 <span data-ttu-id="34e41-110">określoną Wskaźnik do liczby kontekstów przejścia w tablicy.</span><span class="sxs-lookup"><span data-stu-id="34e41-110">[out] A pointer to the number of transition contexts in the array.</span></span>  
  
 `uiSizeOfContext`  
 <span data-ttu-id="34e41-111">podczas Rozmiar struktury kontekstu.</span><span class="sxs-lookup"><span data-stu-id="34e41-111">[in] The size of the context structure.</span></span>  
  
 `Flags`  
 <span data-ttu-id="34e41-112">podczas Ustaw wartość na 0 lub SOS_STACKTRACE_SHOWADDRESSES (0x01), aby pokazać rejestr EBP oraz wskaźnik wprowadzania stosu (ESP) przed każdą `module!functionname` wierszem.</span><span class="sxs-lookup"><span data-stu-id="34e41-112">[in] Set to either 0 or SOS_STACKTRACE_SHOWADDRESSES (0x01) to show the EBP register and the enter stack pointer (ESP) in front of each `module!functionname` line.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="34e41-113">Uwagi</span><span class="sxs-lookup"><span data-stu-id="34e41-113">Remarks</span></span>  
 <span data-ttu-id="34e41-114">Strukturę `_EFN_StackTrace` można wywołać z interfejsu programistycznego WinDbg.</span><span class="sxs-lookup"><span data-stu-id="34e41-114">The `_EFN_StackTrace` structure can be called from a WinDbg programmatic interface.</span></span> <span data-ttu-id="34e41-115">Parametry są używane w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="34e41-115">Parameters are used as follows:</span></span>  
  
- <span data-ttu-id="34e41-116">Jeśli `wszTextOut` ma wartość null, a `puiTextLength` nie ma wartości null, funkcja zwraca długość ciągu w `puiTextLength`.</span><span class="sxs-lookup"><span data-stu-id="34e41-116">If `wszTextOut` is null and `puiTextLength` is not null, the function returns the string length in `puiTextLength`.</span></span>  
  
- <span data-ttu-id="34e41-117">Jeśli `wszTextOut` nie ma wartości null, funkcja zapisuje tekst w `wszTextOut` do lokalizacji wskazanej przez `puiTextLength`.</span><span class="sxs-lookup"><span data-stu-id="34e41-117">If `wszTextOut` is not null, the function stores text in `wszTextOut` up to the location indicated by `puiTextLength`.</span></span> <span data-ttu-id="34e41-118">Pomyślnie zwraca wartość, jeśli w buforze było wystarczająco dużo miejsca E_OUTOFMEMORY lub jeśli bufor nie był wystarczająco długi.</span><span class="sxs-lookup"><span data-stu-id="34e41-118">It returns successfully if there was enough room in the buffer, or returns E_OUTOFMEMORY if the buffer was not long enough.</span></span>  
  
- <span data-ttu-id="34e41-119">Część przejścia funkcji jest ignorowana, jeśli `pTransitionContexts` i `puiTransitionContextCount` mają wartość null.</span><span class="sxs-lookup"><span data-stu-id="34e41-119">The transition portion of the function is ignored if `pTransitionContexts` and `puiTransitionContextCount` are both null.</span></span> <span data-ttu-id="34e41-120">W takim przypadku funkcja udostępnia obiekty wywołujące z tekstem wyjściowym tylko nazw funkcji.</span><span class="sxs-lookup"><span data-stu-id="34e41-120">In this case, the function provides callers with text output of only the function names.</span></span>  
  
- <span data-ttu-id="34e41-121">Jeśli `pTransitionContexts` ma wartość null, a `puiTransitionContextCount` nie ma wartości null, funkcja zwraca wymaganą liczbę wpisów kontekstu w `puiTransitionContextCount`.</span><span class="sxs-lookup"><span data-stu-id="34e41-121">If `pTransitionContexts` is null and `puiTransitionContextCount` is not null, the function returns the necessary number of context entries in `puiTransitionContextCount`.</span></span>  
  
- <span data-ttu-id="34e41-122">Jeśli `pTransitionContexts` nie ma wartości null, funkcja traktuje ją jako tablicę struktur o długości `puiTransitionContextCount`.</span><span class="sxs-lookup"><span data-stu-id="34e41-122">If `pTransitionContexts` is not null, the function treats it as an array of structures of length `puiTransitionContextCount`.</span></span> <span data-ttu-id="34e41-123">Rozmiar struktury jest określony przez `uiSizeOfContext`i musi być rozmiarem [SimpleContext](stacktrace-simplecontext-structure.md) lub `CONTEXT` dla architektury.</span><span class="sxs-lookup"><span data-stu-id="34e41-123">The structure size is given by `uiSizeOfContext`, and must be the size of [SimpleContext](stacktrace-simplecontext-structure.md) or `CONTEXT` for the architecture.</span></span>  
  
- <span data-ttu-id="34e41-124">`wszTextOut` jest zapisywana w następującym formacie:</span><span class="sxs-lookup"><span data-stu-id="34e41-124">`wszTextOut` is written in the following format:</span></span>  
  
    ```output  
    "<ModuleName>!<Function Name>[+<offset in hex>]  
    ...  
    (TRANSITION)  
    ..."  
    ```  
  
- <span data-ttu-id="34e41-125">Jeśli przesunięcie w postaci szesnastkowej jest 0x0, przesunięcie nie jest zapisywane.</span><span class="sxs-lookup"><span data-stu-id="34e41-125">If the offset in hex is 0x0, no offset is written.</span></span>  
  
- <span data-ttu-id="34e41-126">W przypadku braku kodu zarządzanego w wątku, który jest obecnie w kontekście, funkcja zwraca SOS_E_NOMANAGEDCODE.</span><span class="sxs-lookup"><span data-stu-id="34e41-126">If there is no managed code on the thread currently in context, the function returns SOS_E_NOMANAGEDCODE.</span></span>  
  
- <span data-ttu-id="34e41-127">Parametr `Flags` ma wartość 0 lub SOS_STACKTRACE_SHOWADDRESSES, aby zobaczyć EBP i ESP przed każdym wierszem `module!functionname`.</span><span class="sxs-lookup"><span data-stu-id="34e41-127">The `Flags` parameter is either 0 or SOS_STACKTRACE_SHOWADDRESSES to see EBP and ESP in front of each `module!functionname` line.</span></span> <span data-ttu-id="34e41-128">Domyślnie jest to 0.</span><span class="sxs-lookup"><span data-stu-id="34e41-128">By default, it is 0.</span></span>  
  
    ```cpp  
    #define SOS_STACKTRACE_SHOWADDRESSES   0x00000001  
    ```  
  
## <a name="requirements"></a><span data-ttu-id="34e41-129">Wymagania</span><span class="sxs-lookup"><span data-stu-id="34e41-129">Requirements</span></span>  
 <span data-ttu-id="34e41-130">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="34e41-130">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="34e41-131">**Nagłówek:** SOS_Stacktrace. h</span><span class="sxs-lookup"><span data-stu-id="34e41-131">**Header:** SOS_Stacktrace.h</span></span>  
  
 <span data-ttu-id="34e41-132">**Wersje .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="34e41-132">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="34e41-133">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="34e41-133">See also</span></span>

- [<span data-ttu-id="34e41-134">Debugowanie statycznych funkcji globalnych</span><span class="sxs-lookup"><span data-stu-id="34e41-134">Debugging Global Static Functions</span></span>](debugging-global-static-functions.md)
