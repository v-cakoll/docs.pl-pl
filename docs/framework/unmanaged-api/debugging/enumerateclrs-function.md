---
title: EnumerateCLRs — Funkcja
ms.date: 03/30/2017
api_name:
- EnumerateCLRs
api_location:
- dbgshim.dll
api_type:
- COM
f1_keywords:
- EnumerateCLRs
helpviewer_keywords:
- debugging API [Silverlight]
- Silverlight, debugging
- EnumerateCLRs function
ms.assetid: f8d50cb3-ec4f-4529-8fe3-bd61fd28e13c
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: e7532218728aead72186b5156da87db6d3bc0a8c
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/06/2019
ms.locfileid: "57469339"
---
# <a name="enumerateclrs-function"></a><span data-ttu-id="ae667-102">EnumerateCLRs — Funkcja</span><span class="sxs-lookup"><span data-stu-id="ae667-102">EnumerateCLRs Function</span></span>
<span data-ttu-id="ae667-103">Udostępnia mechanizm wyliczania CLRs w procesie.</span><span class="sxs-lookup"><span data-stu-id="ae667-103">Provides a mechanism for enumerating the CLRs in a process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ae667-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="ae667-104">Syntax</span></span>  
  
```  
HRESULT EnumerateCLRs (  
    [in]  DWORD      debuggeePID,  
    [out] HANDLE**   ppHandleArrayOut,  
    [out] LPWSTR**   ppStringArrayOut,  
    [out] DWORD*     pdwArrayLengthOut  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ae667-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="ae667-105">Parameters</span></span>  
 `debuggeePID`  
 <span data-ttu-id="ae667-106">[in] Proces identyfikator procesu, z którego będzie można wyliczyć CLRs załadowane.</span><span class="sxs-lookup"><span data-stu-id="ae667-106">[in] Process identifier of the process from which loaded CLRs will be enumerated.</span></span>  
  
 `ppHandleArrayOut`  
 <span data-ttu-id="ae667-107">[out] Wskaźnik na tablicę zawierającą dojścia zdarzenia, które są używane w dalszym uruchamiania aparatu CLR.</span><span class="sxs-lookup"><span data-stu-id="ae667-107">[out] Pointer to an array containing event handles that are used to continue a CLR startup.</span></span> <span data-ttu-id="ae667-108">Dojście do każdego w tablicy nie jest gwarantowana był prawidłowy.</span><span class="sxs-lookup"><span data-stu-id="ae667-108">Each handle in the array is not guaranteed to be valid.</span></span> <span data-ttu-id="ae667-109">Jeśli prawidłowy, uchwyt ma być używany jako zdarzenie Kontynuuj uruchamiania dla odpowiedniego środowiska uruchomieniowego, znajduje się w tym samym indeksie `ppStringArrayOut`.</span><span class="sxs-lookup"><span data-stu-id="ae667-109">If valid, the handle is to be used as the continue-startup event for the corresponding runtime located in the same index of `ppStringArrayOut`.</span></span>  
  
 `ppStringArrayOut`  
 <span data-ttu-id="ae667-110">[out] Wskaźnik na tablicę ciągów, które określają pełnej ścieżki do CLRs załadowany w procesie.</span><span class="sxs-lookup"><span data-stu-id="ae667-110">[out] Pointer to an array of strings that specify full paths to CLRs loaded in the process.</span></span>  
  
 `pdwArrayLengthOut`  
 <span data-ttu-id="ae667-111">[out] Wskaźnik do typu DWORD, który zawiera długości równej wielkości `ppHandleArrayOut` i `pdwArrayLengthOut`.</span><span class="sxs-lookup"><span data-stu-id="ae667-111">[out] Pointer to a DWORD that contains the length of the equally sized `ppHandleArrayOut` and `pdwArrayLengthOut`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="ae667-112">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="ae667-112">Return Value</span></span>  
 <span data-ttu-id="ae667-113">S_OK</span><span class="sxs-lookup"><span data-stu-id="ae667-113">S_OK</span></span>  
 <span data-ttu-id="ae667-114">CLRs procesu został pomyślnie określana i odpowiednie dojścia i tablice ścieżki zostały prawidłowo wypełnione.</span><span class="sxs-lookup"><span data-stu-id="ae667-114">The number of CLRs in the process was successfully determined, and the corresponding handle and path arrays were properly filled.</span></span>  
  
 <span data-ttu-id="ae667-115">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="ae667-115">E_INVALIDARG</span></span>  
 <span data-ttu-id="ae667-116">Albo `ppHandleArrayOut` lub `ppStringArrayOut` ma wartość null, lub `pdwArrayLengthOut` ma wartość null.</span><span class="sxs-lookup"><span data-stu-id="ae667-116">Either `ppHandleArrayOut` or `ppStringArrayOut` is null, or `pdwArrayLengthOut` is null.</span></span>  
  
 <span data-ttu-id="ae667-117">E_OUTOFMEMORY</span><span class="sxs-lookup"><span data-stu-id="ae667-117">E_OUTOFMEMORY</span></span>  
 <span data-ttu-id="ae667-118">Funkcja nie może przydzielić wystarczającej ilości pamięci dla tablic dojścia i ścieżkę.</span><span class="sxs-lookup"><span data-stu-id="ae667-118">The function is unable to allocate enough memory for the handle and path arrays.</span></span>  
  
 <span data-ttu-id="ae667-119">E_FAIL (lub inne kody powrotne e_)</span><span class="sxs-lookup"><span data-stu-id="ae667-119">E_FAIL (or other E_ return codes)</span></span>  
 <span data-ttu-id="ae667-120">Nie można wyliczyć CLRs załadowane.</span><span class="sxs-lookup"><span data-stu-id="ae667-120">Unable to enumerate loaded CLRs.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ae667-121">Uwagi</span><span class="sxs-lookup"><span data-stu-id="ae667-121">Remarks</span></span>  
 <span data-ttu-id="ae667-122">Dla procesu docelowego, który jest identyfikowany przez `debuggeePID`, funkcja zwraca tablicę ścieżek, `ppStringArrayOut`, CLRs załadowany w procesie; tablicę uchwytów zdarzeń `ppHandleArrayOut`, które mogą zawierać zdarzeń Kontynuuj uruchamiania dla środowiska CLR, w tym samym indeksie; oraz Rozmiar macierzy, `pdwArrayLengthOut`, która określa liczbę CLRs, które są ładowane.</span><span class="sxs-lookup"><span data-stu-id="ae667-122">For a target process that is identified by `debuggeePID`, the function returns an array of paths, `ppStringArrayOut`, to CLRs loaded in the process; an array of event handles, `ppHandleArrayOut`, which may contain a continue-startup event for the CLR at the same index; and the size of the arrays, `pdwArrayLengthOut`, which specifies the number of CLRs that are loaded.</span></span>  
  
 <span data-ttu-id="ae667-123">W systemie operacyjnym Windows `debuggeePID` mapuje do systemu operacyjnego przetworzyć identyfikatora.</span><span class="sxs-lookup"><span data-stu-id="ae667-123">On the Windows operating system, `debuggeePID` maps to an OS process identifier.</span></span>  
  
 <span data-ttu-id="ae667-124">Pamięć `ppHandleArrayOut` i `ppStringArrayOut` są przydzielane przez tę funkcję.</span><span class="sxs-lookup"><span data-stu-id="ae667-124">The memory for `ppHandleArrayOut` and `ppStringArrayOut` are allocated by this function.</span></span> <span data-ttu-id="ae667-125">Aby zwolnić pamięć przydzielona, należy wywołać [CloseCLREnumeration, funkcja](../../../../docs/framework/unmanaged-api/debugging/closeclrenumeration-function.md).</span><span class="sxs-lookup"><span data-stu-id="ae667-125">To free the memory allocated, you must call [CloseCLREnumeration Function](../../../../docs/framework/unmanaged-api/debugging/closeclrenumeration-function.md).</span></span>  
  
 <span data-ttu-id="ae667-126">Ta funkcja może zostać wywołany z oba parametry tablicy ustawiona na wartość null, aby zwrócić liczbę CLRs w procesie docelowym.</span><span class="sxs-lookup"><span data-stu-id="ae667-126">This function can be called with both array parameters set to null in order to return the count of CLRs in the target process.</span></span> <span data-ttu-id="ae667-127">Z tej liczby obiekt wywołujący może wywnioskować rozmiar buforu, który zostanie utworzony: `(sizeof(HANDLE) * count) + (sizeof(LPWSTR) * count) + (sizeof(WCHAR*) * count * MAX_PATH)`.</span><span class="sxs-lookup"><span data-stu-id="ae667-127">From this count, a caller can infer the size of the buffer that will be created: `(sizeof(HANDLE) * count) + (sizeof(LPWSTR) * count) + (sizeof(WCHAR*) * count * MAX_PATH)`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ae667-128">Wymagania</span><span class="sxs-lookup"><span data-stu-id="ae667-128">Requirements</span></span>  
 <span data-ttu-id="ae667-129">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ae667-129">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ae667-130">**Nagłówek:** dbgshim.h</span><span class="sxs-lookup"><span data-stu-id="ae667-130">**Header:** dbgshim.h</span></span>  
  
 <span data-ttu-id="ae667-131">**Biblioteka:** dbgshim.dll</span><span class="sxs-lookup"><span data-stu-id="ae667-131">**Library:** dbgshim.dll</span></span>  
  
 <span data-ttu-id="ae667-132">**Wersje programu .NET framework:** 3.5 z dodatkiem SP1</span><span class="sxs-lookup"><span data-stu-id="ae667-132">**.NET Framework Versions:** 3.5 SP1</span></span>
