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
ms.openlocfilehash: 336fba6defc00eb87fcfa7e6b1aaafa0fcb15691
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/06/2019
ms.locfileid: "57494210"
---
# <a name="rundll32shimw-function"></a><span data-ttu-id="d3627-102">RunDll32ShimW — Funkcja</span><span class="sxs-lookup"><span data-stu-id="d3627-102">RunDll32ShimW Function</span></span>
<span data-ttu-id="d3627-103">Wykonuje określone polecenie.</span><span class="sxs-lookup"><span data-stu-id="d3627-103">Executes the specified command.</span></span>  
  
 <span data-ttu-id="d3627-104">Ta funkcja jest przestarzała w [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)].</span><span class="sxs-lookup"><span data-stu-id="d3627-104">This function has been deprecated in the [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)].</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d3627-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="d3627-105">Syntax</span></span>  
  
```  
HRESULT RunDll32ShimW (  
    [in] HWND        hwnd,  
    [in] HINSTANCE   hinst,  
    [in] LPCWSTR     lpszCmdLine,  
    [in] int         nCmdShow  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d3627-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="d3627-106">Parameters</span></span>  
 `hwnd`  
 <span data-ttu-id="d3627-107">[in] Dojście do okna, w którym będą wyświetlane dane wyjściowe polecenia.</span><span class="sxs-lookup"><span data-stu-id="d3627-107">[in] A handle to a window in which the command output will be displayed.</span></span>  
  
 `hinst`  
 <span data-ttu-id="d3627-108">[in] Dojście do biblioteki, która zawiera polecenia.</span><span class="sxs-lookup"><span data-stu-id="d3627-108">[in] A handle to the library that contains the command.</span></span>  
  
 `lpszCmdLine`  
 <span data-ttu-id="d3627-109">[in] Ciąg, który określa polecenie do wykonania.</span><span class="sxs-lookup"><span data-stu-id="d3627-109">[in] A string that specifies the command to be executed.</span></span>  
  
 `nCmdShow`  
 <span data-ttu-id="d3627-110">[in] Liczba całkowita, która określa tryb wyświetlania w oknie danych wyjściowych.</span><span class="sxs-lookup"><span data-stu-id="d3627-110">[in] An integer that specifies the display mode for the output window.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d3627-111">Wymagania</span><span class="sxs-lookup"><span data-stu-id="d3627-111">Requirements</span></span>  
 <span data-ttu-id="d3627-112">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d3627-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d3627-113">**Nagłówek:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="d3627-113">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="d3627-114">**Biblioteka:** MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="d3627-114">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="d3627-115">**Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d3627-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d3627-116">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="d3627-116">See also</span></span>
- [<span data-ttu-id="d3627-117">Przestarzałe funkcje hostingu środowiska CLR</span><span class="sxs-lookup"><span data-stu-id="d3627-117">Deprecated CLR Hosting Functions</span></span>](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
