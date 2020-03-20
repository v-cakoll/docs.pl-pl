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
ms.openlocfilehash: 6be0bc5d08f612dcb8ed7d256711e0c4367b9274
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79178135"
---
# <a name="getrequestedruntimeversion-function"></a><span data-ttu-id="343d0-102">GetRequestedRuntimeVersion — Funkcja</span><span class="sxs-lookup"><span data-stu-id="343d0-102">GetRequestedRuntimeVersion Function</span></span>
<span data-ttu-id="343d0-103">Pobiera numer wersji środowiska wykonawczego języka wspólnego (CLR) wymagane przez określoną aplikację.</span><span class="sxs-lookup"><span data-stu-id="343d0-103">Gets the version number of the common language runtime (CLR) requested by the specified application.</span></span> <span data-ttu-id="343d0-104">Jeśli ta wersja nie jest zainstalowana, pobiera najnowszą wersję, która jest zainstalowana przed żądaną wersją.</span><span class="sxs-lookup"><span data-stu-id="343d0-104">If that version is not installed, gets the most recent version that is installed before the requested version.</span></span>  
  
 <span data-ttu-id="343d0-105">Ta funkcja została przestarzała w .NET Framework 4.</span><span class="sxs-lookup"><span data-stu-id="343d0-105">This function has been deprecated in the .NET Framework 4.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="343d0-106">Składnia</span><span class="sxs-lookup"><span data-stu-id="343d0-106">Syntax</span></span>  
  
```cpp  
HRESULT GetRequestedRuntimeVersion (  
    [in]  LPWSTR  pExe,
    [out] LPWSTR  pVersion,
    [in]  DWORD   cchBuffer,
    [out] DWORD  *pdwLength  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="343d0-107">Parametry</span><span class="sxs-lookup"><span data-stu-id="343d0-107">Parameters</span></span>  
 `pExe`  
 <span data-ttu-id="343d0-108">[w] Nazwa aplikacji.</span><span class="sxs-lookup"><span data-stu-id="343d0-108">[in] The name of the application.</span></span>  
  
 `pVersion`  
 <span data-ttu-id="343d0-109">[na zewnątrz] Bufor, który zawiera ciąg numeru wersji po pomyślnym zakończeniu.</span><span class="sxs-lookup"><span data-stu-id="343d0-109">[out] A buffer that contains the version number string upon successful completion.</span></span>  
  
 `cchBuffer`  
 <span data-ttu-id="343d0-110">[w] Długość buforu wersji.</span><span class="sxs-lookup"><span data-stu-id="343d0-110">[in] The length of the version buffer.</span></span>  
  
 `pdwLength`  
 <span data-ttu-id="343d0-111">[na zewnątrz] Wskaźnik do długości ciągu numeru wersji.</span><span class="sxs-lookup"><span data-stu-id="343d0-111">[out] A pointer to the length of the version number string.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="343d0-112">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="343d0-112">Return Value</span></span>  
 <span data-ttu-id="343d0-113">Ta metoda zwraca standardowe kody błędów modelu com (Component Object Model), zgodnie z definicją w pliku WinError.h, oprócz następujących wartości.</span><span class="sxs-lookup"><span data-stu-id="343d0-113">This method returns standard Component Object Model (COM) error codes, as defined in WinError.h, in addition to the following values.</span></span>  
  
|<span data-ttu-id="343d0-114">Kod powrotu</span><span class="sxs-lookup"><span data-stu-id="343d0-114">Return code</span></span>|<span data-ttu-id="343d0-115">Opis</span><span class="sxs-lookup"><span data-stu-id="343d0-115">Description</span></span>|  
|-----------------|-----------------|  
|<span data-ttu-id="343d0-116">S_OK</span><span class="sxs-lookup"><span data-stu-id="343d0-116">S_OK</span></span>|<span data-ttu-id="343d0-117">Metoda została ukończona pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="343d0-117">The method completed successfully.</span></span>|  
|<span data-ttu-id="343d0-118">ERROR_INSUFFICIENT_BUFFER</span><span class="sxs-lookup"><span data-stu-id="343d0-118">ERROR_INSUFFICIENT_BUFFER</span></span>|<span data-ttu-id="343d0-119">Bufor wersji nie jest wystarczająco duży, aby przechowywać ciąg wersji.</span><span class="sxs-lookup"><span data-stu-id="343d0-119">The version buffer is not large enough to store the version string.</span></span>|  
|<span data-ttu-id="343d0-120">E_pointer</span><span class="sxs-lookup"><span data-stu-id="343d0-120">E_POINTER</span></span>|<span data-ttu-id="343d0-121">`pdwLength`ma wartość null.</span><span class="sxs-lookup"><span data-stu-id="343d0-121">`pdwLength` is null.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="343d0-122">Wymagania</span><span class="sxs-lookup"><span data-stu-id="343d0-122">Requirements</span></span>  
 <span data-ttu-id="343d0-123">**Platformy:** Zobacz [Wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="343d0-123">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="343d0-124">**Nagłówek:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="343d0-124">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="343d0-125">**Biblioteka:** Mscoree.dll</span><span class="sxs-lookup"><span data-stu-id="343d0-125">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="343d0-126">**Wersje programu .NET Framework:**[!INCLUDE[net_current_v11plus](../../../../includes/net-current-v11plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="343d0-126">**.NET Framework Versions:** [!INCLUDE[net_current_v11plus](../../../../includes/net-current-v11plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="343d0-127">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="343d0-127">See also</span></span>

- [<span data-ttu-id="343d0-128">GetRequestedRuntimeInfo, funkcja</span><span class="sxs-lookup"><span data-stu-id="343d0-128">GetRequestedRuntimeInfo Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/getrequestedruntimeinfo-function.md)
- [<span data-ttu-id="343d0-129">GetVersionFromProcess, funkcja</span><span class="sxs-lookup"><span data-stu-id="343d0-129">GetVersionFromProcess Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/getversionfromprocess-function.md)
- [<span data-ttu-id="343d0-130">Przestarzałe funkcje hostingu środowiska CLR</span><span class="sxs-lookup"><span data-stu-id="343d0-130">Deprecated CLR Hosting Functions</span></span>](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
