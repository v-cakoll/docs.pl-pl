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
ms.openlocfilehash: 39223e10b0f75eefb83f3b9a83c5f030318cd715
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54738933"
---
# <a name="callfunctionshim-function"></a><span data-ttu-id="4b802-102">CallFunctionShim — Funkcja</span><span class="sxs-lookup"><span data-stu-id="4b802-102">CallFunctionShim Function</span></span>
<span data-ttu-id="4b802-103">Wywołuje funkcję, która ma określoną nazwę i parametry w określonej bibliotece.</span><span class="sxs-lookup"><span data-stu-id="4b802-103">Makes a call to the function that has the specified name and parameters in the specified library.</span></span>  
  
 <span data-ttu-id="4b802-104">Ta funkcja jest przestarzała w [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)].</span><span class="sxs-lookup"><span data-stu-id="4b802-104">This function has been deprecated in the [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)].</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4b802-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="4b802-105">Syntax</span></span>  
  
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
  
#### <a name="parameters"></a><span data-ttu-id="4b802-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="4b802-106">Parameters</span></span>  
 `szDllName`  
 <span data-ttu-id="4b802-107">[in] Nazwa biblioteki zawierający funkcję.</span><span class="sxs-lookup"><span data-stu-id="4b802-107">[in] The name of the library containing the function.</span></span>  
  
 `szFunctionName`  
 <span data-ttu-id="4b802-108">[in] Nazwa funkcji.</span><span class="sxs-lookup"><span data-stu-id="4b802-108">[in] The name of the function.</span></span>  
  
 `lpvArgument1`  
 <span data-ttu-id="4b802-109">[in] Pierwszy argument do przekazania do funkcji.</span><span class="sxs-lookup"><span data-stu-id="4b802-109">[in] The first argument to pass to the function.</span></span>  
  
 `lpvArgument2`  
 <span data-ttu-id="4b802-110">[in] Drugi argument do przekazania do funkcji.</span><span class="sxs-lookup"><span data-stu-id="4b802-110">[in] The second argument to pass to the function.</span></span>  
  
 `szVersion`  
 <span data-ttu-id="4b802-111">[in] Wersja biblioteki, która zawiera funkcję.</span><span class="sxs-lookup"><span data-stu-id="4b802-111">[in] The version of the library that contains the function.</span></span>  
  
 `pvReserved`  
 <span data-ttu-id="4b802-112">[in] Zarezerwowane do użytku w przyszłości.</span><span class="sxs-lookup"><span data-stu-id="4b802-112">[in] Reserved for future use.</span></span> <span data-ttu-id="4b802-113">Należy przekazać wartość zero, w tym parametrze.</span><span class="sxs-lookup"><span data-stu-id="4b802-113">Pass zero in this parameter.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4b802-114">Wymagania</span><span class="sxs-lookup"><span data-stu-id="4b802-114">Requirements</span></span>  
 <span data-ttu-id="4b802-115">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4b802-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4b802-116">**Nagłówek:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="4b802-116">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="4b802-117">**Biblioteka:** MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="4b802-117">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="4b802-118">**Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4b802-118">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4b802-119">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="4b802-119">See also</span></span>
- [<span data-ttu-id="4b802-120">Przestarzałe funkcje hostingu środowiska CLR</span><span class="sxs-lookup"><span data-stu-id="4b802-120">Deprecated CLR Hosting Functions</span></span>](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
