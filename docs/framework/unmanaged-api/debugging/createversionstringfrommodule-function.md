---
title: "CreateVersionStringFromModule — Funkcja"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: CreateVersionStringFromModule
api_location: dbgshim.dll
api_type: COM
f1_keywords: CreateVersionStringFromModule
helpviewer_keywords:
- debugging API [Silverlight]
- Silverlight, debugging
- CreateVersionStringFromModule function
ms.assetid: 3d2fe9bd-75ef-4364-84a6-da1e1994ac1a
topic_type: apiref
caps.latest.revision: "4"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 9d7d545256393cfbe37216f0d6db064d5e7cb410
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="createversionstringfrommodule-function"></a><span data-ttu-id="b53e7-102">CreateVersionStringFromModule — Funkcja</span><span class="sxs-lookup"><span data-stu-id="b53e7-102">CreateVersionStringFromModule Function</span></span>
<span data-ttu-id="b53e7-103">Tworzy ciąg wersji ze wspólnego języka środowiska uruchomieniowego (języka wspólnego CLR) ścieżki w procesie docelowym.</span><span class="sxs-lookup"><span data-stu-id="b53e7-103">Creates a version string from a common language runtime (CLR) path in a target process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b53e7-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="b53e7-104">Syntax</span></span>  
  
```  
HRESULT CreateVersionStringFromModule (  
    [in]  DWORD      pidDebuggee,  
    [in]  LPCWSTR    szModuleName,  
    [out, size_is(cchBuffer),  
          length_is(*pdwLength)] LPWSTR Buffer,  
    [in]  DWORD      cchBuffer,  
    [out] DWORD*     pdwLength  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="b53e7-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="b53e7-105">Parameters</span></span>  
 `pidDebuggee`  
 <span data-ttu-id="b53e7-106">[in] Identyfikator procesu, w którym element docelowy CLR został załadowany.</span><span class="sxs-lookup"><span data-stu-id="b53e7-106">[in] Identifier of the process in which the target CLR is loaded.</span></span>  
  
 `szModuleName`  
 <span data-ttu-id="b53e7-107">[in] Pełną lub względną ścieżkę do obiektu docelowego CLR, który jest ładowany w procesie.</span><span class="sxs-lookup"><span data-stu-id="b53e7-107">[in] Full or relative path to the target CLR that is loaded in the process.</span></span>  
  
 `pBuffer`  
 <span data-ttu-id="b53e7-108">[out] Zwróć buforu do przechowywania ciąg wersji dla elementu docelowego CLR.</span><span class="sxs-lookup"><span data-stu-id="b53e7-108">[out] Return buffer for storing the version string for the target CLR.</span></span>  
  
 `cchBuffer`  
 <span data-ttu-id="b53e7-109">[in] Rozmiar `pBuffer`.</span><span class="sxs-lookup"><span data-stu-id="b53e7-109">[in] Size of `pBuffer`.</span></span>  
  
 `pdwLength`  
 <span data-ttu-id="b53e7-110">[out] Długość ciągu wersji zwrócony przez `pBuffer`.</span><span class="sxs-lookup"><span data-stu-id="b53e7-110">[out] Length of the version string returned by `pBuffer`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="b53e7-111">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="b53e7-111">Return Value</span></span>  
 <span data-ttu-id="b53e7-112">S_OK</span><span class="sxs-lookup"><span data-stu-id="b53e7-112">S_OK</span></span>  
 <span data-ttu-id="b53e7-113">Pomyślnie zwrócono ciąg wersji dla elementu docelowego CLR w `pBuffer`.</span><span class="sxs-lookup"><span data-stu-id="b53e7-113">The version string for the target CLR was successfully returned in `pBuffer`.</span></span>  
  
 <span data-ttu-id="b53e7-114">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="b53e7-114">E_INVALIDARG</span></span>  
 <span data-ttu-id="b53e7-115">`szModuleName`jest równa null, lub element `pBuffer` lub `cchBuffer` ma wartość null.</span><span class="sxs-lookup"><span data-stu-id="b53e7-115">`szModuleName` is null, or either `pBuffer` or `cchBuffer` is null.</span></span> <span data-ttu-id="b53e7-116">`pBuffer`i `cchBuffer` muszą być wartość null lub inną niż null.</span><span class="sxs-lookup"><span data-stu-id="b53e7-116">`pBuffer` and `cchBuffer` must both be null or non-null.</span></span>  
  
 <span data-ttu-id="b53e7-117">HRESULT_FROM_WIN32(ERROR_INSUFFICIENT_BUFFER)</span><span class="sxs-lookup"><span data-stu-id="b53e7-117">HRESULT_FROM_WIN32(ERROR_INSUFFICIENT_BUFFER)</span></span>  
 <span data-ttu-id="b53e7-118">`pdwLength`jest większa niż `cchBuffer`.</span><span class="sxs-lookup"><span data-stu-id="b53e7-118">`pdwLength` is greater than `cchBuffer`.</span></span> <span data-ttu-id="b53e7-119">Może to być oczekiwany wynik, jeśli przekazanego wartości null zarówno dla `pBuffer` i `cchBuffer`i rozmiar buforu niezbędne przy użyciu `pdwLength`.</span><span class="sxs-lookup"><span data-stu-id="b53e7-119">This may be an expected result if you have passed null for both `pBuffer` and `cchBuffer`, and queried the necessary buffer size by using `pdwLength`.</span></span>  
  
 <span data-ttu-id="b53e7-120">HRESULT_FROM_WIN32(ERROR_MOD_NOT_FOUND)</span><span class="sxs-lookup"><span data-stu-id="b53e7-120">HRESULT_FROM_WIN32(ERROR_MOD_NOT_FOUND)</span></span>  
 <span data-ttu-id="b53e7-121">`szModuleName`zawiera ścieżkę do prawidłowy CLR w procesie docelowym.</span><span class="sxs-lookup"><span data-stu-id="b53e7-121">`szModuleName` does not contain a path to a valid CLR in the target process.</span></span>  
  
 <span data-ttu-id="b53e7-122">E_FAIL (lub inne kody powrotu E_)</span><span class="sxs-lookup"><span data-stu-id="b53e7-122">E_FAIL (or other E_ return codes)</span></span>  
 <span data-ttu-id="b53e7-123">`pidDebuggee`nie odwołuje się nieprawidłowy procesu lub innych awarii.</span><span class="sxs-lookup"><span data-stu-id="b53e7-123">`pidDebuggee` does not refer to a valid process, or other failure.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="b53e7-124">Uwagi</span><span class="sxs-lookup"><span data-stu-id="b53e7-124">Remarks</span></span>  
 <span data-ttu-id="b53e7-125">Ta funkcja akceptuje proces CLR, który jest identyfikowany przez `pidDebuggee` i ciąg ścieżki, która jest określona przez `szModuleName`.</span><span class="sxs-lookup"><span data-stu-id="b53e7-125">This function accepts a CLR process that is identified by `pidDebuggee` and a string path that is specified by `szModuleName`.</span></span> <span data-ttu-id="b53e7-126">Ciąg wersji jest zwracany w buforze który `pBuffer` wskazuje.</span><span class="sxs-lookup"><span data-stu-id="b53e7-126">The version string is returned in the buffer that `pBuffer` points to.</span></span> <span data-ttu-id="b53e7-127">Ten ciąg jest nieprzezroczysta dla użytkownika funkcji; oznacza to, że jest wewnętrzna znaczenia w sam ciąg wersji.</span><span class="sxs-lookup"><span data-stu-id="b53e7-127">This string is opaque to the function user; that is, there is no intrinsic meaning in the version string itself.</span></span> <span data-ttu-id="b53e7-128">Jest on używany wyłącznie w kontekście tej funkcji i [createdebugginginterfacefromversion — funkcja](../../../../docs/framework/unmanaged-api/debugging/createdebugginginterfacefromversion-function-for-silverlight.md).</span><span class="sxs-lookup"><span data-stu-id="b53e7-128">It is used solely in the context of this function and the [CreateDebuggingInterfaceFromVersion function](../../../../docs/framework/unmanaged-api/debugging/createdebugginginterfacefromversion-function-for-silverlight.md).</span></span>  
  
 <span data-ttu-id="b53e7-129">Ta funkcja powinna być wywoływana dwukrotnie.</span><span class="sxs-lookup"><span data-stu-id="b53e7-129">This function should be called twice.</span></span> <span data-ttu-id="b53e7-130">Podczas wywoływania po raz pierwszy go przekazać wartości null zarówno dla `pBuffer` i `cchBuffer`.</span><span class="sxs-lookup"><span data-stu-id="b53e7-130">When you call it the first time, pass null for both `pBuffer` and `cchBuffer`.</span></span> <span data-ttu-id="b53e7-131">Gdy to zrobisz, rozmiar buforu niezbędne do `pBuffer` zostaną zwrócone w `pdwLength`.</span><span class="sxs-lookup"><span data-stu-id="b53e7-131">When you do this, the size of the buffer necessary for `pBuffer` will be returned in `pdwLength`.</span></span> <span data-ttu-id="b53e7-132">Można następnie wywołaj funkcję po raz drugi i przekaż bufor w `pBuffer` i jego rozmiar w `cchBuffer`.</span><span class="sxs-lookup"><span data-stu-id="b53e7-132">You can then call the function a second time, and pass the buffer in `pBuffer` and its size in `cchBuffer`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b53e7-133">Wymagania</span><span class="sxs-lookup"><span data-stu-id="b53e7-133">Requirements</span></span>  
 <span data-ttu-id="b53e7-134">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b53e7-134">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b53e7-135">**Nagłówek:** dbgshim.h</span><span class="sxs-lookup"><span data-stu-id="b53e7-135">**Header:** dbgshim.h</span></span>  
  
 <span data-ttu-id="b53e7-136">**Biblioteka:** biblioteki dbgshim.dll</span><span class="sxs-lookup"><span data-stu-id="b53e7-136">**Library:** dbgshim.dll</span></span>  
  
 <span data-ttu-id="b53e7-137">**Wersje programu .NET framework:** 3.5 z dodatkiem SP1</span><span class="sxs-lookup"><span data-stu-id="b53e7-137">**.NET Framework Versions:** 3.5 SP1</span></span>
