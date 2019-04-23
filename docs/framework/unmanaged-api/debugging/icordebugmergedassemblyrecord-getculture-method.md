---
title: ICorDebugMergedAssemblyRecord::GetCulture Method
ms.date: 03/30/2017
ms.assetid: 030b2f8c-8c21-40b7-855d-3afa78975a17
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 093b21a439b96c9fe2f971300f314d1b75527f1f
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59207204"
---
# <a name="icordebugmergedassemblyrecordgetculture-method"></a><span data-ttu-id="e9af8-102">ICorDebugMergedAssemblyRecord::GetCulture Method</span><span class="sxs-lookup"><span data-stu-id="e9af8-102">ICorDebugMergedAssemblyRecord::GetCulture Method</span></span>
<span data-ttu-id="e9af8-103">Pobiera ciąg nazwy kultury zestawu.</span><span class="sxs-lookup"><span data-stu-id="e9af8-103">Gets the culture name string of the assembly.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e9af8-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="e9af8-104">Syntax</span></span>  
  
```  
HRESULT GetCulture(  
   [in] ULONG32 cchCulture,   
   [out] ULONG32 *pcchCulture,   
   [out, size_is(cchCulture), length_is(*pcchCulture)] WCHAR szCulture[]  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="e9af8-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="e9af8-105">Parameters</span></span>  
 `cchCulture`  
 <span data-ttu-id="e9af8-106">[in] Liczba znaków w `szCulture` buforu.</span><span class="sxs-lookup"><span data-stu-id="e9af8-106">[in] The number of characters in the `szCulture` buffer.</span></span>  
  
 `pcchCulture`  
 <span data-ttu-id="e9af8-107">[out] Liczba znaków rzeczywiście zapisanych na `szCulture` buforu.</span><span class="sxs-lookup"><span data-stu-id="e9af8-107">[out] The number of characters actually written to the `szCulture` buffer.</span></span>  
  
 `szCulture`  
 <span data-ttu-id="e9af8-108">[out] Tablica znaków, który zawiera nazwę kultury.</span><span class="sxs-lookup"><span data-stu-id="e9af8-108">[out] A character array that contains the culture name.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="e9af8-109">Uwagi</span><span class="sxs-lookup"><span data-stu-id="e9af8-109">Remarks</span></span>  
 <span data-ttu-id="e9af8-110">Nazwa kultury jest unikatowy ciąg, który identyfikuje kultury, na przykład "en US" (w przypadku kultury angielski (Stany Zjednoczone)) lub "neutralnej" (dla kultury neutralnej).</span><span class="sxs-lookup"><span data-stu-id="e9af8-110">The culture name is a unique string that identifies a culture, such as "en-US" (for the English (United States) culture), or "neutral" (for a neutral culture).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="e9af8-111">Ta metoda jest tylko dostępne z architekturą .NET Native.</span><span class="sxs-lookup"><span data-stu-id="e9af8-111">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e9af8-112">Wymagania</span><span class="sxs-lookup"><span data-stu-id="e9af8-112">Requirements</span></span>  
 <span data-ttu-id="e9af8-113">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e9af8-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e9af8-114">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="e9af8-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="e9af8-115">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="e9af8-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="e9af8-116">**Wersje programu .NET framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e9af8-116">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e9af8-117">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="e9af8-117">See also</span></span>

- [<span data-ttu-id="e9af8-118">ICorDebugMergedAssemblyRecord, interfejs</span><span class="sxs-lookup"><span data-stu-id="e9af8-118">ICorDebugMergedAssemblyRecord Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmergedassemblyrecord-interface.md)
- [<span data-ttu-id="e9af8-119">Debugowanie, interfejsy</span><span class="sxs-lookup"><span data-stu-id="e9af8-119">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
