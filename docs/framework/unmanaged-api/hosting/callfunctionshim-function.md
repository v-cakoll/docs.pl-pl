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
ms.openlocfilehash: 31d93ac427ec67726c9456d623aeb683c9029ccd
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/10/2019
ms.locfileid: "67773763"
---
# <a name="callfunctionshim-function"></a><span data-ttu-id="2296d-102">CallFunctionShim — Funkcja</span><span class="sxs-lookup"><span data-stu-id="2296d-102">CallFunctionShim Function</span></span>
<span data-ttu-id="2296d-103">Wywołuje funkcję, która ma określoną nazwę i parametry w określonej bibliotece.</span><span class="sxs-lookup"><span data-stu-id="2296d-103">Makes a call to the function that has the specified name and parameters in the specified library.</span></span>  
  
 <span data-ttu-id="2296d-104">Ta funkcja jest przestarzała w programie .NET Framework 4.</span><span class="sxs-lookup"><span data-stu-id="2296d-104">This function has been deprecated in the .NET Framework 4.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2296d-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="2296d-105">Syntax</span></span>  
  
```cpp  
HRESULT CallFunctionShim (  
    [in] LPCWSTR     szDllName,  
    [in] LPCSTR      szFunctionName,  
    [in] LPVOID      lpvArgument1,  
    [in] LPVOID      lpvArgument2,  
    [in] LPCWSTR     szVersion,  
    [in] LPVOID      pvReserved  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="2296d-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="2296d-106">Parameters</span></span>  
 `szDllName`  
 <span data-ttu-id="2296d-107">[in] Nazwa biblioteki zawierający funkcję.</span><span class="sxs-lookup"><span data-stu-id="2296d-107">[in] The name of the library containing the function.</span></span>  
  
 `szFunctionName`  
 <span data-ttu-id="2296d-108">[in] Nazwa funkcji.</span><span class="sxs-lookup"><span data-stu-id="2296d-108">[in] The name of the function.</span></span>  
  
 `lpvArgument1`  
 <span data-ttu-id="2296d-109">[in] Pierwszy argument do przekazania do funkcji.</span><span class="sxs-lookup"><span data-stu-id="2296d-109">[in] The first argument to pass to the function.</span></span>  
  
 `lpvArgument2`  
 <span data-ttu-id="2296d-110">[in] Drugi argument do przekazania do funkcji.</span><span class="sxs-lookup"><span data-stu-id="2296d-110">[in] The second argument to pass to the function.</span></span>  
  
 `szVersion`  
 <span data-ttu-id="2296d-111">[in] Wersja biblioteki, która zawiera funkcję.</span><span class="sxs-lookup"><span data-stu-id="2296d-111">[in] The version of the library that contains the function.</span></span>  
  
 `pvReserved`  
 <span data-ttu-id="2296d-112">[in] Zarezerwowane do użytku w przyszłości.</span><span class="sxs-lookup"><span data-stu-id="2296d-112">[in] Reserved for future use.</span></span> <span data-ttu-id="2296d-113">Należy przekazać wartość zero, w tym parametrze.</span><span class="sxs-lookup"><span data-stu-id="2296d-113">Pass zero in this parameter.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2296d-114">Wymagania</span><span class="sxs-lookup"><span data-stu-id="2296d-114">Requirements</span></span>  
 <span data-ttu-id="2296d-115">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2296d-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2296d-116">**Nagłówek:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="2296d-116">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="2296d-117">**Biblioteka:** MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="2296d-117">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="2296d-118">**Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2296d-118">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2296d-119">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="2296d-119">See also</span></span>

- [<span data-ttu-id="2296d-120">Przestarzałe funkcje hostingu środowiska CLR</span><span class="sxs-lookup"><span data-stu-id="2296d-120">Deprecated CLR Hosting Functions</span></span>](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
