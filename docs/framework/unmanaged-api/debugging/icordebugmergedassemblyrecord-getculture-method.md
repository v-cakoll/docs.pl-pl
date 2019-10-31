---
title: 'ICorDebugMergedAssemblyRecord:: getculture — Metoda'
ms.date: 03/30/2017
ms.assetid: 030b2f8c-8c21-40b7-855d-3afa78975a17
ms.openlocfilehash: f39a1f17c80d27a38c0f2a8a516405f72c79bbcf
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73131425"
---
# <a name="icordebugmergedassemblyrecordgetculture-method"></a><span data-ttu-id="4f767-102">ICorDebugMergedAssemblyRecord:: getculture — Metoda</span><span class="sxs-lookup"><span data-stu-id="4f767-102">ICorDebugMergedAssemblyRecord::GetCulture Method</span></span>
<span data-ttu-id="4f767-103">Pobiera ciąg nazwy kultury zestawu.</span><span class="sxs-lookup"><span data-stu-id="4f767-103">Gets the culture name string of the assembly.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4f767-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="4f767-104">Syntax</span></span>  
  
```cpp  
HRESULT GetCulture(  
   [in] ULONG32 cchCulture,   
   [out] ULONG32 *pcchCulture,   
   [out, size_is(cchCulture), length_is(*pcchCulture)] WCHAR szCulture[]  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="4f767-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="4f767-105">Parameters</span></span>  
 `cchCulture`  
 <span data-ttu-id="4f767-106">podczas Liczba znaków w buforze `szCulture`.</span><span class="sxs-lookup"><span data-stu-id="4f767-106">[in] The number of characters in the `szCulture` buffer.</span></span>  
  
 `pcchCulture`  
 <span data-ttu-id="4f767-107">określoną Liczba znaków rzeczywiście zapisywana w buforze `szCulture`.</span><span class="sxs-lookup"><span data-stu-id="4f767-107">[out] The number of characters actually written to the `szCulture` buffer.</span></span>  
  
 `szCulture`  
 <span data-ttu-id="4f767-108">określoną Tablica znaków, która zawiera nazwę kultury.</span><span class="sxs-lookup"><span data-stu-id="4f767-108">[out] A character array that contains the culture name.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="4f767-109">Uwagi</span><span class="sxs-lookup"><span data-stu-id="4f767-109">Remarks</span></span>  
 <span data-ttu-id="4f767-110">Nazwa kultury jest unikatowym ciągiem, który identyfikuje kulturę, na przykład "en-US" (dla kultury angielskiej (Stany Zjednoczone)) lub "neutralną" (dla kultury neutralnej).</span><span class="sxs-lookup"><span data-stu-id="4f767-110">The culture name is a unique string that identifies a culture, such as "en-US" (for the English (United States) culture), or "neutral" (for a neutral culture).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="4f767-111">Ta metoda jest dostępna tylko z .NET Native.</span><span class="sxs-lookup"><span data-stu-id="4f767-111">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4f767-112">Wymagania</span><span class="sxs-lookup"><span data-stu-id="4f767-112">Requirements</span></span>  
 <span data-ttu-id="4f767-113">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4f767-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4f767-114">**Nagłówek:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="4f767-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="4f767-115">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="4f767-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="4f767-116">**Wersje .NET Framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4f767-116">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4f767-117">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="4f767-117">See also</span></span>

- [<span data-ttu-id="4f767-118">ICorDebugMergedAssemblyRecord, interfejs</span><span class="sxs-lookup"><span data-stu-id="4f767-118">ICorDebugMergedAssemblyRecord Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmergedassemblyrecord-interface.md)
- [<span data-ttu-id="4f767-119">Debugowanie, interfejsy</span><span class="sxs-lookup"><span data-stu-id="4f767-119">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
