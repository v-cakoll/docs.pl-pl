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
ms.openlocfilehash: 69288e995ec789091bf089368cd9a60f003df86e
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73122973"
---
# <a name="enumerateclrs-function"></a><span data-ttu-id="be254-102">EnumerateCLRs — Funkcja</span><span class="sxs-lookup"><span data-stu-id="be254-102">EnumerateCLRs Function</span></span>
<span data-ttu-id="be254-103">Zapewnia mechanizm wyliczania CLRs w procesie.</span><span class="sxs-lookup"><span data-stu-id="be254-103">Provides a mechanism for enumerating the CLRs in a process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="be254-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="be254-104">Syntax</span></span>  
  
```cpp  
HRESULT EnumerateCLRs (  
    [in]  DWORD      debuggeePID,  
    [out] HANDLE**   ppHandleArrayOut,  
    [out] LPWSTR**   ppStringArrayOut,  
    [out] DWORD*     pdwArrayLengthOut  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="be254-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="be254-105">Parameters</span></span>  
 `debuggeePID`  
 <span data-ttu-id="be254-106">podczas Identyfikator procesu, z którego jest wyliczany załadowany CLRs.</span><span class="sxs-lookup"><span data-stu-id="be254-106">[in] Process identifier of the process from which loaded CLRs will be enumerated.</span></span>  
  
 `ppHandleArrayOut`  
 <span data-ttu-id="be254-107">określoną Wskaźnik do tablicy zawierającej uchwyty zdarzeń, które są używane do kontynuowania uruchamiania CLR.</span><span class="sxs-lookup"><span data-stu-id="be254-107">[out] Pointer to an array containing event handles that are used to continue a CLR startup.</span></span> <span data-ttu-id="be254-108">Nie ma gwarancji, że każdy uchwyt w tablicy jest prawidłowy.</span><span class="sxs-lookup"><span data-stu-id="be254-108">Each handle in the array is not guaranteed to be valid.</span></span> <span data-ttu-id="be254-109">Jeśli jest prawidłowy, dojście ma być używane jako zdarzenie kontynuacji dla odpowiedniego środowiska uruchomieniowego znajdujące się w tym samym indeksie `ppStringArrayOut`.</span><span class="sxs-lookup"><span data-stu-id="be254-109">If valid, the handle is to be used as the continue-startup event for the corresponding runtime located in the same index of `ppStringArrayOut`.</span></span>  
  
 `ppStringArrayOut`  
 <span data-ttu-id="be254-110">określoną Wskaźnik do tablicy ciągów, które określają pełne ścieżki do CLRs załadowane w procesie.</span><span class="sxs-lookup"><span data-stu-id="be254-110">[out] Pointer to an array of strings that specify full paths to CLRs loaded in the process.</span></span>  
  
 `pdwArrayLengthOut`  
 <span data-ttu-id="be254-111">określoną Wskaźnik do typu DWORD, który zawiera długość równomiernie dopasowane `ppHandleArrayOut` i `pdwArrayLengthOut`.</span><span class="sxs-lookup"><span data-stu-id="be254-111">[out] Pointer to a DWORD that contains the length of the equally sized `ppHandleArrayOut` and `pdwArrayLengthOut`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="be254-112">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="be254-112">Return Value</span></span>  
 <span data-ttu-id="be254-113">S_OK</span><span class="sxs-lookup"><span data-stu-id="be254-113">S_OK</span></span>  
 <span data-ttu-id="be254-114">Liczba CLRs w procesie została pomyślnie określona, a odpowiednie tablice uchwytów i ścieżek zostały prawidłowo wypełnione.</span><span class="sxs-lookup"><span data-stu-id="be254-114">The number of CLRs in the process was successfully determined, and the corresponding handle and path arrays were properly filled.</span></span>  
  
 <span data-ttu-id="be254-115">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="be254-115">E_INVALIDARG</span></span>  
 <span data-ttu-id="be254-116">`ppHandleArrayOut` lub `ppStringArrayOut` ma wartość null lub `pdwArrayLengthOut` ma wartość null.</span><span class="sxs-lookup"><span data-stu-id="be254-116">Either `ppHandleArrayOut` or `ppStringArrayOut` is null, or `pdwArrayLengthOut` is null.</span></span>  
  
 <span data-ttu-id="be254-117">E_OUTOFMEMORY</span><span class="sxs-lookup"><span data-stu-id="be254-117">E_OUTOFMEMORY</span></span>  
 <span data-ttu-id="be254-118">Funkcja nie może przydzielić wystarczającej ilości pamięci dla tablic uchwytu i ścieżki.</span><span class="sxs-lookup"><span data-stu-id="be254-118">The function is unable to allocate enough memory for the handle and path arrays.</span></span>  
  
 <span data-ttu-id="be254-119">E_FAIL (lub inne kody powrotne E_)</span><span class="sxs-lookup"><span data-stu-id="be254-119">E_FAIL (or other E_ return codes)</span></span>  
 <span data-ttu-id="be254-120">Nie można wyliczyć załadowanych CLRs.</span><span class="sxs-lookup"><span data-stu-id="be254-120">Unable to enumerate loaded CLRs.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="be254-121">Uwagi</span><span class="sxs-lookup"><span data-stu-id="be254-121">Remarks</span></span>  
 <span data-ttu-id="be254-122">Dla procesu docelowego, który jest identyfikowany przez `debuggeePID`, funkcja zwraca tablicę ścieżek, `ppStringArrayOut`, aby CLRs załadować w procesie; Tablica dojść do zdarzeń, `ppHandleArrayOut`, która może zawierać zdarzenie kontynuacji uruchamiania dla środowiska CLR w tym samym indeksie; i rozmiar tablic, `pdwArrayLengthOut`, który określa liczbę załadowanych CLRs.</span><span class="sxs-lookup"><span data-stu-id="be254-122">For a target process that is identified by `debuggeePID`, the function returns an array of paths, `ppStringArrayOut`, to CLRs loaded in the process; an array of event handles, `ppHandleArrayOut`, which may contain a continue-startup event for the CLR at the same index; and the size of the arrays, `pdwArrayLengthOut`, which specifies the number of CLRs that are loaded.</span></span>  
  
 <span data-ttu-id="be254-123">W systemie operacyjnym Windows `debuggeePID` mapuje na identyfikator procesu systemu operacyjnego.</span><span class="sxs-lookup"><span data-stu-id="be254-123">On the Windows operating system, `debuggeePID` maps to an OS process identifier.</span></span>  
  
 <span data-ttu-id="be254-124">Pamięć dla `ppHandleArrayOut` i `ppStringArrayOut` są przydzielone przez tę funkcję.</span><span class="sxs-lookup"><span data-stu-id="be254-124">The memory for `ppHandleArrayOut` and `ppStringArrayOut` are allocated by this function.</span></span> <span data-ttu-id="be254-125">Aby zwolnić przydzieloną pamięć, należy wywołać [funkcję CloseCLREnumeration](../../../../docs/framework/unmanaged-api/debugging/closeclrenumeration-function.md).</span><span class="sxs-lookup"><span data-stu-id="be254-125">To free the memory allocated, you must call [CloseCLREnumeration Function](../../../../docs/framework/unmanaged-api/debugging/closeclrenumeration-function.md).</span></span>  
  
 <span data-ttu-id="be254-126">Tę funkcję można wywołać z parametrami tablicy ustawionymi na wartość null, aby można było zwrócić liczbę CLRs w procesie docelowym.</span><span class="sxs-lookup"><span data-stu-id="be254-126">This function can be called with both array parameters set to null in order to return the count of CLRs in the target process.</span></span> <span data-ttu-id="be254-127">Z tego licznika obiekt wywołujący może wnioskować o rozmiar buforu, który zostanie utworzony: `(sizeof(HANDLE) * count) + (sizeof(LPWSTR) * count) + (sizeof(WCHAR*) * count * MAX_PATH)`.</span><span class="sxs-lookup"><span data-stu-id="be254-127">From this count, a caller can infer the size of the buffer that will be created: `(sizeof(HANDLE) * count) + (sizeof(LPWSTR) * count) + (sizeof(WCHAR*) * count * MAX_PATH)`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="be254-128">Wymagania</span><span class="sxs-lookup"><span data-stu-id="be254-128">Requirements</span></span>  
 <span data-ttu-id="be254-129">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="be254-129">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="be254-130">**Nagłówek:** dbgshim. h</span><span class="sxs-lookup"><span data-stu-id="be254-130">**Header:** dbgshim.h</span></span>  
  
 <span data-ttu-id="be254-131">**Biblioteka:** dbgshim. dll</span><span class="sxs-lookup"><span data-stu-id="be254-131">**Library:** dbgshim.dll</span></span>  
  
 <span data-ttu-id="be254-132">**.NET Framework wersje:** 3,5 SP1</span><span class="sxs-lookup"><span data-stu-id="be254-132">**.NET Framework Versions:** 3.5 SP1</span></span>
