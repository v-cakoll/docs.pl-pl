---
title: _CorValidateImage — Funkcja
ms.date: 03/30/2017
api_name:
- _CorValidateImage
api_location:
- mscoree.dll
api_type:
- DLLExport
f1_keywords:
- _CorValidateImage
helpviewer_keywords:
- _CorValidateImage function [.NET Framework hosting]
ms.assetid: 0117e080-05f9-4772-885d-e1847230947c
topic_type:
- apiref
ms.openlocfilehash: 426b39aa3d1ada5ae44565a742b70681a7bcf6d3
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/08/2020
ms.locfileid: "84493477"
---
# <a name="_corvalidateimage-function"></a><span data-ttu-id="4bdf0-102">_CorValidateImage — Funkcja</span><span class="sxs-lookup"><span data-stu-id="4bdf0-102">_CorValidateImage Function</span></span>
<span data-ttu-id="4bdf0-103">Sprawdza poprawność obrazów modułu zarządzanego i powiadamia program ładujący system operacyjny po ich załadowaniu.</span><span class="sxs-lookup"><span data-stu-id="4bdf0-103">Validates managed module images, and notifies the operating system loader after they have been loaded.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4bdf0-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="4bdf0-104">Syntax</span></span>  
  
```cpp  
STDAPI _CorValidateImage (
   [in] PVOID* ImageBase,  
   [in] LPCWSTR FileName  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="4bdf0-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="4bdf0-105">Parameters</span></span>  
 `ImageBase`  
 <span data-ttu-id="4bdf0-106">podczas Wskaźnik do lokalizacji początkowej obrazu do zweryfikowania jako kod zarządzany.</span><span class="sxs-lookup"><span data-stu-id="4bdf0-106">[in] A pointer to the starting location of the image to validate as managed code.</span></span> <span data-ttu-id="4bdf0-107">Obraz musi już być załadowany do pamięci.</span><span class="sxs-lookup"><span data-stu-id="4bdf0-107">The image must already be loaded into memory.</span></span>  
  
 `FileName`  
 <span data-ttu-id="4bdf0-108">podczas Nazwa pliku obrazu.</span><span class="sxs-lookup"><span data-stu-id="4bdf0-108">[in] The file name of the image.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="4bdf0-109">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="4bdf0-109">Return Value</span></span>  
 <span data-ttu-id="4bdf0-110">Ta funkcja zwraca wartości standardowe `E_INVALIDARG` , `E_OUTOFMEMORY` , `E_UNEXPECTED` , i `E_FAIL` , jak również następujące wartości.</span><span class="sxs-lookup"><span data-stu-id="4bdf0-110">This function returns the standard values `E_INVALIDARG`, `E_OUTOFMEMORY`, `E_UNEXPECTED`, and `E_FAIL`, as well as the following values.</span></span>  
  
|<span data-ttu-id="4bdf0-111">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="4bdf0-111">Return value</span></span>|<span data-ttu-id="4bdf0-112">Opis</span><span class="sxs-lookup"><span data-stu-id="4bdf0-112">Description</span></span>|  
|------------------|-----------------|  
|`STATUS_INVALID_IMAGE_FORMAT`|<span data-ttu-id="4bdf0-113">Obraz jest nieprawidłowy.</span><span class="sxs-lookup"><span data-stu-id="4bdf0-113">The image is invalid.</span></span> <span data-ttu-id="4bdf0-114">Ta wartość ma wynik HRESULT 0xC000007BL.</span><span class="sxs-lookup"><span data-stu-id="4bdf0-114">This value has the HRESULT 0xC000007BL.</span></span>|  
|`STATUS_SUCCESS`|<span data-ttu-id="4bdf0-115">Obraz jest prawidłowy.</span><span class="sxs-lookup"><span data-stu-id="4bdf0-115">The image is valid.</span></span> <span data-ttu-id="4bdf0-116">Ta wartość ma wynik HRESULT.</span><span class="sxs-lookup"><span data-stu-id="4bdf0-116">This value has the HRESULT 0x00000000L.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="4bdf0-117">Uwagi</span><span class="sxs-lookup"><span data-stu-id="4bdf0-117">Remarks</span></span>  
 <span data-ttu-id="4bdf0-118">W systemie Windows XP i nowszych wersjach moduł ładujący systemu operacyjnego sprawdza moduły zarządzane, sprawdzając bit katalogu deskryptorów COM w nagłówku pliku Common Object Format (COFF).</span><span class="sxs-lookup"><span data-stu-id="4bdf0-118">In Windows XP and later versions, the operating system loader checks for managed modules by examining the COM Descriptor Directory bit in the common object file format (COFF) header.</span></span> <span data-ttu-id="4bdf0-119">Zestaw bit wskazuje moduł zarządzany.</span><span class="sxs-lookup"><span data-stu-id="4bdf0-119">A set bit indicates a managed module.</span></span> <span data-ttu-id="4bdf0-120">W przypadku wykrycia modułu zarządzanego przez moduł ładujący ładuje biblioteki MsCorEE. dll i wywołania `_CorValidateImage` , które wykonują następujące czynności:</span><span class="sxs-lookup"><span data-stu-id="4bdf0-120">If the loader detects a managed module, it loads MsCorEE.dll and calls `_CorValidateImage`, which performs the following actions:</span></span>  
  
- <span data-ttu-id="4bdf0-121">Potwierdza, że obraz jest prawidłowym modułem zarządzanym.</span><span class="sxs-lookup"><span data-stu-id="4bdf0-121">Confirms that the image is a valid managed module.</span></span>  
  
- <span data-ttu-id="4bdf0-122">Zmienia punkt wejścia w obrazie na punkt wejścia w środowisku uruchomieniowym języka wspólnego (CLR).</span><span class="sxs-lookup"><span data-stu-id="4bdf0-122">Changes the entry point in the image to an entry point in the common language runtime (CLR).</span></span>  
  
- <span data-ttu-id="4bdf0-123">W przypadku 64-bitowych wersji systemu Windows program modyfikuje obraz znajdujący się w pamięci, przekształcając go z PE32 na PE32 + format.</span><span class="sxs-lookup"><span data-stu-id="4bdf0-123">For 64-bit versions of Windows, modifies the image that is in memory by transforming it from PE32 to PE32+ format.</span></span>  
  
- <span data-ttu-id="4bdf0-124">Zwraca do modułu ładującego po załadowaniu obrazów modułu zarządzanego.</span><span class="sxs-lookup"><span data-stu-id="4bdf0-124">Returns to the loader when the managed module images are loaded.</span></span>  
  
 <span data-ttu-id="4bdf0-125">W przypadku obrazów wykonywalnych program ładujący systemu operacyjnego wywołuje funkcję [_CorExeMain](corexemain-function.md) , niezależnie od punktu wejścia określonego w pliku wykonywalnym.</span><span class="sxs-lookup"><span data-stu-id="4bdf0-125">For executable images, the operating system loader then calls the [_CorExeMain](corexemain-function.md) function, regardless of the entry point specified in the executable.</span></span> <span data-ttu-id="4bdf0-126">W przypadku obrazów zestawów bibliotek DLL moduł ładujący wywołuje funkcję [_CorDllMain](cordllmain-function.md) .</span><span class="sxs-lookup"><span data-stu-id="4bdf0-126">For DLL assembly images, the loader calls the [_CorDllMain](cordllmain-function.md) function.</span></span>  
  
 <span data-ttu-id="4bdf0-127">`_CorExeMain`lub `_CorDllMain` wykonuje następujące akcje:</span><span class="sxs-lookup"><span data-stu-id="4bdf0-127">`_CorExeMain` or `_CorDllMain` performs the following actions:</span></span>  
  
- <span data-ttu-id="4bdf0-128">Inicjuje środowisko CLR.</span><span class="sxs-lookup"><span data-stu-id="4bdf0-128">Initializes the CLR.</span></span>  
  
- <span data-ttu-id="4bdf0-129">Lokalizuje zarządzany punkt wejścia z nagłówka CLR zestawu.</span><span class="sxs-lookup"><span data-stu-id="4bdf0-129">Locates the managed entry point from the assembly's CLR header.</span></span>  
  
- <span data-ttu-id="4bdf0-130">Rozpoczyna wykonywanie.</span><span class="sxs-lookup"><span data-stu-id="4bdf0-130">Begins execution.</span></span>  
  
 <span data-ttu-id="4bdf0-131">Moduł ładujący wywołuje funkcję [_CorImageUnloading](corimageunloading-function.md) , gdy zarządzane obrazy modułu są zwolnione.</span><span class="sxs-lookup"><span data-stu-id="4bdf0-131">The loader calls the [_CorImageUnloading](corimageunloading-function.md) function when managed module images are unloaded.</span></span> <span data-ttu-id="4bdf0-132">Jednakże ta funkcja nie wykonuje żadnych działań; Zwraca wartość.</span><span class="sxs-lookup"><span data-stu-id="4bdf0-132">However, this function does not perform any action; it just returns.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4bdf0-133">Wymagania</span><span class="sxs-lookup"><span data-stu-id="4bdf0-133">Requirements</span></span>  
 <span data-ttu-id="4bdf0-134">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4bdf0-134">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4bdf0-135">**Nagłówek:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="4bdf0-135">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="4bdf0-136">**Biblioteka:** Uwzględnione jako zasób w bibliotece MsCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="4bdf0-136">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="4bdf0-137">**.NET Framework wersje:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4bdf0-137">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4bdf0-138">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="4bdf0-138">See also</span></span>

- [<span data-ttu-id="4bdf0-139">Statyczne funkcje globalne metadanych</span><span class="sxs-lookup"><span data-stu-id="4bdf0-139">Metadata Global Static Functions</span></span>](../metadata/metadata-global-static-functions.md)
