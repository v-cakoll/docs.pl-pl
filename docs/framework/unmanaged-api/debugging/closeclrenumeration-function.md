---
title: CloseCLREnumeration — Funkcja
ms.date: 03/30/2017
api_name:
- CloseCLREnumeration
api_location:
- dbgshim.dll
api_type:
- COM
f1_keywords:
- CloseCLREnumeration
helpviewer_keywords:
- debugging API [Silverlight]
- Silverlight, debugging
- CloseCLR Enumeration function
ms.assetid: 5e3c3958-80bb-43b1-a96b-dd3e6dbd9cd7
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 60b6d9c302cd3af9f41e5a8dce62d7eb268c4198
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61961177"
---
# <a name="closeclrenumeration-function"></a><span data-ttu-id="69e13-102">CloseCLREnumeration — Funkcja</span><span class="sxs-lookup"><span data-stu-id="69e13-102">CloseCLREnumeration Function</span></span>
<span data-ttu-id="69e13-103">Zamyka wszystkie prawidłowe typowe języka środowiska uruchomieniowego (języka wspólnego CLR) kontynuować uruchamianie zdarzenia znajdujące się w tablicy, uchwyt zwracany przez [enumerateclrs — funkcja](../../../../docs/framework/unmanaged-api/debugging/enumerateclrs-function.md)i zwalnia pamięć dla tablic ścieżka dojścia i parametry.</span><span class="sxs-lookup"><span data-stu-id="69e13-103">Closes any valid common language runtime (CLR) continue-startup events located in an array of handles returned by the [EnumerateCLRs function](../../../../docs/framework/unmanaged-api/debugging/enumerateclrs-function.md), and frees the memory for the handle and string path arrays.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="69e13-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="69e13-104">Syntax</span></span>  
  
```  
HRESULT CloseCLREnumeration (  
    [in]  DWORD      pHandleArray,  
    [in]  LPWSTR**   pStringArray,  
    [in]  DWORD*     dwArrayLength  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="69e13-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="69e13-105">Parameters</span></span>  
 `pHandleArray`  
 <span data-ttu-id="69e13-106">[in] Wskaźnik do tablicy uchwytów zdarzeń zwróciło [enumerateclrs — funkcja](../../../../docs/framework/unmanaged-api/debugging/enumerateclrs-function.md).</span><span class="sxs-lookup"><span data-stu-id="69e13-106">[in] Pointer to the array of event handles returned from the [EnumerateCLRs function](../../../../docs/framework/unmanaged-api/debugging/enumerateclrs-function.md).</span></span>  
  
 `pStringArray`  
 <span data-ttu-id="69e13-107">[in] Wskaźnik do tablicy CLR ciąg ścieżki zwróciło [enumerateclrs — funkcja](../../../../docs/framework/unmanaged-api/debugging/enumerateclrs-function.md).</span><span class="sxs-lookup"><span data-stu-id="69e13-107">[in] Pointer to the array of CLR string paths returned from the [EnumerateCLRs function](../../../../docs/framework/unmanaged-api/debugging/enumerateclrs-function.md).</span></span>  
  
 `dwArrayLength`  
 <span data-ttu-id="69e13-108">[in] DWORD, zawierający rozmiaru (o długości) albo `pHandleArray` lub `pStringArray` (są one takie same).</span><span class="sxs-lookup"><span data-stu-id="69e13-108">[in] DWORD that contains the size (length) of either `pHandleArray` or `pStringArray` (they are the same).</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="69e13-109">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="69e13-109">Return Value</span></span>  
 <span data-ttu-id="69e13-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="69e13-110">S_OK</span></span>  
 <span data-ttu-id="69e13-111">Uchwyty otwierane przez [enumerateclrs — funkcja](../../../../docs/framework/unmanaged-api/debugging/enumerateclrs-function.md) zostały zamknięte, i jest zwalniana pamięci przydzielonej dla tablic dojścia i parametry.</span><span class="sxs-lookup"><span data-stu-id="69e13-111">Handles opened by the [EnumerateCLRs function](../../../../docs/framework/unmanaged-api/debugging/enumerateclrs-function.md) are closed, and memory allocated for the handle and string arrays is freed.</span></span>  
  
 <span data-ttu-id="69e13-112">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="69e13-112">E_INVALIDARG</span></span>  
 <span data-ttu-id="69e13-113">Długość `pHandleArray` pasuje do długości, który jest przekazywany `dwArrayLength`.</span><span class="sxs-lookup"><span data-stu-id="69e13-113">The length of `pHandleArray` does not match the length that is passed in `dwArrayLength`.</span></span>  
  
 <span data-ttu-id="69e13-114">E_FAIL (lub inne kody powrotne e_)</span><span class="sxs-lookup"><span data-stu-id="69e13-114">E_FAIL (or other E_ return codes)</span></span>  
 <span data-ttu-id="69e13-115">Funkcja nie może zwolnić pamięć dla `pHandleArray` i `pStringArray`.</span><span class="sxs-lookup"><span data-stu-id="69e13-115">The function is unable to free the memory for `pHandleArray` and `pStringArray`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="69e13-116">Wymagania</span><span class="sxs-lookup"><span data-stu-id="69e13-116">Requirements</span></span>  
 <span data-ttu-id="69e13-117">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="69e13-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="69e13-118">**Nagłówek:** dbgshim.h</span><span class="sxs-lookup"><span data-stu-id="69e13-118">**Header:** dbgshim.h</span></span>  
  
 <span data-ttu-id="69e13-119">**Biblioteka:** dbgshim.dll</span><span class="sxs-lookup"><span data-stu-id="69e13-119">**Library:** dbgshim.dll</span></span>  
  
 <span data-ttu-id="69e13-120">**Wersje programu .NET framework:** 3.5 z dodatkiem SP1</span><span class="sxs-lookup"><span data-stu-id="69e13-120">**.NET Framework Versions:** 3.5 SP1</span></span>
