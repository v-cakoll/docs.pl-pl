---
title: "GetRealProcAddress — Funkcja"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: GetRealProcAddress
api_location: mscoree.dll
api_type: DLLExport
f1_keywords: GetRealProcAddress
helpviewer_keywords: GetRealProcAddress function [.NET Framework hosting]
ms.assetid: f1f2fab1-400b-488f-95f2-d49c4fca3556
topic_type: apiref
caps.latest.revision: "16"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 53e51bcf72f1a59f5c471564022d0d8c415381a6
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="getrealprocaddress-function"></a><span data-ttu-id="16627-102">GetRealProcAddress — Funkcja</span><span class="sxs-lookup"><span data-stu-id="16627-102">GetRealProcAddress Function</span></span>
<span data-ttu-id="16627-103">Pobiera adres określonej funkcji, który został wyeksportowany z najnowszej wersji zainstalowane środowisko uruchomieniowe języka wspólnego (CLR).</span><span class="sxs-lookup"><span data-stu-id="16627-103">Gets the address of the specified function that is exported from the latest installed version of the common language runtime (CLR).</span></span>  
  
 <span data-ttu-id="16627-104">Ta funkcja jest przestarzała w [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)].</span><span class="sxs-lookup"><span data-stu-id="16627-104">This function has been deprecated in the [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)].</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="16627-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="16627-105">Syntax</span></span>  
  
```  
HRESULT GetRealProcAddress (  
    [in]  LPCSTR  pwszProcName,   
    [out] VOID  **ppv  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="16627-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="16627-106">Parameters</span></span>  
 `pwszProcName`  
 <span data-ttu-id="16627-107">[in] Nazwa funkcji.</span><span class="sxs-lookup"><span data-stu-id="16627-107">[in] The name of the function.</span></span>  
  
 `ppv`  
 <span data-ttu-id="16627-108">[out] Lokalizacja odbierająca wskaźnik do adresu funkcji.</span><span class="sxs-lookup"><span data-stu-id="16627-108">[out] The location that receives a pointer to the address of the function.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="16627-109">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="16627-109">Return Value</span></span>  
 <span data-ttu-id="16627-110">Ta metoda zwraca standardowy składnik modelu COM. kody błędów, zgodnie z definicją w pliku WinError.h oprócz następujących wartości zdefiniowane w CorError.h.</span><span class="sxs-lookup"><span data-stu-id="16627-110">This method returns standard Component Object Model (COM) error codes, as defined in WinError.h, in addition to the following values defined in CorError.h.</span></span>  
  
|<span data-ttu-id="16627-111">Kod powrotu</span><span class="sxs-lookup"><span data-stu-id="16627-111">Return code</span></span>|<span data-ttu-id="16627-112">Opis</span><span class="sxs-lookup"><span data-stu-id="16627-112">Description</span></span>|  
|-----------------|-----------------|  
|<span data-ttu-id="16627-113">S_OK</span><span class="sxs-lookup"><span data-stu-id="16627-113">S_OK</span></span>|<span data-ttu-id="16627-114">Metoda została ukończona pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="16627-114">The method completed successfully.</span></span>|  
|<span data-ttu-id="16627-115">E_POINTER</span><span class="sxs-lookup"><span data-stu-id="16627-115">E_POINTER</span></span>|<span data-ttu-id="16627-116">`ppv`nie jest prawidłowy.</span><span class="sxs-lookup"><span data-stu-id="16627-116">`ppv` is not valid.</span></span>|  
|<span data-ttu-id="16627-117">CLR_E_SHIM_RUNTIMEEXPORT</span><span class="sxs-lookup"><span data-stu-id="16627-117">CLR_E_SHIM_RUNTIMEEXPORT</span></span>|<span data-ttu-id="16627-118">Funkcja nie są eksportowane z środowiska uruchomieniowego.</span><span class="sxs-lookup"><span data-stu-id="16627-118">The function is not exported from the runtime.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="16627-119">Wymagania</span><span class="sxs-lookup"><span data-stu-id="16627-119">Requirements</span></span>  
 <span data-ttu-id="16627-120">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="16627-120">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="16627-121">**Nagłówek:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="16627-121">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="16627-122">**Biblioteka:** biblioteki MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="16627-122">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="16627-123">**Wersje programu .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="16627-123">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="16627-124">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="16627-124">See Also</span></span>  
 [<span data-ttu-id="16627-125">Przestarzałe funkcje hostingu środowiska CLR.</span><span class="sxs-lookup"><span data-stu-id="16627-125">Deprecated CLR Hosting Functions</span></span>](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
