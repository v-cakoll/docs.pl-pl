---
title: CreateVersionStringFromModule — Funkcja
ms.date: 03/30/2017
api_name:
- CreateVersionStringFromModule
api_location:
- dbgshim.dll
api_type:
- COM
f1_keywords:
- CreateVersionStringFromModule
helpviewer_keywords:
- debugging API [Silverlight]
- Silverlight, debugging
- CreateVersionStringFromModule function
ms.assetid: 3d2fe9bd-75ef-4364-84a6-da1e1994ac1a
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: b68624b962ed610dbeecd3e4cead769ab1400f4a
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/10/2019
ms.locfileid: "67739210"
---
# <a name="createversionstringfrommodule-function"></a><span data-ttu-id="46c65-102">CreateVersionStringFromModule — Funkcja</span><span class="sxs-lookup"><span data-stu-id="46c65-102">CreateVersionStringFromModule Function</span></span>
<span data-ttu-id="46c65-103">Tworzy ciąg wersji ze ścieżki środowiska uruchomieniowego (języka wspólnego CLR) języka wspólnego w procesie docelowym.</span><span class="sxs-lookup"><span data-stu-id="46c65-103">Creates a version string from a common language runtime (CLR) path in a target process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="46c65-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="46c65-104">Syntax</span></span>  
  
```cpp  
HRESULT CreateVersionStringFromModule (  
    [in]  DWORD      pidDebuggee,  
    [in]  LPCWSTR    szModuleName,  
    [out, size_is(cchBuffer),  
          length_is(*pdwLength)] LPWSTR Buffer,  
    [in]  DWORD      cchBuffer,  
    [out] DWORD*     pdwLength  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="46c65-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="46c65-105">Parameters</span></span>  
 `pidDebuggee`  
 <span data-ttu-id="46c65-106">[in] Identyfikator procesu, w którym celem CLR jest załadowany.</span><span class="sxs-lookup"><span data-stu-id="46c65-106">[in] Identifier of the process in which the target CLR is loaded.</span></span>  
  
 `szModuleName`  
 <span data-ttu-id="46c65-107">[in] Pełną lub względną ścieżkę do obiektu docelowego CLR, który jest załadowany do procesu.</span><span class="sxs-lookup"><span data-stu-id="46c65-107">[in] Full or relative path to the target CLR that is loaded in the process.</span></span>  
  
 `pBuffer`  
 <span data-ttu-id="46c65-108">[out] Zwraca bufor do przechowywania ciągu wersji dla elementu docelowego CLR.</span><span class="sxs-lookup"><span data-stu-id="46c65-108">[out] Return buffer for storing the version string for the target CLR.</span></span>  
  
 `cchBuffer`  
 <span data-ttu-id="46c65-109">[in] Rozmiar `pBuffer`.</span><span class="sxs-lookup"><span data-stu-id="46c65-109">[in] Size of `pBuffer`.</span></span>  
  
 `pdwLength`  
 <span data-ttu-id="46c65-110">[out] Długość ciągu wersji zwracanego przez `pBuffer`.</span><span class="sxs-lookup"><span data-stu-id="46c65-110">[out] Length of the version string returned by `pBuffer`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="46c65-111">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="46c65-111">Return Value</span></span>  
 <span data-ttu-id="46c65-112">S_OK</span><span class="sxs-lookup"><span data-stu-id="46c65-112">S_OK</span></span>  
 <span data-ttu-id="46c65-113">Ciąg wersji dla elementu docelowego CLR została pomyślnie zwrócona w `pBuffer`.</span><span class="sxs-lookup"><span data-stu-id="46c65-113">The version string for the target CLR was successfully returned in `pBuffer`.</span></span>  
  
 <span data-ttu-id="46c65-114">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="46c65-114">E_INVALIDARG</span></span>  
 <span data-ttu-id="46c65-115">`szModuleName` jest wartością null, lub element `pBuffer` lub `cchBuffer` ma wartość null.</span><span class="sxs-lookup"><span data-stu-id="46c65-115">`szModuleName` is null, or either `pBuffer` or `cchBuffer` is null.</span></span> <span data-ttu-id="46c65-116">`pBuffer` i `cchBuffer` muszą być wartość null lub jest inna niż null.</span><span class="sxs-lookup"><span data-stu-id="46c65-116">`pBuffer` and `cchBuffer` must both be null or non-null.</span></span>  
  
 <span data-ttu-id="46c65-117">HRESULT_FROM_WIN32(ERROR_INSUFFICIENT_BUFFER)</span><span class="sxs-lookup"><span data-stu-id="46c65-117">HRESULT_FROM_WIN32(ERROR_INSUFFICIENT_BUFFER)</span></span>  
 <span data-ttu-id="46c65-118">`pdwLength` jest większa niż `cchBuffer`.</span><span class="sxs-lookup"><span data-stu-id="46c65-118">`pdwLength` is greater than `cchBuffer`.</span></span> <span data-ttu-id="46c65-119">Może to być oczekiwany wynik, jeśli przekazana wartość null dla obu `pBuffer` i `cchBuffer`i sprawdzać rozmiar buforu niezbędne za pomocą `pdwLength`.</span><span class="sxs-lookup"><span data-stu-id="46c65-119">This may be an expected result if you have passed null for both `pBuffer` and `cchBuffer`, and queried the necessary buffer size by using `pdwLength`.</span></span>  
  
 <span data-ttu-id="46c65-120">HRESULT_FROM_WIN32(ERROR_MOD_NOT_FOUND)</span><span class="sxs-lookup"><span data-stu-id="46c65-120">HRESULT_FROM_WIN32(ERROR_MOD_NOT_FOUND)</span></span>  
 <span data-ttu-id="46c65-121">`szModuleName` nie zawiera ścieżki do prawidłowe CLR w procesie docelowym.</span><span class="sxs-lookup"><span data-stu-id="46c65-121">`szModuleName` does not contain a path to a valid CLR in the target process.</span></span>  
  
 <span data-ttu-id="46c65-122">E_FAIL (lub inne kody powrotne e_)</span><span class="sxs-lookup"><span data-stu-id="46c65-122">E_FAIL (or other E_ return codes)</span></span>  
 <span data-ttu-id="46c65-123">`pidDebuggee` Nie można znaleźć prawidłowy proces, lub inna awaria.</span><span class="sxs-lookup"><span data-stu-id="46c65-123">`pidDebuggee` does not refer to a valid process, or other failure.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="46c65-124">Uwagi</span><span class="sxs-lookup"><span data-stu-id="46c65-124">Remarks</span></span>  
 <span data-ttu-id="46c65-125">Ta funkcja akceptuje procesu CLR, która jest identyfikowana przez `pidDebuggee` i ścieżki ciąg, który jest określony przez `szModuleName`.</span><span class="sxs-lookup"><span data-stu-id="46c65-125">This function accepts a CLR process that is identified by `pidDebuggee` and a string path that is specified by `szModuleName`.</span></span> <span data-ttu-id="46c65-126">Ciąg wersji jest zwracany w buforze, `pBuffer` wskazuje.</span><span class="sxs-lookup"><span data-stu-id="46c65-126">The version string is returned in the buffer that `pBuffer` points to.</span></span> <span data-ttu-id="46c65-127">Ten ciąg jest nieprzezroczysta dla użytkownika funkcji; oznacza to nie ma znaczenia wewnętrzne w ciąg wersji.</span><span class="sxs-lookup"><span data-stu-id="46c65-127">This string is opaque to the function user; that is, there is no intrinsic meaning in the version string itself.</span></span> <span data-ttu-id="46c65-128">Jest używana wyłącznie w kontekście tej funkcji i [createdebugginginterfacefromversion — funkcja](../../../../docs/framework/unmanaged-api/debugging/createdebugginginterfacefromversion-function-for-silverlight.md).</span><span class="sxs-lookup"><span data-stu-id="46c65-128">It is used solely in the context of this function and the [CreateDebuggingInterfaceFromVersion function](../../../../docs/framework/unmanaged-api/debugging/createdebugginginterfacefromversion-function-for-silverlight.md).</span></span>  
  
 <span data-ttu-id="46c65-129">Ta funkcja powinna być wywoływana dwa razy.</span><span class="sxs-lookup"><span data-stu-id="46c65-129">This function should be called twice.</span></span> <span data-ttu-id="46c65-130">Gdy wywołujesz ją po raz pierwszy, przekazać wartości null dla obu `pBuffer` i `cchBuffer`.</span><span class="sxs-lookup"><span data-stu-id="46c65-130">When you call it the first time, pass null for both `pBuffer` and `cchBuffer`.</span></span> <span data-ttu-id="46c65-131">Gdy to zrobisz, rozmiar buforu, które są niezbędne do `pBuffer` zostaną zwrócone w `pdwLength`.</span><span class="sxs-lookup"><span data-stu-id="46c65-131">When you do this, the size of the buffer necessary for `pBuffer` will be returned in `pdwLength`.</span></span> <span data-ttu-id="46c65-132">Można następnie wywołać funkcję po raz drugi i przekaż bufor w `pBuffer` i jej rozmiar w `cchBuffer`.</span><span class="sxs-lookup"><span data-stu-id="46c65-132">You can then call the function a second time, and pass the buffer in `pBuffer` and its size in `cchBuffer`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="46c65-133">Wymagania</span><span class="sxs-lookup"><span data-stu-id="46c65-133">Requirements</span></span>  
 <span data-ttu-id="46c65-134">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="46c65-134">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="46c65-135">**Nagłówek:** dbgshim.h</span><span class="sxs-lookup"><span data-stu-id="46c65-135">**Header:** dbgshim.h</span></span>  
  
 <span data-ttu-id="46c65-136">**Biblioteka:** dbgshim.dll</span><span class="sxs-lookup"><span data-stu-id="46c65-136">**Library:** dbgshim.dll</span></span>  
  
 <span data-ttu-id="46c65-137">**Wersje programu .NET framework:** 3.5 z dodatkiem SP1</span><span class="sxs-lookup"><span data-stu-id="46c65-137">**.NET Framework Versions:** 3.5 SP1</span></span>
