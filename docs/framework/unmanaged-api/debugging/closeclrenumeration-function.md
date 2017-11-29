---
title: "CloseCLREnumeration — Funkcja"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: CloseCLREnumeration
api_location: dbgshim.dll
api_type: COM
f1_keywords: CloseCLREnumeration
helpviewer_keywords:
- debugging API [Silverlight]
- Silverlight, debugging
- CloseCLR Enumeration function
ms.assetid: 5e3c3958-80bb-43b1-a96b-dd3e6dbd9cd7
topic_type: apiref
caps.latest.revision: "4"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: d9f14b851795c92c3ce0c1e7536a4ff78fbdf927
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="closeclrenumeration-function"></a><span data-ttu-id="7349c-102">CloseCLREnumeration — Funkcja</span><span class="sxs-lookup"><span data-stu-id="7349c-102">CloseCLREnumeration Function</span></span>
<span data-ttu-id="7349c-103">Zamyka żadnych prawidłowy wspólnego języka środowiska uruchomieniowego (języka wspólnego CLR) kontynuować uruchamianie zdarzenia znajdujące się w tablicy dojść zwrócony przez [enumerateclrs — funkcja](../../../../docs/framework/unmanaged-api/debugging/enumerateclrs-function.md)i zwalnia pamięć dla tablic dojście i ciągu ścieżki.</span><span class="sxs-lookup"><span data-stu-id="7349c-103">Closes any valid common language runtime (CLR) continue-startup events located in an array of handles returned by the [EnumerateCLRs function](../../../../docs/framework/unmanaged-api/debugging/enumerateclrs-function.md), and frees the memory for the handle and string path arrays.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7349c-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="7349c-104">Syntax</span></span>  
  
```  
HRESULT CloseCLREnumeration (  
    [in]  DWORD      pHandleArray,  
    [in]  LPWSTR**   pStringArray,  
    [in]  DWORD*     dwArrayLength  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="7349c-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="7349c-105">Parameters</span></span>  
 `pHandleArray`  
 <span data-ttu-id="7349c-106">[in] Wskaźnik do tablicy uchwytów zdarzeń zwrócony z [enumerateclrs — funkcja](../../../../docs/framework/unmanaged-api/debugging/enumerateclrs-function.md).</span><span class="sxs-lookup"><span data-stu-id="7349c-106">[in] Pointer to the array of event handles returned from the [EnumerateCLRs function](../../../../docs/framework/unmanaged-api/debugging/enumerateclrs-function.md).</span></span>  
  
 `pStringArray`  
 <span data-ttu-id="7349c-107">[in] Wskaźnik do tablicy CLR ciąg ścieżki zwrócony z [enumerateclrs — funkcja](../../../../docs/framework/unmanaged-api/debugging/enumerateclrs-function.md).</span><span class="sxs-lookup"><span data-stu-id="7349c-107">[in] Pointer to the array of CLR string paths returned from the [EnumerateCLRs function](../../../../docs/framework/unmanaged-api/debugging/enumerateclrs-function.md).</span></span>  
  
 `dwArrayLength`  
 <span data-ttu-id="7349c-108">[in] DWORD zawierający rozmiaru (długość) albo `pHandleArray` lub `pStringArray` (są one takie same).</span><span class="sxs-lookup"><span data-stu-id="7349c-108">[in] DWORD that contains the size (length) of either `pHandleArray` or `pStringArray` (they are the same).</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="7349c-109">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="7349c-109">Return Value</span></span>  
 <span data-ttu-id="7349c-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="7349c-110">S_OK</span></span>  
 <span data-ttu-id="7349c-111">Uchwyty otwarty przez [enumerateclrs — funkcja](../../../../docs/framework/unmanaged-api/debugging/enumerateclrs-function.md) są zamknięte i zostanie zwolniona pamięć przydzielona dla tablic dojście i ciąg.</span><span class="sxs-lookup"><span data-stu-id="7349c-111">Handles opened by the [EnumerateCLRs function](../../../../docs/framework/unmanaged-api/debugging/enumerateclrs-function.md) are closed, and memory allocated for the handle and string arrays is freed.</span></span>  
  
 <span data-ttu-id="7349c-112">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="7349c-112">E_INVALIDARG</span></span>  
 <span data-ttu-id="7349c-113">Długość `pHandleArray` nie odpowiada długości, który jest przekazywany w `dwArrayLength`.</span><span class="sxs-lookup"><span data-stu-id="7349c-113">The length of `pHandleArray` does not match the length that is passed in `dwArrayLength`.</span></span>  
  
 <span data-ttu-id="7349c-114">E_FAIL (lub inne kody powrotu E_)</span><span class="sxs-lookup"><span data-stu-id="7349c-114">E_FAIL (or other E_ return codes)</span></span>  
 <span data-ttu-id="7349c-115">Nie można zwolnić pamięć jest funkcja `pHandleArray` i `pStringArray`.</span><span class="sxs-lookup"><span data-stu-id="7349c-115">The function is unable to free the memory for `pHandleArray` and `pStringArray`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7349c-116">Wymagania</span><span class="sxs-lookup"><span data-stu-id="7349c-116">Requirements</span></span>  
 <span data-ttu-id="7349c-117">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7349c-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7349c-118">**Nagłówek:** dbgshim.h</span><span class="sxs-lookup"><span data-stu-id="7349c-118">**Header:** dbgshim.h</span></span>  
  
 <span data-ttu-id="7349c-119">**Biblioteka:** biblioteki dbgshim.dll</span><span class="sxs-lookup"><span data-stu-id="7349c-119">**Library:** dbgshim.dll</span></span>  
  
 <span data-ttu-id="7349c-120">**Wersje programu .NET framework:** 3.5 z dodatkiem SP1</span><span class="sxs-lookup"><span data-stu-id="7349c-120">**.NET Framework Versions:** 3.5 SP1</span></span>
