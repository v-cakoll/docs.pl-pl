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
ms.openlocfilehash: 3a6da0e845fa50d090cdf0808b211a5806c40961
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79178217"
---
# <a name="_corvalidateimage-function"></a><span data-ttu-id="1c677-102">_CorValidateImage — Funkcja</span><span class="sxs-lookup"><span data-stu-id="1c677-102">_CorValidateImage Function</span></span>
<span data-ttu-id="1c677-103">Sprawdza poprawność obrazów modułów zarządzanych i powiadamia moduł ładujący systemu operacyjnego po ich załadowaniu.</span><span class="sxs-lookup"><span data-stu-id="1c677-103">Validates managed module images, and notifies the operating system loader after they have been loaded.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1c677-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="1c677-104">Syntax</span></span>  
  
```cpp  
STDAPI _CorValidateImage (
   [in] PVOID* ImageBase,  
   [in] LPCWSTR FileName  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="1c677-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="1c677-105">Parameters</span></span>  
 `ImageBase`  
 <span data-ttu-id="1c677-106">[w] Wskaźnik do lokalizacji początkowej obrazu, aby sprawdzić poprawność jako kod zarządzany.</span><span class="sxs-lookup"><span data-stu-id="1c677-106">[in] A pointer to the starting location of the image to validate as managed code.</span></span> <span data-ttu-id="1c677-107">Obraz musi być już załadowany do pamięci.</span><span class="sxs-lookup"><span data-stu-id="1c677-107">The image must already be loaded into memory.</span></span>  
  
 `FileName`  
 <span data-ttu-id="1c677-108">[w] Nazwa pliku obrazu.</span><span class="sxs-lookup"><span data-stu-id="1c677-108">[in] The file name of the image.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="1c677-109">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="1c677-109">Return Value</span></span>  
 <span data-ttu-id="1c677-110">Ta funkcja zwraca `E_INVALIDARG`wartości `E_OUTOFMEMORY` `E_UNEXPECTED`standardowe `E_FAIL`, , i , a także następujące wartości.</span><span class="sxs-lookup"><span data-stu-id="1c677-110">This function returns the standard values `E_INVALIDARG`, `E_OUTOFMEMORY`, `E_UNEXPECTED`, and `E_FAIL`, as well as the following values.</span></span>  
  
|<span data-ttu-id="1c677-111">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="1c677-111">Return value</span></span>|<span data-ttu-id="1c677-112">Opis</span><span class="sxs-lookup"><span data-stu-id="1c677-112">Description</span></span>|  
|------------------|-----------------|  
|`STATUS_INVALID_IMAGE_FORMAT`|<span data-ttu-id="1c677-113">Obraz jest nieprawidłowy.</span><span class="sxs-lookup"><span data-stu-id="1c677-113">The image is invalid.</span></span> <span data-ttu-id="1c677-114">Ta wartość ma HRESULT 0xC000007BL.</span><span class="sxs-lookup"><span data-stu-id="1c677-114">This value has the HRESULT 0xC000007BL.</span></span>|  
|`STATUS_SUCCESS`|<span data-ttu-id="1c677-115">Obraz jest prawidłowy.</span><span class="sxs-lookup"><span data-stu-id="1c677-115">The image is valid.</span></span> <span data-ttu-id="1c677-116">Ta wartość ma HRESULT 0x0000000L.</span><span class="sxs-lookup"><span data-stu-id="1c677-116">This value has the HRESULT 0x00000000L.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="1c677-117">Uwagi</span><span class="sxs-lookup"><span data-stu-id="1c677-117">Remarks</span></span>  
 <span data-ttu-id="1c677-118">W systemie Windows XP i nowszych wersjach program ładujący systemu operacyjnego sprawdza moduły zarządzane, sprawdzając bit katalogu deskryptora COM w nagłówku wspólnego formatu pliku obiektu (COFF).</span><span class="sxs-lookup"><span data-stu-id="1c677-118">In Windows XP and later versions, the operating system loader checks for managed modules by examining the COM Descriptor Directory bit in the common object file format (COFF) header.</span></span> <span data-ttu-id="1c677-119">Bit zestawu wskazuje moduł zarządzany.</span><span class="sxs-lookup"><span data-stu-id="1c677-119">A set bit indicates a managed module.</span></span> <span data-ttu-id="1c677-120">Jeśli moduł ładujący wykryje moduł zarządzany, ładuje msCorEE.dll i wywołuje `_CorValidateImage`, który wykonuje następujące akcje:</span><span class="sxs-lookup"><span data-stu-id="1c677-120">If the loader detects a managed module, it loads MsCorEE.dll and calls `_CorValidateImage`, which performs the following actions:</span></span>  
  
- <span data-ttu-id="1c677-121">Potwierdza, że obraz jest prawidłowym modułem zarządzanym.</span><span class="sxs-lookup"><span data-stu-id="1c677-121">Confirms that the image is a valid managed module.</span></span>  
  
- <span data-ttu-id="1c677-122">Zmienia punkt wejścia na obrazie na punkt wejścia w czasie wykonywania języka wspólnego (CLR).</span><span class="sxs-lookup"><span data-stu-id="1c677-122">Changes the entry point in the image to an entry point in the common language runtime (CLR).</span></span>  
  
- <span data-ttu-id="1c677-123">W przypadku 64-bitowych wersji systemu Windows modyfikuje obraz w pamięci, przekształcając go z pe32 do formatu PE32+.</span><span class="sxs-lookup"><span data-stu-id="1c677-123">For 64-bit versions of Windows, modifies the image that is in memory by transforming it from PE32 to PE32+ format.</span></span>  
  
- <span data-ttu-id="1c677-124">Powraca do modułu ładującego po załadowaniu obrazów modułu zarządzanego.</span><span class="sxs-lookup"><span data-stu-id="1c677-124">Returns to the loader when the managed module images are loaded.</span></span>  
  
 <span data-ttu-id="1c677-125">W przypadku obrazów wykonywalnych program ładujący systemu operacyjnego wywołuje następnie funkcję [_CorExeMain,](../../../../docs/framework/unmanaged-api/hosting/corexemain-function.md) niezależnie od punktu wejścia określonego w pliku wykonywalnym.</span><span class="sxs-lookup"><span data-stu-id="1c677-125">For executable images, the operating system loader then calls the [_CorExeMain](../../../../docs/framework/unmanaged-api/hosting/corexemain-function.md) function, regardless of the entry point specified in the executable.</span></span> <span data-ttu-id="1c677-126">W przypadku obrazów zestawu DLL moduł ładujący wywołuje funkcję [_CorDllMain.](../../../../docs/framework/unmanaged-api/hosting/cordllmain-function.md)</span><span class="sxs-lookup"><span data-stu-id="1c677-126">For DLL assembly images, the loader calls the [_CorDllMain](../../../../docs/framework/unmanaged-api/hosting/cordllmain-function.md) function.</span></span>  
  
 <span data-ttu-id="1c677-127">`_CorExeMain`lub `_CorDllMain` wykonuje następujące czynności:</span><span class="sxs-lookup"><span data-stu-id="1c677-127">`_CorExeMain` or `_CorDllMain` performs the following actions:</span></span>  
  
- <span data-ttu-id="1c677-128">Inicjuje clr.</span><span class="sxs-lookup"><span data-stu-id="1c677-128">Initializes the CLR.</span></span>  
  
- <span data-ttu-id="1c677-129">Lokalizuje zarządzany punkt wejścia z nagłówka CLR zestawu.</span><span class="sxs-lookup"><span data-stu-id="1c677-129">Locates the managed entry point from the assembly's CLR header.</span></span>  
  
- <span data-ttu-id="1c677-130">Rozpoczyna wykonywanie.</span><span class="sxs-lookup"><span data-stu-id="1c677-130">Begins execution.</span></span>  
  
 <span data-ttu-id="1c677-131">Moduł ładujący wywołuje funkcję [_CorImageUnloading,](../../../../docs/framework/unmanaged-api/hosting/corimageunloading-function.md) gdy obrazy modułów zarządzanych są zwalniane.</span><span class="sxs-lookup"><span data-stu-id="1c677-131">The loader calls the [_CorImageUnloading](../../../../docs/framework/unmanaged-api/hosting/corimageunloading-function.md) function when managed module images are unloaded.</span></span> <span data-ttu-id="1c677-132">Jednak ta funkcja nie wykonuje żadnych akcji; po prostu powraca.</span><span class="sxs-lookup"><span data-stu-id="1c677-132">However, this function does not perform any action; it just returns.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1c677-133">Wymagania</span><span class="sxs-lookup"><span data-stu-id="1c677-133">Requirements</span></span>  
 <span data-ttu-id="1c677-134">**Platformy:** Zobacz [Wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1c677-134">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1c677-135">**Nagłówek:** Okręg wyborczy Cor.h</span><span class="sxs-lookup"><span data-stu-id="1c677-135">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="1c677-136">**Biblioteka:** Uwzględnione jako zasób w pliku MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="1c677-136">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="1c677-137">**Wersje programu .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1c677-137">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1c677-138">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="1c677-138">See also</span></span>

- [<span data-ttu-id="1c677-139">Statyczne funkcje globalne metadanych</span><span class="sxs-lookup"><span data-stu-id="1c677-139">Metadata Global Static Functions</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-global-static-functions.md)
