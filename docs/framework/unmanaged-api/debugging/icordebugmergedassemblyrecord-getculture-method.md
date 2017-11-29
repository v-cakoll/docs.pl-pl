---
title: "ICorDebugMergedAssemblyRecord::GetCulture — metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: 030b2f8c-8c21-40b7-855d-3afa78975a17
caps.latest.revision: "4"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 7791491a050e31d8d6c5dfb6ef9ffe209921753d
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="icordebugmergedassemblyrecordgetculture-method"></a><span data-ttu-id="5da84-102">ICorDebugMergedAssemblyRecord::GetCulture — metoda</span><span class="sxs-lookup"><span data-stu-id="5da84-102">ICorDebugMergedAssemblyRecord::GetCulture Method</span></span>
<span data-ttu-id="5da84-103">Pobiera ciąg nazwy kultury zestawu.</span><span class="sxs-lookup"><span data-stu-id="5da84-103">Gets the culture name string of the assembly.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5da84-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="5da84-104">Syntax</span></span>  
  
```  
HRESULT GetCulture(  
   [in] ULONG32 cchCulture,   
   [out] ULONG32 *pcchCulture,   
   [out, size_is(cchCulture), length_is(*pcchCulture)] WCHAR szCulture[]  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="5da84-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="5da84-105">Parameters</span></span>  
 `cchCulture`  
 <span data-ttu-id="5da84-106">[in] Liczba znaków w `szCulture` buforu.</span><span class="sxs-lookup"><span data-stu-id="5da84-106">[in] The number of characters in the `szCulture` buffer.</span></span>  
  
 `pcchCulture`  
 <span data-ttu-id="5da84-107">[out] Liczba znaków, które faktycznie zapisane `szCulture` buforu.</span><span class="sxs-lookup"><span data-stu-id="5da84-107">[out] The number of characters actually written to the `szCulture` buffer.</span></span>  
  
 `szCulture`  
 <span data-ttu-id="5da84-108">[out] Tablica znaków, która zawiera nazwę kultury.</span><span class="sxs-lookup"><span data-stu-id="5da84-108">[out] A character array that contains the culture name.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="5da84-109">Uwagi</span><span class="sxs-lookup"><span data-stu-id="5da84-109">Remarks</span></span>  
 <span data-ttu-id="5da84-110">Nazwa kultury jest unikatowy ciąg identyfikujący kulturze, na przykład "en US" (dla kultury angielski (Stany Zjednoczone)) lub "neutralną" (dla kultury neutralnej).</span><span class="sxs-lookup"><span data-stu-id="5da84-110">The culture name is a unique string that identifies a culture, such as "en-US" (for the English (United States) culture), or "neutral" (for a neutral culture).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="5da84-111">Ta metoda jest tylko dostępne z platformą .NET Native.</span><span class="sxs-lookup"><span data-stu-id="5da84-111">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5da84-112">Wymagania</span><span class="sxs-lookup"><span data-stu-id="5da84-112">Requirements</span></span>  
 <span data-ttu-id="5da84-113">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5da84-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5da84-114">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="5da84-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="5da84-115">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="5da84-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="5da84-116">**Wersje programu .NET framework:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5da84-116">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5da84-117">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="5da84-117">See Also</span></span>  
 [<span data-ttu-id="5da84-118">Interfejs ICorDebugMergedAssemblyRecord</span><span class="sxs-lookup"><span data-stu-id="5da84-118">ICorDebugMergedAssemblyRecord Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmergedassemblyrecord-interface.md)  
 [<span data-ttu-id="5da84-119">Interfejsy debugowania</span><span class="sxs-lookup"><span data-stu-id="5da84-119">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
