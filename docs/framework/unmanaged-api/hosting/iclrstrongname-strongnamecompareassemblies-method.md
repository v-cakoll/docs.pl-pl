---
title: ICLRStrongName::StrongNameCompareAssemblies — Metoda
ms.date: 03/30/2017
api_name:
- ICLRStrongName.StrongNameCompareAssemblies
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRStrongName::StrongNameCompareAssemblies
helpviewer_keywords:
- ICLRStrongName::StrongNameCompareAssemblies method [.NET Framework hosting]
- StrongNameCompareAssemblies method, ICLRStrongName interface [.NET Framework hosting]
ms.assetid: b1fb356c-72cf-4aa4-8376-f291a6d97c01
topic_type:
- apiref
ms.openlocfilehash: fdca03b781e07b709cbc54e673dbaa2a1130fbe3
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73135145"
---
# <a name="iclrstrongnamestrongnamecompareassemblies-method"></a><span data-ttu-id="8b032-102">ICLRStrongName::StrongNameCompareAssemblies — Metoda</span><span class="sxs-lookup"><span data-stu-id="8b032-102">ICLRStrongName::StrongNameCompareAssemblies Method</span></span>
<span data-ttu-id="8b032-103">Określa, czy dwa zestawy różnią się tylko sygnaturami silnej nazwy.</span><span class="sxs-lookup"><span data-stu-id="8b032-103">Determines whether two assemblies differ only by their strong name signatures.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8b032-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="8b032-104">Syntax</span></span>  
  
```cpp  
HRESULT StrongNameCompareAssemblies (  
    [in]  LPCWSTR   wszAssembly1,  
    [in]  LPCWSTR   wszAssembly2,  
    [out] DWORD     *pdwResult  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="8b032-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="8b032-105">Parameters</span></span>  
 `wszAssembly1`  
 <span data-ttu-id="8b032-106">podczas Ścieżka do pierwszego zestawu.</span><span class="sxs-lookup"><span data-stu-id="8b032-106">[in] The path to the first assembly.</span></span>  
  
 `wszAssembly2`  
 <span data-ttu-id="8b032-107">podczas Ścieżka do drugiego zestawu.</span><span class="sxs-lookup"><span data-stu-id="8b032-107">[in] The path to the second assembly.</span></span>  
  
 `pdwResult`  
 <span data-ttu-id="8b032-108">określoną Jedna z następujących wartości:</span><span class="sxs-lookup"><span data-stu-id="8b032-108">[out] One of the following values:</span></span>  
  
- <span data-ttu-id="8b032-109">`SN_CMP_DIFFERENT` (0) — określa, że zestawy zawierają różne dane.</span><span class="sxs-lookup"><span data-stu-id="8b032-109">`SN_CMP_DIFFERENT` (0) - Specifies that the assemblies contain different data.</span></span>  
  
- <span data-ttu-id="8b032-110">`SN_CMP_IDENTICAL` (1) — określa, że zestawy są dokładnie takie same, łącznie z ich sygnaturami i sumą kontrolną.</span><span class="sxs-lookup"><span data-stu-id="8b032-110">`SN_CMP_IDENTICAL` (1) - Specifies that the assemblies are exactly the same, including their signatures and checksum.</span></span>  
  
- <span data-ttu-id="8b032-111">`SN_CMP_SIGONLY` (2) — określa, że zestawy różnią się tylko sygnaturą i sumą kontrolną.</span><span class="sxs-lookup"><span data-stu-id="8b032-111">`SN_CMP_SIGONLY` (2) - Specifies that the assemblies differ only by signature and checksum.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="8b032-112">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="8b032-112">Return Value</span></span>  
 <span data-ttu-id="8b032-113">`S_OK`, jeśli metoda została ukończona pomyślnie; w przeciwnym razie wartość HRESULT wskazująca niepowodzenie (zobacz [typowe wartości HRESULT](https://go.microsoft.com/fwlink/?LinkId=213878) dla listy).</span><span class="sxs-lookup"><span data-stu-id="8b032-113">`S_OK` if the method completed successfully; otherwise, an HRESULT value that indicates failure (see [Common HRESULT Values](https://go.microsoft.com/fwlink/?LinkId=213878) for a list).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8b032-114">Wymagania</span><span class="sxs-lookup"><span data-stu-id="8b032-114">Requirements</span></span>  
 <span data-ttu-id="8b032-115">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8b032-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8b032-116">**Nagłówek:** Obiekt ServiceHost. h</span><span class="sxs-lookup"><span data-stu-id="8b032-116">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="8b032-117">**Biblioteka:** Uwzględnione jako zasób w bibliotece MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="8b032-117">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="8b032-118">**Wersje .NET Framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8b032-118">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="8b032-119">Uwagi</span><span class="sxs-lookup"><span data-stu-id="8b032-119">Remarks</span></span>  
 <span data-ttu-id="8b032-120">Podpis silnej nazwy zestawu składa się z nazwy tekstu, wersji, kultury i tokenu klucza publicznego zestawu.</span><span class="sxs-lookup"><span data-stu-id="8b032-120">The strong name signature of an assembly consists of the assembly's text name, version, culture, and public key token.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8b032-121">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="8b032-121">See also</span></span>

- [<span data-ttu-id="8b032-122">ICLRStrongName, interfejs</span><span class="sxs-lookup"><span data-stu-id="8b032-122">ICLRStrongName Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
