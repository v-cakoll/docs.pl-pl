---
title: RunDll32ShimW — Funkcja
ms.date: 03/30/2017
api_name:
- RunDll32ShimW
api_location:
- mscoree.dll
api_type:
- DLLExport
f1_keywords:
- RunDll32ShimW
helpviewer_keywords:
- RunDll32ShimW function [.NET Framework hosting]
ms.assetid: 9ea07b57-96e2-44df-8711-8fe6c119087f
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: ccfdf9ffab35f076b85c067c2b412020a5f541b2
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59231087"
---
# <a name="rundll32shimw-function"></a><span data-ttu-id="b2671-102">RunDll32ShimW — Funkcja</span><span class="sxs-lookup"><span data-stu-id="b2671-102">RunDll32ShimW Function</span></span>
<span data-ttu-id="b2671-103">Wykonuje określone polecenie.</span><span class="sxs-lookup"><span data-stu-id="b2671-103">Executes the specified command.</span></span>  
  
 <span data-ttu-id="b2671-104">Ta funkcja jest przestarzała w [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)].</span><span class="sxs-lookup"><span data-stu-id="b2671-104">This function has been deprecated in the [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)].</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b2671-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="b2671-105">Syntax</span></span>  
  
```  
HRESULT RunDll32ShimW (  
    [in] HWND        hwnd,  
    [in] HINSTANCE   hinst,  
    [in] LPCWSTR     lpszCmdLine,  
    [in] int         nCmdShow  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="b2671-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="b2671-106">Parameters</span></span>  
 `hwnd`  
 <span data-ttu-id="b2671-107">[in] Dojście do okna, w którym będą wyświetlane dane wyjściowe polecenia.</span><span class="sxs-lookup"><span data-stu-id="b2671-107">[in] A handle to a window in which the command output will be displayed.</span></span>  
  
 `hinst`  
 <span data-ttu-id="b2671-108">[in] Dojście do biblioteki, która zawiera polecenia.</span><span class="sxs-lookup"><span data-stu-id="b2671-108">[in] A handle to the library that contains the command.</span></span>  
  
 `lpszCmdLine`  
 <span data-ttu-id="b2671-109">[in] Ciąg, który określa polecenie do wykonania.</span><span class="sxs-lookup"><span data-stu-id="b2671-109">[in] A string that specifies the command to be executed.</span></span>  
  
 `nCmdShow`  
 <span data-ttu-id="b2671-110">[in] Liczba całkowita, która określa tryb wyświetlania w oknie danych wyjściowych.</span><span class="sxs-lookup"><span data-stu-id="b2671-110">[in] An integer that specifies the display mode for the output window.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b2671-111">Wymagania</span><span class="sxs-lookup"><span data-stu-id="b2671-111">Requirements</span></span>  
 <span data-ttu-id="b2671-112">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b2671-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b2671-113">**Nagłówek:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="b2671-113">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="b2671-114">**Biblioteka:** MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="b2671-114">**Library:** MSCorEE.dll</span></span>  
  
 **<span data-ttu-id="b2671-115">Wersje programu .NET framework:</span><span class="sxs-lookup"><span data-stu-id="b2671-115">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="b2671-116">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="b2671-116">See also</span></span>

- [<span data-ttu-id="b2671-117">Przestarzałe funkcje hostingu środowiska CLR</span><span class="sxs-lookup"><span data-stu-id="b2671-117">Deprecated CLR Hosting Functions</span></span>](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
