---
title: GetRequestedRuntimeVersionForCLSID — Funkcja
ms.date: 03/30/2017
api_name:
- GetRequestedRuntimeVersionForCLSID
api_location:
- mscoree.dll
api_type:
- DLLExport
f1_keywords:
- GetRequestedRuntimeVersionForCLSID
helpviewer_keywords:
- GetRequestedRuntimeVersionForCLSID function [.NET Framework hosting]
ms.assetid: 5bb12f9a-0612-434b-b4ed-2db636a20bec
topic_type:
- apiref
ms.openlocfilehash: 6132e94544b30486b70ecfec49c1ddd5e3c0f50b
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79178113"
---
# <a name="getrequestedruntimeversionforclsid-function"></a><span data-ttu-id="e7b7b-102">GetRequestedRuntimeVersionForCLSID — Funkcja</span><span class="sxs-lookup"><span data-stu-id="e7b7b-102">GetRequestedRuntimeVersionForCLSID Function</span></span>
<span data-ttu-id="e7b7b-103">Pobiera odpowiednie informacje o wersji wspólnego środowiska wykonawczego języka (CLR) dla klasy z określonym `CLSID`.</span><span class="sxs-lookup"><span data-stu-id="e7b7b-103">Gets the appropriate common language runtime (CLR) version information for the class with the specified `CLSID`.</span></span>  
  
 <span data-ttu-id="e7b7b-104">Ta funkcja została przestarzała w .NET Framework 4.</span><span class="sxs-lookup"><span data-stu-id="e7b7b-104">This function has been deprecated in the .NET Framework 4.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e7b7b-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="e7b7b-105">Syntax</span></span>  
  
```cpp  
HRESULT GetRequestedRuntimeVersionForCLSID (  
    [in]  REFCLSID   rclsid,
    [out]  LPWSTR     pVersion,
    [in]  DWORD      cchBuffer,
    [out] DWORD*     dwLength,
    [in]  CLSID_RESOLUTION_FLAGS dwResolutionFlags  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="e7b7b-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="e7b7b-106">Parameters</span></span>  
 `rclsid`  
 <span data-ttu-id="e7b7b-107">[w]  Składnika. `CLSID`</span><span class="sxs-lookup"><span data-stu-id="e7b7b-107">[in]  The `CLSID` of the component.</span></span>  
  
 `pVersion`  
 <span data-ttu-id="e7b7b-108">[na zewnątrz]  Bufor, który zawiera ciąg numeru wersji po pomyślnym zakończeniu.</span><span class="sxs-lookup"><span data-stu-id="e7b7b-108">[out]  A buffer that contains the version number string upon successful completion.</span></span>  
  
 `cchBuffer`  
 <span data-ttu-id="e7b7b-109">[w]  Rozmiar buforu `pVersion` w postaci szerokich znaków.</span><span class="sxs-lookup"><span data-stu-id="e7b7b-109">[in]  The size, in wide characters, of the `pVersion` buffer.</span></span>  
  
 `dwLength`  
 <span data-ttu-id="e7b7b-110">[na zewnątrz] Długość w bajtach zwracanego buforu.</span><span class="sxs-lookup"><span data-stu-id="e7b7b-110">[out] The length, in bytes, of the returned buffer.</span></span>  
  
 `dwResolutionFlags`  
 <span data-ttu-id="e7b7b-111">[w]  Jedną z CLSID_RESOLUTION_FLAGS wartości.</span><span class="sxs-lookup"><span data-stu-id="e7b7b-111">[in]  One of the CLSID_RESOLUTION_FLAGS values.</span></span> <span data-ttu-id="e7b7b-112">Obsługiwane są następujące wartości:</span><span class="sxs-lookup"><span data-stu-id="e7b7b-112">The following values are supported:</span></span>  
  
- <span data-ttu-id="e7b7b-113">CLSID_RESOLUTION_DEFAULT: (0x0) Określa, że domyślne zachowanie interop powinny być używane.</span><span class="sxs-lookup"><span data-stu-id="e7b7b-113">CLSID_RESOLUTION_DEFAULT: (0x0) Specifies that default interop behavior should be used.</span></span>  
  
- <span data-ttu-id="e7b7b-114">CLSID_RESOLUTION_REGISTERED: (0x1) Określa, że rejestr powinien być przeszukiwany i zasady podkładki powinny być stosowane.</span><span class="sxs-lookup"><span data-stu-id="e7b7b-114">CLSID_RESOLUTION_REGISTERED: (0x1) Specifies that the registry should be searched and shim policy should be applied.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="e7b7b-115">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="e7b7b-115">Return Value</span></span>  
  
|<span data-ttu-id="e7b7b-116">HRESULT</span><span class="sxs-lookup"><span data-stu-id="e7b7b-116">HRESULT</span></span>|<span data-ttu-id="e7b7b-117">Opis</span><span class="sxs-lookup"><span data-stu-id="e7b7b-117">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="e7b7b-118">S_OK</span><span class="sxs-lookup"><span data-stu-id="e7b7b-118">S_OK</span></span>|<span data-ttu-id="e7b7b-119">Funkcja została zwrócona pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="e7b7b-119">The function returned successfully.</span></span>|  
|<span data-ttu-id="e7b7b-120">E_invalidarg</span><span class="sxs-lookup"><span data-stu-id="e7b7b-120">E_INVALIDARG</span></span>|<span data-ttu-id="e7b7b-121">Jeden z parametrów ma nieprawidłowy typ lub format.</span><span class="sxs-lookup"><span data-stu-id="e7b7b-121">One of the parameters has an invalid type or format.</span></span>|  
|<span data-ttu-id="e7b7b-122">ERROR_INSUFFICIENT_BUFFER</span><span class="sxs-lookup"><span data-stu-id="e7b7b-122">ERROR_INSUFFICIENT_BUFFER</span></span>|<span data-ttu-id="e7b7b-123">Bufor `pVersion` nie jest wystarczająco duży, aby pomieścić cały ciąg wersji.</span><span class="sxs-lookup"><span data-stu-id="e7b7b-123">The `pVersion` buffer is not large enough to hold the entire version string.</span></span>|  
|<span data-ttu-id="e7b7b-124">REGDB_E_CLASSNOTREG</span><span class="sxs-lookup"><span data-stu-id="e7b7b-124">REGDB_E_CLASSNOTREG</span></span>|<span data-ttu-id="e7b7b-125">Nie ma żadnej klasy `CLSID`zarejestrowanej z określonym .</span><span class="sxs-lookup"><span data-stu-id="e7b7b-125">There is no class registered with the specified `CLSID`.</span></span>|  
|<span data-ttu-id="e7b7b-126">E_pointer</span><span class="sxs-lookup"><span data-stu-id="e7b7b-126">E_POINTER</span></span>|<span data-ttu-id="e7b7b-127">`dwLength`jest null `cchBuffer` lub jest wystarczająco duży, aby `pVersion` pomieścić ciąg wersji, ale jest null.</span><span class="sxs-lookup"><span data-stu-id="e7b7b-127">`dwLength` is null, or `cchBuffer` is large enough to hold the version string, but `pVersion` is null.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="e7b7b-128">Wymagania</span><span class="sxs-lookup"><span data-stu-id="e7b7b-128">Requirements</span></span>  
 <span data-ttu-id="e7b7b-129">**Platformy:** Zobacz [Wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e7b7b-129">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e7b7b-130">**Nagłówek:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="e7b7b-130">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="e7b7b-131">**Wersje programu .NET Framework:**[!INCLUDE[net_current_v11plus](../../../../includes/net-current-v11plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e7b7b-131">**.NET Framework Versions:** [!INCLUDE[net_current_v11plus](../../../../includes/net-current-v11plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e7b7b-132">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="e7b7b-132">See also</span></span>

- [<span data-ttu-id="e7b7b-133">Przestarzałe funkcje hostingu środowiska CLR</span><span class="sxs-lookup"><span data-stu-id="e7b7b-133">Deprecated CLR Hosting Functions</span></span>](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
