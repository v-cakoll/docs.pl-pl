---
title: ICorDebugMergedAssemblyRecord::Metoda GetCulture
ms.date: 03/30/2017
ms.assetid: 030b2f8c-8c21-40b7-855d-3afa78975a17
ms.openlocfilehash: ad54a93b16e803170987dd56d8063669f7e67f94
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79178754"
---
# <a name="icordebugmergedassemblyrecordgetculture-method"></a><span data-ttu-id="3a315-102">ICorDebugMergedAssemblyRecord::Metoda GetCulture</span><span class="sxs-lookup"><span data-stu-id="3a315-102">ICorDebugMergedAssemblyRecord::GetCulture Method</span></span>
<span data-ttu-id="3a315-103">Pobiera ciąg nazwy kultury zestawu.</span><span class="sxs-lookup"><span data-stu-id="3a315-103">Gets the culture name string of the assembly.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3a315-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="3a315-104">Syntax</span></span>  
  
```cpp  
HRESULT GetCulture(  
   [in] ULONG32 cchCulture,
   [out] ULONG32 *pcchCulture,
   [out, size_is(cchCulture), length_is(*pcchCulture)] WCHAR szCulture[]  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="3a315-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="3a315-105">Parameters</span></span>  
 `cchCulture`  
 <span data-ttu-id="3a315-106">[w] Liczba znaków w `szCulture` buforze.</span><span class="sxs-lookup"><span data-stu-id="3a315-106">[in] The number of characters in the `szCulture` buffer.</span></span>  
  
 `pcchCulture`  
 <span data-ttu-id="3a315-107">[na zewnątrz] Liczba znaków faktycznie zapisanych `szCulture` w buforze.</span><span class="sxs-lookup"><span data-stu-id="3a315-107">[out] The number of characters actually written to the `szCulture` buffer.</span></span>  
  
 `szCulture`  
 <span data-ttu-id="3a315-108">[na zewnątrz] Tablica znaków zawierająca nazwę kultury.</span><span class="sxs-lookup"><span data-stu-id="3a315-108">[out] A character array that contains the culture name.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="3a315-109">Uwagi</span><span class="sxs-lookup"><span data-stu-id="3a315-109">Remarks</span></span>  
 <span data-ttu-id="3a315-110">Nazwa kultury jest unikatowy ciąg, który identyfikuje kultury, takich jak "en-US" (dla kultury angielski (Stany Zjednoczone) lub "neutralny" (dla kultury neutralnej).</span><span class="sxs-lookup"><span data-stu-id="3a315-110">The culture name is a unique string that identifies a culture, such as "en-US" (for the English (United States) culture), or "neutral" (for a neutral culture).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="3a315-111">Ta metoda jest dostępna tylko w przypadku platformy .NET Native.</span><span class="sxs-lookup"><span data-stu-id="3a315-111">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3a315-112">Wymagania</span><span class="sxs-lookup"><span data-stu-id="3a315-112">Requirements</span></span>  
 <span data-ttu-id="3a315-113">**Platformy:** Zobacz [Wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3a315-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3a315-114">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="3a315-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="3a315-115">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="3a315-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="3a315-116">**Wersje programu .NET Framework:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3a315-116">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3a315-117">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="3a315-117">See also</span></span>

- [<span data-ttu-id="3a315-118">ICorDebugMergedAssemblyRecord, interfejs</span><span class="sxs-lookup"><span data-stu-id="3a315-118">ICorDebugMergedAssemblyRecord Interface</span></span>](icordebugmergedassemblyrecord-interface.md)
- [<span data-ttu-id="3a315-119">Debugowanie — Interfejsy</span><span class="sxs-lookup"><span data-stu-id="3a315-119">Debugging Interfaces</span></span>](debugging-interfaces.md)
