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
ms.workload: dotnet
ms.openlocfilehash: 7963d311707d12aa697c606605f9a34b6f65d1eb
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugmergedassemblyrecordgetculture-method"></a><span data-ttu-id="a615e-102">ICorDebugMergedAssemblyRecord::GetCulture — metoda</span><span class="sxs-lookup"><span data-stu-id="a615e-102">ICorDebugMergedAssemblyRecord::GetCulture Method</span></span>
<span data-ttu-id="a615e-103">Pobiera ciąg nazwy kultury zestawu.</span><span class="sxs-lookup"><span data-stu-id="a615e-103">Gets the culture name string of the assembly.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a615e-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="a615e-104">Syntax</span></span>  
  
```  
HRESULT GetCulture(  
   [in] ULONG32 cchCulture,   
   [out] ULONG32 *pcchCulture,   
   [out, size_is(cchCulture), length_is(*pcchCulture)] WCHAR szCulture[]  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="a615e-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="a615e-105">Parameters</span></span>  
 `cchCulture`  
 <span data-ttu-id="a615e-106">[in] Liczba znaków w `szCulture` buforu.</span><span class="sxs-lookup"><span data-stu-id="a615e-106">[in] The number of characters in the `szCulture` buffer.</span></span>  
  
 `pcchCulture`  
 <span data-ttu-id="a615e-107">[out] Liczba znaków, które faktycznie zapisane `szCulture` buforu.</span><span class="sxs-lookup"><span data-stu-id="a615e-107">[out] The number of characters actually written to the `szCulture` buffer.</span></span>  
  
 `szCulture`  
 <span data-ttu-id="a615e-108">[out] Tablica znaków, która zawiera nazwę kultury.</span><span class="sxs-lookup"><span data-stu-id="a615e-108">[out] A character array that contains the culture name.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="a615e-109">Uwagi</span><span class="sxs-lookup"><span data-stu-id="a615e-109">Remarks</span></span>  
 <span data-ttu-id="a615e-110">Nazwa kultury jest unikatowy ciąg identyfikujący kulturze, na przykład "en US" (dla kultury angielski (Stany Zjednoczone)) lub "neutralną" (dla kultury neutralnej).</span><span class="sxs-lookup"><span data-stu-id="a615e-110">The culture name is a unique string that identifies a culture, such as "en-US" (for the English (United States) culture), or "neutral" (for a neutral culture).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="a615e-111">Ta metoda jest tylko dostępne z platformą .NET Native.</span><span class="sxs-lookup"><span data-stu-id="a615e-111">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a615e-112">Wymagania</span><span class="sxs-lookup"><span data-stu-id="a615e-112">Requirements</span></span>  
 <span data-ttu-id="a615e-113">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a615e-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a615e-114">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="a615e-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="a615e-115">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="a615e-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="a615e-116">**Wersje programu .NET framework:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a615e-116">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a615e-117">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="a615e-117">See Also</span></span>  
 [<span data-ttu-id="a615e-118">ICorDebugMergedAssemblyRecord, interfejs</span><span class="sxs-lookup"><span data-stu-id="a615e-118">ICorDebugMergedAssemblyRecord Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmergedassemblyrecord-interface.md)  
 [<span data-ttu-id="a615e-119">Debugowanie, interfejsy</span><span class="sxs-lookup"><span data-stu-id="a615e-119">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
