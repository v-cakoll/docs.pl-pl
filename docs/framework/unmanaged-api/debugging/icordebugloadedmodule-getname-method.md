---
title: ICorDebugLoadedModule::GetName — metoda
ms.date: 03/30/2017
ms.assetid: 88c304d5-edaa-4c0e-a8e1-144e8a76877e
ms.openlocfilehash: 4cf2c5c099de3d66878f09ff702a1cad6ddb8f57
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73122622"
---
# <a name="icordebugloadedmodulegetname-method"></a><span data-ttu-id="8be6d-102">ICorDebugLoadedModule::GetName — metoda</span><span class="sxs-lookup"><span data-stu-id="8be6d-102">ICorDebugLoadedModule::GetName Method</span></span>
<span data-ttu-id="8be6d-103">Pobiera nazwę załadowanego modułu.</span><span class="sxs-lookup"><span data-stu-id="8be6d-103">Gets the name of the loaded module.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8be6d-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="8be6d-104">Syntax</span></span>  
  
```cpp  
HRESULT GetName(  
   [in] ULONG32 cchName,  
   [out] ULONG32 *pcchName,  
   [out, size_is(cchName),  
   length_is(*pcchName)] WCHAR szName[]  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="8be6d-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="8be6d-105">Parameters</span></span>  
 `cchName`  
 <span data-ttu-id="8be6d-106">podczas Liczba znaków w buforze `szName`.</span><span class="sxs-lookup"><span data-stu-id="8be6d-106">[in] The number of characters in the `szName` buffer.</span></span>  
  
 `pcchName`  
 <span data-ttu-id="8be6d-107">określoną Wskaźnik do liczby znaków rzeczywiście zapisywana w buforze `szName`.</span><span class="sxs-lookup"><span data-stu-id="8be6d-107">[out] A pointer to the number of characters actually written to the `szName` buffer.</span></span>  
  
 `szName`  
 <span data-ttu-id="8be6d-108">określoną Tablica znaków, która zawiera nazwę załadowanego modułu.</span><span class="sxs-lookup"><span data-stu-id="8be6d-108">[out] An array of characters that contain the name of the loaded module.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="8be6d-109">Uwagi</span><span class="sxs-lookup"><span data-stu-id="8be6d-109">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="8be6d-110">Ta metoda jest dostępna tylko z .NET Native.</span><span class="sxs-lookup"><span data-stu-id="8be6d-110">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8be6d-111">Wymagania</span><span class="sxs-lookup"><span data-stu-id="8be6d-111">Requirements</span></span>  
 <span data-ttu-id="8be6d-112">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8be6d-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8be6d-113">**Nagłówek:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="8be6d-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="8be6d-114">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="8be6d-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="8be6d-115">**Wersje .NET Framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8be6d-115">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8be6d-116">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="8be6d-116">See also</span></span>

- [<span data-ttu-id="8be6d-117">ICorDebugLoadedModule, interfejs</span><span class="sxs-lookup"><span data-stu-id="8be6d-117">ICorDebugLoadedModule Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugloadedmodule-interface.md)
- [<span data-ttu-id="8be6d-118">Debugowanie, interfejsy</span><span class="sxs-lookup"><span data-stu-id="8be6d-118">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
