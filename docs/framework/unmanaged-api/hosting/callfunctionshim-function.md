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
ms.openlocfilehash: e8945d40a3761ec51a73a8ae90ddc1d84ccab651
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/19/2020
ms.locfileid: "83616869"
---
# <a name="callfunctionshim-function"></a><span data-ttu-id="6c6a5-102">CallFunctionShim — Funkcja</span><span class="sxs-lookup"><span data-stu-id="6c6a5-102">CallFunctionShim Function</span></span>
<span data-ttu-id="6c6a5-103">Wywołuje funkcję, która ma określoną nazwę i parametry w określonej bibliotece.</span><span class="sxs-lookup"><span data-stu-id="6c6a5-103">Makes a call to the function that has the specified name and parameters in the specified library.</span></span>  
  
 <span data-ttu-id="6c6a5-104">Ta funkcja jest przestarzała w .NET Framework 4.</span><span class="sxs-lookup"><span data-stu-id="6c6a5-104">This function has been deprecated in the .NET Framework 4.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6c6a5-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="6c6a5-105">Syntax</span></span>  
  
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
  
## <a name="parameters"></a><span data-ttu-id="6c6a5-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="6c6a5-106">Parameters</span></span>  
 `szDllName`  
 <span data-ttu-id="6c6a5-107">podczas Nazwa biblioteki zawierającej funkcję.</span><span class="sxs-lookup"><span data-stu-id="6c6a5-107">[in] The name of the library containing the function.</span></span>  
  
 `szFunctionName`  
 <span data-ttu-id="6c6a5-108">podczas Nazwa funkcji.</span><span class="sxs-lookup"><span data-stu-id="6c6a5-108">[in] The name of the function.</span></span>  
  
 `lpvArgument1`  
 <span data-ttu-id="6c6a5-109">podczas Pierwszy argument do przekazania do funkcji.</span><span class="sxs-lookup"><span data-stu-id="6c6a5-109">[in] The first argument to pass to the function.</span></span>  
  
 `lpvArgument2`  
 <span data-ttu-id="6c6a5-110">podczas Drugi argument do przekazania do funkcji.</span><span class="sxs-lookup"><span data-stu-id="6c6a5-110">[in] The second argument to pass to the function.</span></span>  
  
 `szVersion`  
 <span data-ttu-id="6c6a5-111">podczas Wersja biblioteki, która zawiera funkcję.</span><span class="sxs-lookup"><span data-stu-id="6c6a5-111">[in] The version of the library that contains the function.</span></span>  
  
 `pvReserved`  
 <span data-ttu-id="6c6a5-112">podczas Zarezerwowane do użytku w przyszłości.</span><span class="sxs-lookup"><span data-stu-id="6c6a5-112">[in] Reserved for future use.</span></span> <span data-ttu-id="6c6a5-113">Przekaż zero w tym parametrze.</span><span class="sxs-lookup"><span data-stu-id="6c6a5-113">Pass zero in this parameter.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6c6a5-114">Wymagania</span><span class="sxs-lookup"><span data-stu-id="6c6a5-114">Requirements</span></span>  
 <span data-ttu-id="6c6a5-115">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6c6a5-115">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6c6a5-116">**Nagłówek:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="6c6a5-116">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="6c6a5-117">**Biblioteka:** MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="6c6a5-117">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="6c6a5-118">**.NET Framework wersje:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6c6a5-118">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6c6a5-119">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="6c6a5-119">See also</span></span>

- [<span data-ttu-id="6c6a5-120">Przestarzałe funkcje hostingu środowiska CLR</span><span class="sxs-lookup"><span data-stu-id="6c6a5-120">Deprecated CLR Hosting Functions</span></span>](deprecated-clr-hosting-functions.md)
