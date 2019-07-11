---
title: ICorDebugMergedAssemblyRecord::GetCulture Method
ms.date: 03/30/2017
ms.assetid: 030b2f8c-8c21-40b7-855d-3afa78975a17
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 0472a52d0893bfd487cd6daa6548ec1ce0c44a9b
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/10/2019
ms.locfileid: "67762207"
---
# <a name="icordebugmergedassemblyrecordgetculture-method"></a><span data-ttu-id="99817-102">ICorDebugMergedAssemblyRecord::GetCulture Method</span><span class="sxs-lookup"><span data-stu-id="99817-102">ICorDebugMergedAssemblyRecord::GetCulture Method</span></span>
<span data-ttu-id="99817-103">Pobiera ciąg nazwy kultury zestawu.</span><span class="sxs-lookup"><span data-stu-id="99817-103">Gets the culture name string of the assembly.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="99817-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="99817-104">Syntax</span></span>  
  
```cpp  
HRESULT GetCulture(  
   [in] ULONG32 cchCulture,   
   [out] ULONG32 *pcchCulture,   
   [out, size_is(cchCulture), length_is(*pcchCulture)] WCHAR szCulture[]  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="99817-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="99817-105">Parameters</span></span>  
 `cchCulture`  
 <span data-ttu-id="99817-106">[in] Liczba znaków w `szCulture` buforu.</span><span class="sxs-lookup"><span data-stu-id="99817-106">[in] The number of characters in the `szCulture` buffer.</span></span>  
  
 `pcchCulture`  
 <span data-ttu-id="99817-107">[out] Liczba znaków rzeczywiście zapisanych na `szCulture` buforu.</span><span class="sxs-lookup"><span data-stu-id="99817-107">[out] The number of characters actually written to the `szCulture` buffer.</span></span>  
  
 `szCulture`  
 <span data-ttu-id="99817-108">[out] Tablica znaków, który zawiera nazwę kultury.</span><span class="sxs-lookup"><span data-stu-id="99817-108">[out] A character array that contains the culture name.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="99817-109">Uwagi</span><span class="sxs-lookup"><span data-stu-id="99817-109">Remarks</span></span>  
 <span data-ttu-id="99817-110">Nazwa kultury jest unikatowy ciąg, który identyfikuje kultury, na przykład "en US" (w przypadku kultury angielski (Stany Zjednoczone)) lub "neutralnej" (dla kultury neutralnej).</span><span class="sxs-lookup"><span data-stu-id="99817-110">The culture name is a unique string that identifies a culture, such as "en-US" (for the English (United States) culture), or "neutral" (for a neutral culture).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="99817-111">Ta metoda jest tylko dostępne z architekturą .NET Native.</span><span class="sxs-lookup"><span data-stu-id="99817-111">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="99817-112">Wymagania</span><span class="sxs-lookup"><span data-stu-id="99817-112">Requirements</span></span>  
 <span data-ttu-id="99817-113">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="99817-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="99817-114">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="99817-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="99817-115">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="99817-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="99817-116">**Wersje programu .NET framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="99817-116">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="99817-117">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="99817-117">See also</span></span>

- [<span data-ttu-id="99817-118">ICorDebugMergedAssemblyRecord, interfejs</span><span class="sxs-lookup"><span data-stu-id="99817-118">ICorDebugMergedAssemblyRecord Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmergedassemblyrecord-interface.md)
- [<span data-ttu-id="99817-119">Debugowanie, interfejsy</span><span class="sxs-lookup"><span data-stu-id="99817-119">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
