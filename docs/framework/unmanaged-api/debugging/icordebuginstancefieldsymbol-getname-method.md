---
title: 'ICorDebugInstanceFieldSymbol:: GetName — Metoda'
ms.date: 03/30/2017
ms.assetid: d9c12b1f-9c1d-4943-8e9e-93b55faf085f
ms.openlocfilehash: d88e18b8d6d497098e340b396972f9ead28dbaf6
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73139051"
---
# <a name="icordebuginstancefieldsymbolgetname-method"></a><span data-ttu-id="6a8ed-102">ICorDebugInstanceFieldSymbol:: GetName — Metoda</span><span class="sxs-lookup"><span data-stu-id="6a8ed-102">ICorDebugInstanceFieldSymbol::GetName Method</span></span>
<span data-ttu-id="6a8ed-103">Pobiera nazwę pola wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="6a8ed-103">Gets the name of the instance field.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6a8ed-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="6a8ed-104">Syntax</span></span>  
  
```cpp  
HRESULT GetName(  
   [in] ULONG32 cchName,   
   [out] ULONG32 *pcchName,   
   [out, size_is(cchName), length_is(*pcchName)] WCHAR szName[]  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="6a8ed-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="6a8ed-105">Parameters</span></span>  
 `cchName`  
 <span data-ttu-id="6a8ed-106">podczas Liczba znaków w buforze `szName`.</span><span class="sxs-lookup"><span data-stu-id="6a8ed-106">[in] The number of characters in the `szName` buffer.</span></span>  
  
 `pcchName`  
 <span data-ttu-id="6a8ed-107">określoną Wskaźnik do liczby znaków rzeczywiście zapisywana w buforze `szName`.</span><span class="sxs-lookup"><span data-stu-id="6a8ed-107">[out] A pointer to the number of characters actually written to the `szName` buffer.</span></span>  
  
 `szName`  
 <span data-ttu-id="6a8ed-108">określoną Tablica znaków przechowująca zwróconą nazwę.</span><span class="sxs-lookup"><span data-stu-id="6a8ed-108">[out] A character array that stores the returned name.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="6a8ed-109">Uwagi</span><span class="sxs-lookup"><span data-stu-id="6a8ed-109">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="6a8ed-110">Ta metoda jest dostępna tylko z .NET Native.</span><span class="sxs-lookup"><span data-stu-id="6a8ed-110">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6a8ed-111">Wymagania</span><span class="sxs-lookup"><span data-stu-id="6a8ed-111">Requirements</span></span>  
 <span data-ttu-id="6a8ed-112">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6a8ed-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6a8ed-113">**Nagłówek:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="6a8ed-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="6a8ed-114">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="6a8ed-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="6a8ed-115">**Wersje .NET Framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6a8ed-115">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6a8ed-116">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="6a8ed-116">See also</span></span>

- [<span data-ttu-id="6a8ed-117">ICorDebugInstanceFieldSymbol, interfejs</span><span class="sxs-lookup"><span data-stu-id="6a8ed-117">ICorDebugInstanceFieldSymbol Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebuginstancefieldsymbol-interface.md)
- [<span data-ttu-id="6a8ed-118">Debugowanie, interfejsy</span><span class="sxs-lookup"><span data-stu-id="6a8ed-118">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
