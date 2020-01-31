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
ms.openlocfilehash: 609d6e47c951aa104cb23084b65e98827a6851f1
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/28/2020
ms.locfileid: "76789180"
---
# <a name="createversionstringfrommodule-function"></a><span data-ttu-id="922d8-102">CreateVersionStringFromModule — Funkcja</span><span class="sxs-lookup"><span data-stu-id="922d8-102">CreateVersionStringFromModule Function</span></span>
<span data-ttu-id="922d8-103">Tworzy ciąg wersji ze ścieżki środowiska uruchomieniowego języka wspólnego (CLR) w procesie docelowym.</span><span class="sxs-lookup"><span data-stu-id="922d8-103">Creates a version string from a common language runtime (CLR) path in a target process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="922d8-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="922d8-104">Syntax</span></span>  
  
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
  
## <a name="parameters"></a><span data-ttu-id="922d8-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="922d8-105">Parameters</span></span>  
 `pidDebuggee`  
 <span data-ttu-id="922d8-106">podczas Identyfikator procesu, w którym jest ładowany docelowe środowisko CLR.</span><span class="sxs-lookup"><span data-stu-id="922d8-106">[in] Identifier of the process in which the target CLR is loaded.</span></span>  
  
 `szModuleName`  
 <span data-ttu-id="922d8-107">podczas Pełna lub względna ścieżka do docelowego środowiska CLR, który jest ładowany w procesie.</span><span class="sxs-lookup"><span data-stu-id="922d8-107">[in] Full or relative path to the target CLR that is loaded in the process.</span></span>  
  
 `pBuffer`  
 <span data-ttu-id="922d8-108">określoną Bufor powrotny do przechowywania ciągu wersji dla docelowego środowiska CLR.</span><span class="sxs-lookup"><span data-stu-id="922d8-108">[out] Return buffer for storing the version string for the target CLR.</span></span>  
  
 `cchBuffer`  
 <span data-ttu-id="922d8-109">podczas Rozmiar `pBuffer`.</span><span class="sxs-lookup"><span data-stu-id="922d8-109">[in] Size of `pBuffer`.</span></span>  
  
 `pdwLength`  
 <span data-ttu-id="922d8-110">określoną Długość ciągu wersji zwracanego przez `pBuffer`.</span><span class="sxs-lookup"><span data-stu-id="922d8-110">[out] Length of the version string returned by `pBuffer`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="922d8-111">Wartość zwrócona</span><span class="sxs-lookup"><span data-stu-id="922d8-111">Return Value</span></span>  
 <span data-ttu-id="922d8-112">S_OK</span><span class="sxs-lookup"><span data-stu-id="922d8-112">S_OK</span></span>  
 <span data-ttu-id="922d8-113">Ciąg wersji docelowego środowiska CLR został pomyślnie zwrócony w `pBuffer`.</span><span class="sxs-lookup"><span data-stu-id="922d8-113">The version string for the target CLR was successfully returned in `pBuffer`.</span></span>  
  
 <span data-ttu-id="922d8-114">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="922d8-114">E_INVALIDARG</span></span>  
 <span data-ttu-id="922d8-115">`szModuleName` ma wartość null lub `pBuffer` lub `cchBuffer` ma wartość null.</span><span class="sxs-lookup"><span data-stu-id="922d8-115">`szModuleName` is null, or either `pBuffer` or `cchBuffer` is null.</span></span> <span data-ttu-id="922d8-116">`pBuffer` i `cchBuffer` muszą mieć wartość null lub być wartością null.</span><span class="sxs-lookup"><span data-stu-id="922d8-116">`pBuffer` and `cchBuffer` must both be null or non-null.</span></span>  
  
 <span data-ttu-id="922d8-117">HRESULT_FROM_WIN32 (ERROR_INSUFFICIENT_BUFFER)</span><span class="sxs-lookup"><span data-stu-id="922d8-117">HRESULT_FROM_WIN32(ERROR_INSUFFICIENT_BUFFER)</span></span>  
 <span data-ttu-id="922d8-118">`pdwLength` jest większa niż `cchBuffer`.</span><span class="sxs-lookup"><span data-stu-id="922d8-118">`pdwLength` is greater than `cchBuffer`.</span></span> <span data-ttu-id="922d8-119">Może to być oczekiwany wynik, jeśli przeszedł wartość null dla obu `pBuffer` i `cchBuffer`i zbadano niezbędny rozmiar buforu przy użyciu `pdwLength`.</span><span class="sxs-lookup"><span data-stu-id="922d8-119">This may be an expected result if you have passed null for both `pBuffer` and `cchBuffer`, and queried the necessary buffer size by using `pdwLength`.</span></span>  
  
 <span data-ttu-id="922d8-120">HRESULT_FROM_WIN32 (ERROR_MOD_NOT_FOUND)</span><span class="sxs-lookup"><span data-stu-id="922d8-120">HRESULT_FROM_WIN32(ERROR_MOD_NOT_FOUND)</span></span>  
 <span data-ttu-id="922d8-121">`szModuleName` nie zawiera ścieżki do prawidłowego środowiska CLR w procesie docelowym.</span><span class="sxs-lookup"><span data-stu-id="922d8-121">`szModuleName` does not contain a path to a valid CLR in the target process.</span></span>  
  
 <span data-ttu-id="922d8-122">E_FAIL (lub inne kody powrotne E_)</span><span class="sxs-lookup"><span data-stu-id="922d8-122">E_FAIL (or other E_ return codes)</span></span>  
 <span data-ttu-id="922d8-123">`pidDebuggee` nie odwołuje się do prawidłowego procesu lub innego błędu.</span><span class="sxs-lookup"><span data-stu-id="922d8-123">`pidDebuggee` does not refer to a valid process, or other failure.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="922d8-124">Uwagi</span><span class="sxs-lookup"><span data-stu-id="922d8-124">Remarks</span></span>  
 <span data-ttu-id="922d8-125">Ta funkcja akceptuje proces CLR identyfikowany przez `pidDebuggee` i ścieżkę ciągu, która jest określona przez `szModuleName`.</span><span class="sxs-lookup"><span data-stu-id="922d8-125">This function accepts a CLR process that is identified by `pidDebuggee` and a string path that is specified by `szModuleName`.</span></span> <span data-ttu-id="922d8-126">Ciąg wersji jest zwracany w buforze, do którego wskazuje `pBuffer`.</span><span class="sxs-lookup"><span data-stu-id="922d8-126">The version string is returned in the buffer that `pBuffer` points to.</span></span> <span data-ttu-id="922d8-127">Ten ciąg jest nieprzezroczysty dla użytkownika funkcji; oznacza to, że nie istnieje żadne wewnętrzne znaczenie w ciągu wersji.</span><span class="sxs-lookup"><span data-stu-id="922d8-127">This string is opaque to the function user; that is, there is no intrinsic meaning in the version string itself.</span></span> <span data-ttu-id="922d8-128">Jest używana wyłącznie w kontekście tej funkcji i [funkcji CreateDebuggingInterfaceFromVersion —](createdebugginginterfacefromversion-function-for-silverlight.md).</span><span class="sxs-lookup"><span data-stu-id="922d8-128">It is used solely in the context of this function and the [CreateDebuggingInterfaceFromVersion function](createdebugginginterfacefromversion-function-for-silverlight.md).</span></span>  
  
 <span data-ttu-id="922d8-129">Ta funkcja powinna być wywoływana dwukrotnie.</span><span class="sxs-lookup"><span data-stu-id="922d8-129">This function should be called twice.</span></span> <span data-ttu-id="922d8-130">Po pierwszym wywołaniu należy przekazać wartość null dla obu `pBuffer` i `cchBuffer`.</span><span class="sxs-lookup"><span data-stu-id="922d8-130">When you call it the first time, pass null for both `pBuffer` and `cchBuffer`.</span></span> <span data-ttu-id="922d8-131">Gdy to zrobisz, rozmiar buforu niezbędnego do `pBuffer` zostanie zwrócony w `pdwLength`.</span><span class="sxs-lookup"><span data-stu-id="922d8-131">When you do this, the size of the buffer necessary for `pBuffer` will be returned in `pdwLength`.</span></span> <span data-ttu-id="922d8-132">Następnie można wywołać funkcję po raz drugi i przekazać bufor w `pBuffer` i jego rozmiar w `cchBuffer`.</span><span class="sxs-lookup"><span data-stu-id="922d8-132">You can then call the function a second time, and pass the buffer in `pBuffer` and its size in `cchBuffer`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="922d8-133">Wymagania</span><span class="sxs-lookup"><span data-stu-id="922d8-133">Requirements</span></span>  
 <span data-ttu-id="922d8-134">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="922d8-134">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="922d8-135">**Nagłówek:** dbgshim. h</span><span class="sxs-lookup"><span data-stu-id="922d8-135">**Header:** dbgshim.h</span></span>  
  
 <span data-ttu-id="922d8-136">**Biblioteka:** dbgshim. dll</span><span class="sxs-lookup"><span data-stu-id="922d8-136">**Library:** dbgshim.dll</span></span>  
  
 <span data-ttu-id="922d8-137">**.NET Framework wersje:** 3,5 SP1</span><span class="sxs-lookup"><span data-stu-id="922d8-137">**.NET Framework Versions:** 3.5 SP1</span></span>
