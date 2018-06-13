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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: e8d3a7168ce0ee3484384ae0e2d10ca00367fc9c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33432862"
---
# <a name="getrequestedruntimeversionforclsid-function"></a><span data-ttu-id="2ed17-102">GetRequestedRuntimeVersionForCLSID — Funkcja</span><span class="sxs-lookup"><span data-stu-id="2ed17-102">GetRequestedRuntimeVersionForCLSID Function</span></span>
<span data-ttu-id="2ed17-103">Pobiera odpowiednie wspólnego języka środowiska uruchomieniowego (języka wspólnego CLR) informacje o wersji dla klasy z określonym `CLSID`.</span><span class="sxs-lookup"><span data-stu-id="2ed17-103">Gets the appropriate common language runtime (CLR) version information for the class with the specified `CLSID`.</span></span>  
  
 <span data-ttu-id="2ed17-104">Ta funkcja jest przestarzała w [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)].</span><span class="sxs-lookup"><span data-stu-id="2ed17-104">This function has been deprecated in the [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)].</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2ed17-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="2ed17-105">Syntax</span></span>  
  
```  
HRESULT GetRequestedRuntimeVersionForCLSID (  
    [in]  REFCLSID   rclsid,   
    [out]  LPWSTR     pVersion,   
    [in]  DWORD      cchBuffer,   
    [out] DWORD*     dwLength,   
    [in]  CLSID_RESOLUTION_FLAGS dwResolutionFlags  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="2ed17-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="2ed17-106">Parameters</span></span>  
 `rclsid`  
 <span data-ttu-id="2ed17-107">[in]  `CLSID` Składnika.</span><span class="sxs-lookup"><span data-stu-id="2ed17-107">[in]  The `CLSID` of the component.</span></span>  
  
 `pVersion`  
 <span data-ttu-id="2ed17-108">[out]  Buforu, który zawiera ciąg numer wersji na pomyślne zakończenie.</span><span class="sxs-lookup"><span data-stu-id="2ed17-108">[out]  A buffer that contains the version number string upon successful completion.</span></span>  
  
 `cchBuffer`  
 <span data-ttu-id="2ed17-109">[in]  Rozmiar w znaki dwubajtowe z `pVersion` buforu.</span><span class="sxs-lookup"><span data-stu-id="2ed17-109">[in]  The size, in wide characters, of the `pVersion` buffer.</span></span>  
  
 `dwLength`  
 <span data-ttu-id="2ed17-110">[out] Długość, w bajtach buforu zwrócony.</span><span class="sxs-lookup"><span data-stu-id="2ed17-110">[out] The length, in bytes, of the returned buffer.</span></span>  
  
 `dwResolutionFlags`  
 <span data-ttu-id="2ed17-111">[in]  Jedna z wartości CLSID_RESOLUTION_FLAGS.</span><span class="sxs-lookup"><span data-stu-id="2ed17-111">[in]  One of the CLSID_RESOLUTION_FLAGS values.</span></span> <span data-ttu-id="2ed17-112">Obsługiwane są następujące wartości:</span><span class="sxs-lookup"><span data-stu-id="2ed17-112">The following values are supported:</span></span>  
  
-   <span data-ttu-id="2ed17-113">CLSID_RESOLUTION_DEFAULT: (0x0) określa, że domyślne zachowanie międzyoperacyjnego powinien być używany.</span><span class="sxs-lookup"><span data-stu-id="2ed17-113">CLSID_RESOLUTION_DEFAULT: (0x0) Specifies that default interop behavior should be used.</span></span>  
  
-   <span data-ttu-id="2ed17-114">CLSID_RESOLUTION_REGISTERED: (0x1) określa, czy rejestr powinna być dodatkowo przeszukiwana i użyć podkładek zasad powinny być stosowane.</span><span class="sxs-lookup"><span data-stu-id="2ed17-114">CLSID_RESOLUTION_REGISTERED: (0x1) Specifies that the registry should be searched and shim policy should be applied.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="2ed17-115">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="2ed17-115">Return Value</span></span>  
  
|<span data-ttu-id="2ed17-116">HRESULT</span><span class="sxs-lookup"><span data-stu-id="2ed17-116">HRESULT</span></span>|<span data-ttu-id="2ed17-117">Opis</span><span class="sxs-lookup"><span data-stu-id="2ed17-117">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="2ed17-118">S_OK</span><span class="sxs-lookup"><span data-stu-id="2ed17-118">S_OK</span></span>|<span data-ttu-id="2ed17-119">Wartość zwrócona przez funkcję pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="2ed17-119">The function returned successfully.</span></span>|  
|<span data-ttu-id="2ed17-120">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="2ed17-120">E_INVALIDARG</span></span>|<span data-ttu-id="2ed17-121">Jeden z parametrów ma nieprawidłowy typ lub format.</span><span class="sxs-lookup"><span data-stu-id="2ed17-121">One of the parameters has an invalid type or format.</span></span>|  
|<span data-ttu-id="2ed17-122">ERROR_INSUFFICIENT_BUFFER</span><span class="sxs-lookup"><span data-stu-id="2ed17-122">ERROR_INSUFFICIENT_BUFFER</span></span>|<span data-ttu-id="2ed17-123">`pVersion` Bufor nie jest wystarczająco duży, aby pomieścić ciąg całej wersji.</span><span class="sxs-lookup"><span data-stu-id="2ed17-123">The `pVersion` buffer is not large enough to hold the entire version string.</span></span>|  
|<span data-ttu-id="2ed17-124">REGDB_E_CLASSNOTREG</span><span class="sxs-lookup"><span data-stu-id="2ed17-124">REGDB_E_CLASSNOTREG</span></span>|<span data-ttu-id="2ed17-125">Istnieje klasa nie jest zarejestrowany z określonym `CLSID`.</span><span class="sxs-lookup"><span data-stu-id="2ed17-125">There is no class registered with the specified `CLSID`.</span></span>|  
|<span data-ttu-id="2ed17-126">E_POINTER</span><span class="sxs-lookup"><span data-stu-id="2ed17-126">E_POINTER</span></span>|<span data-ttu-id="2ed17-127">`dwLength` ma wartość null, lub `cchBuffer` jest wystarczająco duży, aby pomieścić ciąg wersji, ale `pVersion` ma wartość null.</span><span class="sxs-lookup"><span data-stu-id="2ed17-127">`dwLength` is null, or `cchBuffer` is large enough to hold the version string, but `pVersion` is null.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="2ed17-128">Wymagania</span><span class="sxs-lookup"><span data-stu-id="2ed17-128">Requirements</span></span>  
 <span data-ttu-id="2ed17-129">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2ed17-129">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2ed17-130">**Nagłówek:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="2ed17-130">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="2ed17-131">**Wersje programu .NET framework:** [!INCLUDE[net_current_v11plus](../../../../includes/net-current-v11plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2ed17-131">**.NET Framework Versions:** [!INCLUDE[net_current_v11plus](../../../../includes/net-current-v11plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2ed17-132">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="2ed17-132">See Also</span></span>  
 [<span data-ttu-id="2ed17-133">Przestarzałe funkcje hostingu środowiska CLR</span><span class="sxs-lookup"><span data-stu-id="2ed17-133">Deprecated CLR Hosting Functions</span></span>](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
