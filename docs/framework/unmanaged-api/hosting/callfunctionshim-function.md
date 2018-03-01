---
title: "CallFunctionShim — Funkcja"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- CallFunctionShim
api_location:
- mscoree.dll
api_type:
- DLLExport
f1_keywords:
- CallFunctionShim
helpviewer_keywords:
- CallfunctionShim function [.NET Framework hosting]
ms.assetid: 37118465-ddf3-41f0-bf27-335b72777e63
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 12c399c876a244d0c27e34b41e08c284d7429bac
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="callfunctionshim-function"></a><span data-ttu-id="74c12-102">CallFunctionShim — Funkcja</span><span class="sxs-lookup"><span data-stu-id="74c12-102">CallFunctionShim Function</span></span>
<span data-ttu-id="74c12-103">Wykonuje wywołanie funkcji, które ma określoną nazwę i parametrów w określonej bibliotece.</span><span class="sxs-lookup"><span data-stu-id="74c12-103">Makes a call to the function that has the specified name and parameters in the specified library.</span></span>  
  
 <span data-ttu-id="74c12-104">Ta funkcja jest przestarzała w [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)].</span><span class="sxs-lookup"><span data-stu-id="74c12-104">This function has been deprecated in the [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)].</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="74c12-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="74c12-105">Syntax</span></span>  
  
```  
HRESULT CallFunctionShim (  
    [in] LPCWSTR     szDllName,  
    [in] LPCSTR      szFunctionName,  
    [in] LPVOID      lpvArgument1,  
    [in] LPVOID      lpvArgument2,  
    [in] LPCWSTR     szVersion,  
    [in] LPVOID      pvReserved  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="74c12-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="74c12-106">Parameters</span></span>  
 `szDllName`  
 <span data-ttu-id="74c12-107">[in] Nazwa biblioteki zawierający funkcję.</span><span class="sxs-lookup"><span data-stu-id="74c12-107">[in] The name of the library containing the function.</span></span>  
  
 `szFunctionName`  
 <span data-ttu-id="74c12-108">[in] Nazwa funkcji.</span><span class="sxs-lookup"><span data-stu-id="74c12-108">[in] The name of the function.</span></span>  
  
 `lpvArgument1`  
 <span data-ttu-id="74c12-109">[in] Pierwszy argument do przekazania do funkcji.</span><span class="sxs-lookup"><span data-stu-id="74c12-109">[in] The first argument to pass to the function.</span></span>  
  
 `lpvArgument2`  
 <span data-ttu-id="74c12-110">[in] Drugi argument można przekazać do funkcji.</span><span class="sxs-lookup"><span data-stu-id="74c12-110">[in] The second argument to pass to the function.</span></span>  
  
 `szVersion`  
 <span data-ttu-id="74c12-111">[in] Wersja biblioteki, która zawiera funkcję.</span><span class="sxs-lookup"><span data-stu-id="74c12-111">[in] The version of the library that contains the function.</span></span>  
  
 `pvReserved`  
 <span data-ttu-id="74c12-112">[in] Zarezerwowane do użytku w przyszłości.</span><span class="sxs-lookup"><span data-stu-id="74c12-112">[in] Reserved for future use.</span></span> <span data-ttu-id="74c12-113">Przekaż zero w tym parametrze.</span><span class="sxs-lookup"><span data-stu-id="74c12-113">Pass zero in this parameter.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="74c12-114">Wymagania</span><span class="sxs-lookup"><span data-stu-id="74c12-114">Requirements</span></span>  
 <span data-ttu-id="74c12-115">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="74c12-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="74c12-116">**Nagłówek:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="74c12-116">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="74c12-117">**Biblioteka:** biblioteki MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="74c12-117">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="74c12-118">**Wersje programu .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="74c12-118">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="74c12-119">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="74c12-119">See Also</span></span>  
 [<span data-ttu-id="74c12-120">Przestarzałe funkcje hostingu środowiska CLR</span><span class="sxs-lookup"><span data-stu-id="74c12-120">Deprecated CLR Hosting Functions</span></span>](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
