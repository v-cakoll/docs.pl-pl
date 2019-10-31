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
ms.openlocfilehash: ce0c6307defd93dcf63ac4e9051fc798041475f3
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73127051"
---
# <a name="getrequestedruntimeversionforclsid-function"></a><span data-ttu-id="f5629-102">GetRequestedRuntimeVersionForCLSID — Funkcja</span><span class="sxs-lookup"><span data-stu-id="f5629-102">GetRequestedRuntimeVersionForCLSID Function</span></span>
<span data-ttu-id="f5629-103">Pobiera odpowiednie informacje o wersji środowiska uruchomieniowego języka wspólnego (CLR) dla klasy z określonym `CLSID`.</span><span class="sxs-lookup"><span data-stu-id="f5629-103">Gets the appropriate common language runtime (CLR) version information for the class with the specified `CLSID`.</span></span>  
  
 <span data-ttu-id="f5629-104">Ta funkcja jest przestarzała w .NET Framework 4.</span><span class="sxs-lookup"><span data-stu-id="f5629-104">This function has been deprecated in the .NET Framework 4.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f5629-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="f5629-105">Syntax</span></span>  
  
```cpp  
HRESULT GetRequestedRuntimeVersionForCLSID (  
    [in]  REFCLSID   rclsid,   
    [out]  LPWSTR     pVersion,   
    [in]  DWORD      cchBuffer,   
    [out] DWORD*     dwLength,   
    [in]  CLSID_RESOLUTION_FLAGS dwResolutionFlags  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="f5629-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="f5629-106">Parameters</span></span>  
 `rclsid`  
 <span data-ttu-id="f5629-107">podczas  `CLSID` składnika.</span><span class="sxs-lookup"><span data-stu-id="f5629-107">[in]  The `CLSID` of the component.</span></span>  
  
 `pVersion`  
 <span data-ttu-id="f5629-108">określoną  Bufor zawierający ciąg numeru wersji po pomyślnym zakończeniu.</span><span class="sxs-lookup"><span data-stu-id="f5629-108">[out]  A buffer that contains the version number string upon successful completion.</span></span>  
  
 `cchBuffer`  
 <span data-ttu-id="f5629-109">podczas  Rozmiar (w bajtach) w buforze `pVersion`.</span><span class="sxs-lookup"><span data-stu-id="f5629-109">[in]  The size, in wide characters, of the `pVersion` buffer.</span></span>  
  
 `dwLength`  
 <span data-ttu-id="f5629-110">określoną Długość (w bajtach) zwróconego buforu.</span><span class="sxs-lookup"><span data-stu-id="f5629-110">[out] The length, in bytes, of the returned buffer.</span></span>  
  
 `dwResolutionFlags`  
 <span data-ttu-id="f5629-111">podczas  Jedna z wartości CLSID_RESOLUTION_FLAGS.</span><span class="sxs-lookup"><span data-stu-id="f5629-111">[in]  One of the CLSID_RESOLUTION_FLAGS values.</span></span> <span data-ttu-id="f5629-112">Obsługiwane są następujące wartości:</span><span class="sxs-lookup"><span data-stu-id="f5629-112">The following values are supported:</span></span>  
  
- <span data-ttu-id="f5629-113">CLSID_RESOLUTION_DEFAULT: (0x0) określa, że należy użyć domyślnego zachowania międzyoperacyjności.</span><span class="sxs-lookup"><span data-stu-id="f5629-113">CLSID_RESOLUTION_DEFAULT: (0x0) Specifies that default interop behavior should be used.</span></span>  
  
- <span data-ttu-id="f5629-114">CLSID_RESOLUTION_REGISTERED: (0x1) określa, że rejestr powinien być przeszukiwany, a zasady podkładki powinny być stosowane.</span><span class="sxs-lookup"><span data-stu-id="f5629-114">CLSID_RESOLUTION_REGISTERED: (0x1) Specifies that the registry should be searched and shim policy should be applied.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="f5629-115">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="f5629-115">Return Value</span></span>  
  
|<span data-ttu-id="f5629-116">HRESULT</span><span class="sxs-lookup"><span data-stu-id="f5629-116">HRESULT</span></span>|<span data-ttu-id="f5629-117">Opis</span><span class="sxs-lookup"><span data-stu-id="f5629-117">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="f5629-118">S_OK</span><span class="sxs-lookup"><span data-stu-id="f5629-118">S_OK</span></span>|<span data-ttu-id="f5629-119">Funkcja została pomyślnie zwrócona.</span><span class="sxs-lookup"><span data-stu-id="f5629-119">The function returned successfully.</span></span>|  
|<span data-ttu-id="f5629-120">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="f5629-120">E_INVALIDARG</span></span>|<span data-ttu-id="f5629-121">Jeden z parametrów ma nieprawidłowy typ lub format.</span><span class="sxs-lookup"><span data-stu-id="f5629-121">One of the parameters has an invalid type or format.</span></span>|  
|<span data-ttu-id="f5629-122">ERROR_INSUFFICIENT_BUFFER</span><span class="sxs-lookup"><span data-stu-id="f5629-122">ERROR_INSUFFICIENT_BUFFER</span></span>|<span data-ttu-id="f5629-123">Bufor `pVersion` nie jest wystarczająco duży, aby pomieścić cały ciąg wersji.</span><span class="sxs-lookup"><span data-stu-id="f5629-123">The `pVersion` buffer is not large enough to hold the entire version string.</span></span>|  
|<span data-ttu-id="f5629-124">REGDB_E_CLASSNOTREG</span><span class="sxs-lookup"><span data-stu-id="f5629-124">REGDB_E_CLASSNOTREG</span></span>|<span data-ttu-id="f5629-125">Nie ma żadnej klasy zarejestrowanej w określonym `CLSID`.</span><span class="sxs-lookup"><span data-stu-id="f5629-125">There is no class registered with the specified `CLSID`.</span></span>|  
|<span data-ttu-id="f5629-126">E_POINTER</span><span class="sxs-lookup"><span data-stu-id="f5629-126">E_POINTER</span></span>|<span data-ttu-id="f5629-127">`dwLength` ma wartość null lub `cchBuffer` jest wystarczająco duży, aby pomieścić ciąg wersji, ale `pVersion` ma wartość null.</span><span class="sxs-lookup"><span data-stu-id="f5629-127">`dwLength` is null, or `cchBuffer` is large enough to hold the version string, but `pVersion` is null.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="f5629-128">Wymagania</span><span class="sxs-lookup"><span data-stu-id="f5629-128">Requirements</span></span>  
 <span data-ttu-id="f5629-129">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f5629-129">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f5629-130">**Nagłówek:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="f5629-130">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="f5629-131">**Wersje .NET Framework:** [!INCLUDE[net_current_v11plus](../../../../includes/net-current-v11plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f5629-131">**.NET Framework Versions:** [!INCLUDE[net_current_v11plus](../../../../includes/net-current-v11plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f5629-132">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="f5629-132">See also</span></span>

- [<span data-ttu-id="f5629-133">Przestarzałe funkcje hostingu środowiska CLR</span><span class="sxs-lookup"><span data-stu-id="f5629-133">Deprecated CLR Hosting Functions</span></span>](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
