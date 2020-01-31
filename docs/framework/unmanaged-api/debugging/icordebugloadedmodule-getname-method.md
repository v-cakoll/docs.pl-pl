---
title: ICorDebugLoadedModule::GetName — metoda
ms.date: 03/30/2017
ms.assetid: 88c304d5-edaa-4c0e-a8e1-144e8a76877e
ms.openlocfilehash: 628f85f3045533ead7ace47b11573a0b1a46df46
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/28/2020
ms.locfileid: "76782053"
---
# <a name="icordebugloadedmodulegetname-method"></a><span data-ttu-id="88443-102">ICorDebugLoadedModule::GetName — metoda</span><span class="sxs-lookup"><span data-stu-id="88443-102">ICorDebugLoadedModule::GetName Method</span></span>
<span data-ttu-id="88443-103">Pobiera nazwę załadowanego modułu.</span><span class="sxs-lookup"><span data-stu-id="88443-103">Gets the name of the loaded module.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="88443-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="88443-104">Syntax</span></span>  
  
```cpp  
HRESULT GetName(  
   [in] ULONG32 cchName,  
   [out] ULONG32 *pcchName,  
   [out, size_is(cchName),  
   length_is(*pcchName)] WCHAR szName[]  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="88443-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="88443-105">Parameters</span></span>  
 `cchName`  
 <span data-ttu-id="88443-106">podczas Liczba znaków w buforze `szName`.</span><span class="sxs-lookup"><span data-stu-id="88443-106">[in] The number of characters in the `szName` buffer.</span></span>  
  
 `pcchName`  
 <span data-ttu-id="88443-107">określoną Wskaźnik do liczby znaków rzeczywiście zapisywana w buforze `szName`.</span><span class="sxs-lookup"><span data-stu-id="88443-107">[out] A pointer to the number of characters actually written to the `szName` buffer.</span></span>  
  
 `szName`  
 <span data-ttu-id="88443-108">określoną Tablica znaków, która zawiera nazwę załadowanego modułu.</span><span class="sxs-lookup"><span data-stu-id="88443-108">[out] An array of characters that contain the name of the loaded module.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="88443-109">Uwagi</span><span class="sxs-lookup"><span data-stu-id="88443-109">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="88443-110">Ta metoda jest dostępna tylko z .NET Native.</span><span class="sxs-lookup"><span data-stu-id="88443-110">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="88443-111">Wymagania</span><span class="sxs-lookup"><span data-stu-id="88443-111">Requirements</span></span>  
 <span data-ttu-id="88443-112">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="88443-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="88443-113">**Nagłówek:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="88443-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="88443-114">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="88443-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="88443-115">**Wersje .NET Framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="88443-115">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="88443-116">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="88443-116">See also</span></span>

- [<span data-ttu-id="88443-117">ICorDebugLoadedModule, interfejs</span><span class="sxs-lookup"><span data-stu-id="88443-117">ICorDebugLoadedModule Interface</span></span>](icordebugloadedmodule-interface.md)
- [<span data-ttu-id="88443-118">Debugowanie, interfejsy</span><span class="sxs-lookup"><span data-stu-id="88443-118">Debugging Interfaces</span></span>](debugging-interfaces.md)
