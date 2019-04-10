---
title: GetRequestedRuntimeVersion — Funkcja
ms.date: 03/30/2017
api_name:
- GetRequestedRuntimeVersion
api_location:
- mscoree.dll
- mscoreei.dll
api_type:
- DLLExport
f1_keywords:
- GetRequestedRuntimeVersion
helpviewer_keywords:
- GetRequestedRuntimeVersion function [.NET Framework hosting]
ms.assetid: 82f596a4-483d-4509-b0c5-a84c53c3da1b
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 1ee737f4c6d34e77996f5ba08ce4d84132a99238
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59207334"
---
# <a name="getrequestedruntimeversion-function"></a><span data-ttu-id="69d51-102">GetRequestedRuntimeVersion — Funkcja</span><span class="sxs-lookup"><span data-stu-id="69d51-102">GetRequestedRuntimeVersion Function</span></span>
<span data-ttu-id="69d51-103">Pobiera numer wersji środowisko uruchomieniowe języka wspólnego (CLR) wymagane przez określoną aplikację.</span><span class="sxs-lookup"><span data-stu-id="69d51-103">Gets the version number of the common language runtime (CLR) requested by the specified application.</span></span> <span data-ttu-id="69d51-104">Jeśli ta wersja nie jest zainstalowana, pobiera najbardziej aktualną wersję zainstalowaną przed żądaną wersją.</span><span class="sxs-lookup"><span data-stu-id="69d51-104">If that version is not installed, gets the most recent version that is installed before the requested version.</span></span>  
  
 <span data-ttu-id="69d51-105">Ta funkcja jest przestarzała w [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)].</span><span class="sxs-lookup"><span data-stu-id="69d51-105">This function has been deprecated in the [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)].</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="69d51-106">Składnia</span><span class="sxs-lookup"><span data-stu-id="69d51-106">Syntax</span></span>  
  
```  
HRESULT GetRequestedRuntimeVersion (  
    [in]  LPWSTR  pExe,   
    [out] LPWSTR  pVersion,   
    [in]  DWORD   cchBuffer,   
    [out] DWORD  *pdwLength  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="69d51-107">Parametry</span><span class="sxs-lookup"><span data-stu-id="69d51-107">Parameters</span></span>  
 `pExe`  
 <span data-ttu-id="69d51-108">[in] Nazwa aplikacji.</span><span class="sxs-lookup"><span data-stu-id="69d51-108">[in] The name of the application.</span></span>  
  
 `pVersion`  
 <span data-ttu-id="69d51-109">[out] Bufor, który zawiera ciąg numeru wersji, po pomyślnym zakończeniu.</span><span class="sxs-lookup"><span data-stu-id="69d51-109">[out] A buffer that contains the version number string upon successful completion.</span></span>  
  
 `cchBuffer`  
 <span data-ttu-id="69d51-110">[in] Długość buforu wersji.</span><span class="sxs-lookup"><span data-stu-id="69d51-110">[in] The length of the version buffer.</span></span>  
  
 `pdwLength`  
 <span data-ttu-id="69d51-111">[out] Wskaźnik do długości ciągu numeru wersji.</span><span class="sxs-lookup"><span data-stu-id="69d51-111">[out] A pointer to the length of the version number string.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="69d51-112">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="69d51-112">Return Value</span></span>  
 <span data-ttu-id="69d51-113">Ta metoda zwraca standardowe kody błędów Component Object Model (COM), zgodnie z definicją w pliku WinError.h oprócz następujących wartości.</span><span class="sxs-lookup"><span data-stu-id="69d51-113">This method returns standard Component Object Model (COM) error codes, as defined in WinError.h, in addition to the following values.</span></span>  
  
|<span data-ttu-id="69d51-114">Kod powrotu</span><span class="sxs-lookup"><span data-stu-id="69d51-114">Return code</span></span>|<span data-ttu-id="69d51-115">Opis</span><span class="sxs-lookup"><span data-stu-id="69d51-115">Description</span></span>|  
|-----------------|-----------------|  
|<span data-ttu-id="69d51-116">S_OK</span><span class="sxs-lookup"><span data-stu-id="69d51-116">S_OK</span></span>|<span data-ttu-id="69d51-117">Metoda została ukończona pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="69d51-117">The method completed successfully.</span></span>|  
|<span data-ttu-id="69d51-118">ERROR_INSUFFICIENT_BUFFER</span><span class="sxs-lookup"><span data-stu-id="69d51-118">ERROR_INSUFFICIENT_BUFFER</span></span>|<span data-ttu-id="69d51-119">Bufor wersji nie jest wystarczająco duży, aby zapisać ciąg wersji.</span><span class="sxs-lookup"><span data-stu-id="69d51-119">The version buffer is not large enough to store the version string.</span></span>|  
|<span data-ttu-id="69d51-120">E_POINTER</span><span class="sxs-lookup"><span data-stu-id="69d51-120">E_POINTER</span></span>|`pdwLength` <span data-ttu-id="69d51-121">ma wartość null.</span><span class="sxs-lookup"><span data-stu-id="69d51-121">is null.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="69d51-122">Wymagania</span><span class="sxs-lookup"><span data-stu-id="69d51-122">Requirements</span></span>  
 <span data-ttu-id="69d51-123">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="69d51-123">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="69d51-124">**Nagłówek:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="69d51-124">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="69d51-125">**Biblioteka:** MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="69d51-125">**Library:** MSCorEE.dll</span></span>  
  
 **<span data-ttu-id="69d51-126">Wersje programu .NET framework:</span><span class="sxs-lookup"><span data-stu-id="69d51-126">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v11plus](../../../../includes/net-current-v11plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="69d51-127">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="69d51-127">See also</span></span>

- [<span data-ttu-id="69d51-128">GetRequestedRuntimeInfo — Funkcja</span><span class="sxs-lookup"><span data-stu-id="69d51-128">GetRequestedRuntimeInfo Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/getrequestedruntimeinfo-function.md)
- [<span data-ttu-id="69d51-129">GetVersionFromProcess — Funkcja</span><span class="sxs-lookup"><span data-stu-id="69d51-129">GetVersionFromProcess Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/getversionfromprocess-function.md)
- [<span data-ttu-id="69d51-130">Przestarzałe funkcje hostingu środowiska CLR</span><span class="sxs-lookup"><span data-stu-id="69d51-130">Deprecated CLR Hosting Functions</span></span>](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
