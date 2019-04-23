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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: df9cc0cc86237b1ec439a4ec4fa6a75429c416d9
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59111179"
---
# <a name="corvalidateimage-function"></a><span data-ttu-id="6c2d3-102">_CorValidateImage — Funkcja</span><span class="sxs-lookup"><span data-stu-id="6c2d3-102">_CorValidateImage Function</span></span>
<span data-ttu-id="6c2d3-103">Sprawdza poprawność obrazów modułu zarządzanego i powiadamia moduł ładujący systemu operacyjnego po ich załadowaniu.</span><span class="sxs-lookup"><span data-stu-id="6c2d3-103">Validates managed module images, and notifies the operating system loader after they have been loaded.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6c2d3-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="6c2d3-104">Syntax</span></span>  
  
```  
STDAPI _CorValidateImage (   
   [in] PVOID* ImageBase,  
   [in] LPCWSTR FileName  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="6c2d3-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="6c2d3-105">Parameters</span></span>  
 `ImageBase`  
 <span data-ttu-id="6c2d3-106">[in] Wskaźnik do początkową lokalizację obrazu do weryfikacji jako kod zarządzany.</span><span class="sxs-lookup"><span data-stu-id="6c2d3-106">[in] A pointer to the starting location of the image to validate as managed code.</span></span> <span data-ttu-id="6c2d3-107">Obraz musi już być ładowane do pamięci.</span><span class="sxs-lookup"><span data-stu-id="6c2d3-107">The image must already be loaded into memory.</span></span>  
  
 `FileName`  
 <span data-ttu-id="6c2d3-108">[in] Nazwa pliku obrazu.</span><span class="sxs-lookup"><span data-stu-id="6c2d3-108">[in] The file name of the image.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="6c2d3-109">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="6c2d3-109">Return Value</span></span>  
 <span data-ttu-id="6c2d3-110">Ta funkcja zwraca wartości standardowych `E_INVALIDARG`, `E_OUTOFMEMORY`, `E_UNEXPECTED`, i `E_FAIL`, a także poniższych wartości.</span><span class="sxs-lookup"><span data-stu-id="6c2d3-110">This function returns the standard values `E_INVALIDARG`, `E_OUTOFMEMORY`, `E_UNEXPECTED`, and `E_FAIL`, as well as the following values.</span></span>  
  
|<span data-ttu-id="6c2d3-111">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="6c2d3-111">Return value</span></span>|<span data-ttu-id="6c2d3-112">Opis</span><span class="sxs-lookup"><span data-stu-id="6c2d3-112">Description</span></span>|  
|------------------|-----------------|  
|`STATUS_INVALID_IMAGE_FORMAT`|<span data-ttu-id="6c2d3-113">Obraz jest nieprawidłowy.</span><span class="sxs-lookup"><span data-stu-id="6c2d3-113">The image is invalid.</span></span> <span data-ttu-id="6c2d3-114">Ta wartość ma HRESULT 0xC000007BL.</span><span class="sxs-lookup"><span data-stu-id="6c2d3-114">This value has the HRESULT 0xC000007BL.</span></span>|  
|`STATUS_SUCCESS`|<span data-ttu-id="6c2d3-115">Obraz jest prawidłowy.</span><span class="sxs-lookup"><span data-stu-id="6c2d3-115">The image is valid.</span></span> <span data-ttu-id="6c2d3-116">Ta wartość ma HRESULT 0x00000000L.</span><span class="sxs-lookup"><span data-stu-id="6c2d3-116">This value has the HRESULT 0x00000000L.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="6c2d3-117">Uwagi</span><span class="sxs-lookup"><span data-stu-id="6c2d3-117">Remarks</span></span>  
 <span data-ttu-id="6c2d3-118">Windows XP i nowszych wersjach moduł ładujący systemu operacyjnego sprawdza, czy modułów zarządzanych, sprawdzając bit COM deskryptora katalogu, w nagłówku format (COFF) pliku obiektu wspólnego.</span><span class="sxs-lookup"><span data-stu-id="6c2d3-118">In Windows XP and later versions, the operating system loader checks for managed modules by examining the COM Descriptor Directory bit in the common object file format (COFF) header.</span></span> <span data-ttu-id="6c2d3-119">Ustawionego bitu wskazuje modułu zarządzanego.</span><span class="sxs-lookup"><span data-stu-id="6c2d3-119">A set bit indicates a managed module.</span></span> <span data-ttu-id="6c2d3-120">Jeśli moduł ładujący wykryje modułu zarządzanego, ładuje MsCorEE.dll i wywołania `_CorValidateImage`, który wykonuje następujące czynności:</span><span class="sxs-lookup"><span data-stu-id="6c2d3-120">If the loader detects a managed module, it loads MsCorEE.dll and calls `_CorValidateImage`, which performs the following actions:</span></span>  
  
-   <span data-ttu-id="6c2d3-121">Potwierdza, że obraz jest prawidłowy modułu zarządzanego.</span><span class="sxs-lookup"><span data-stu-id="6c2d3-121">Confirms that the image is a valid managed module.</span></span>  
  
-   <span data-ttu-id="6c2d3-122">Zmiany punktu wejścia w obrazie punktu wejścia w środowisku uruchomieniowym języka (wspólnego CLR).</span><span class="sxs-lookup"><span data-stu-id="6c2d3-122">Changes the entry point in the image to an entry point in the common language runtime (CLR).</span></span>  
  
-   <span data-ttu-id="6c2d3-123">Dla 64-bitowej wersji systemu Windows modyfikuje obrazu, który znajduje się w pamięci przez przekształcenie go z PE32 je typu PE32 + format.</span><span class="sxs-lookup"><span data-stu-id="6c2d3-123">For 64-bit versions of Windows, modifies the image that is in memory by transforming it from PE32 to PE32+ format.</span></span>  
  
-   <span data-ttu-id="6c2d3-124">Zwraca do modułu ładującego, gdy obrazy modułu zarządzanego są ładowane.</span><span class="sxs-lookup"><span data-stu-id="6c2d3-124">Returns to the loader when the managed module images are loaded.</span></span>  
  
 <span data-ttu-id="6c2d3-125">Obrazy wykonywalne, następnie wywołuje moduł ładujący systemu operacyjnego [_corexemain —](../../../../docs/framework/unmanaged-api/hosting/corexemain-function.md) funkcji, niezależnie od tego, w punkcie wejścia określonym w pliku wykonywalnym.</span><span class="sxs-lookup"><span data-stu-id="6c2d3-125">For executable images, the operating system loader then calls the [_CorExeMain](../../../../docs/framework/unmanaged-api/hosting/corexemain-function.md) function, regardless of the entry point specified in the executable.</span></span> <span data-ttu-id="6c2d3-126">Biblioteka DLL zestawu obrazów, wywołuje moduł ładujący [_cordllmain —](../../../../docs/framework/unmanaged-api/hosting/cordllmain-function.md) funkcji.</span><span class="sxs-lookup"><span data-stu-id="6c2d3-126">For DLL assembly images, the loader calls the [_CorDllMain](../../../../docs/framework/unmanaged-api/hosting/cordllmain-function.md) function.</span></span>  
  
 <span data-ttu-id="6c2d3-127">`_CorExeMain` lub `_CorDllMain` wykonuje następujące czynności:</span><span class="sxs-lookup"><span data-stu-id="6c2d3-127">`_CorExeMain` or `_CorDllMain` performs the following actions:</span></span>  
  
-   <span data-ttu-id="6c2d3-128">Inicjuje środowisko CLR.</span><span class="sxs-lookup"><span data-stu-id="6c2d3-128">Initializes the CLR.</span></span>  
  
-   <span data-ttu-id="6c2d3-129">Lokalizuje zarządzany punkt wejścia w nagłówku CLR zestawu.</span><span class="sxs-lookup"><span data-stu-id="6c2d3-129">Locates the managed entry point from the assembly's CLR header.</span></span>  
  
-   <span data-ttu-id="6c2d3-130">Rozpoczyna wykonywanie.</span><span class="sxs-lookup"><span data-stu-id="6c2d3-130">Begins execution.</span></span>  
  
 <span data-ttu-id="6c2d3-131">Wywołania modułu ładującego [_corimageunloading —](../../../../docs/framework/unmanaged-api/hosting/corimageunloading-function.md) działają w przypadku zarządzanych obrazów modułu są usuwane z pamięci.</span><span class="sxs-lookup"><span data-stu-id="6c2d3-131">The loader calls the [_CorImageUnloading](../../../../docs/framework/unmanaged-api/hosting/corimageunloading-function.md) function when managed module images are unloaded.</span></span> <span data-ttu-id="6c2d3-132">Jednak ta funkcja nie wykonuje żadnych akcji; po prostu zwraca.</span><span class="sxs-lookup"><span data-stu-id="6c2d3-132">However, this function does not perform any action; it just returns.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6c2d3-133">Wymagania</span><span class="sxs-lookup"><span data-stu-id="6c2d3-133">Requirements</span></span>  
 <span data-ttu-id="6c2d3-134">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6c2d3-134">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6c2d3-135">**Nagłówek:** COR.h</span><span class="sxs-lookup"><span data-stu-id="6c2d3-135">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="6c2d3-136">**Biblioteka:** Dołączony jako zasób w MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="6c2d3-136">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="6c2d3-137">**Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6c2d3-137">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6c2d3-138">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="6c2d3-138">See also</span></span>

- [<span data-ttu-id="6c2d3-139">Statyczne funkcje globalne metadanych</span><span class="sxs-lookup"><span data-stu-id="6c2d3-139">Metadata Global Static Functions</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-global-static-functions.md)
