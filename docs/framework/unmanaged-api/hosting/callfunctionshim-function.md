---
title: CallFunctionShim — Funkcja
ms.date: 03/30/2017
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 7aeb813cafbf5b18739c4574c386398ac3c7a77b
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59180482"
---
# <a name="callfunctionshim-function"></a><span data-ttu-id="99e8a-102">CallFunctionShim — Funkcja</span><span class="sxs-lookup"><span data-stu-id="99e8a-102">CallFunctionShim Function</span></span>
<span data-ttu-id="99e8a-103">Wywołuje funkcję, która ma określoną nazwę i parametry w określonej bibliotece.</span><span class="sxs-lookup"><span data-stu-id="99e8a-103">Makes a call to the function that has the specified name and parameters in the specified library.</span></span>  
  
 <span data-ttu-id="99e8a-104">Ta funkcja jest przestarzała w [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)].</span><span class="sxs-lookup"><span data-stu-id="99e8a-104">This function has been deprecated in the [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)].</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="99e8a-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="99e8a-105">Syntax</span></span>  
  
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
  
## <a name="parameters"></a><span data-ttu-id="99e8a-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="99e8a-106">Parameters</span></span>  
 `szDllName`  
 <span data-ttu-id="99e8a-107">[in] Nazwa biblioteki zawierający funkcję.</span><span class="sxs-lookup"><span data-stu-id="99e8a-107">[in] The name of the library containing the function.</span></span>  
  
 `szFunctionName`  
 <span data-ttu-id="99e8a-108">[in] Nazwa funkcji.</span><span class="sxs-lookup"><span data-stu-id="99e8a-108">[in] The name of the function.</span></span>  
  
 `lpvArgument1`  
 <span data-ttu-id="99e8a-109">[in] Pierwszy argument do przekazania do funkcji.</span><span class="sxs-lookup"><span data-stu-id="99e8a-109">[in] The first argument to pass to the function.</span></span>  
  
 `lpvArgument2`  
 <span data-ttu-id="99e8a-110">[in] Drugi argument do przekazania do funkcji.</span><span class="sxs-lookup"><span data-stu-id="99e8a-110">[in] The second argument to pass to the function.</span></span>  
  
 `szVersion`  
 <span data-ttu-id="99e8a-111">[in] Wersja biblioteki, która zawiera funkcję.</span><span class="sxs-lookup"><span data-stu-id="99e8a-111">[in] The version of the library that contains the function.</span></span>  
  
 `pvReserved`  
 <span data-ttu-id="99e8a-112">[in] Zarezerwowane do użytku w przyszłości.</span><span class="sxs-lookup"><span data-stu-id="99e8a-112">[in] Reserved for future use.</span></span> <span data-ttu-id="99e8a-113">Należy przekazać wartość zero, w tym parametrze.</span><span class="sxs-lookup"><span data-stu-id="99e8a-113">Pass zero in this parameter.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="99e8a-114">Wymagania</span><span class="sxs-lookup"><span data-stu-id="99e8a-114">Requirements</span></span>  
 <span data-ttu-id="99e8a-115">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="99e8a-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="99e8a-116">**Nagłówek:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="99e8a-116">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="99e8a-117">**Biblioteka:** MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="99e8a-117">**Library:** MSCorEE.dll</span></span>  
  
 **<span data-ttu-id="99e8a-118">Wersje programu .NET framework:</span><span class="sxs-lookup"><span data-stu-id="99e8a-118">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="99e8a-119">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="99e8a-119">See also</span></span>

- [<span data-ttu-id="99e8a-120">Przestarzałe funkcje hostingu środowiska CLR</span><span class="sxs-lookup"><span data-stu-id="99e8a-120">Deprecated CLR Hosting Functions</span></span>](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
