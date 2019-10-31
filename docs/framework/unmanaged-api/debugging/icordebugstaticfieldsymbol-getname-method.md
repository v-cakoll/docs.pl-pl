---
title: 'ICorDebugStaticFieldSymbol:: GetName — Metoda'
ms.date: 03/30/2017
ms.assetid: e2be4af2-15d1-4e6a-8b68-1d78c93294a4
ms.openlocfilehash: e961ae064bd5bb2c97175b4506ddd8c0f17d3b32
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73131779"
---
# <a name="icordebugstaticfieldsymbolgetname-method"></a><span data-ttu-id="2d9f6-102">ICorDebugStaticFieldSymbol:: GetName — Metoda</span><span class="sxs-lookup"><span data-stu-id="2d9f6-102">ICorDebugStaticFieldSymbol::GetName Method</span></span>
<span data-ttu-id="2d9f6-103">Pobiera nazwę pola statycznego.</span><span class="sxs-lookup"><span data-stu-id="2d9f6-103">Gets the name of the static field.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2d9f6-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="2d9f6-104">Syntax</span></span>  
  
```cpp  
HRESULT GetName(  
   [in] ULONG32 cchName,   
   [out] ULONG32 *pcchName,   
   [out, size_is(cchName), length_is(*pcchName)] WCHAR szName[]  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="2d9f6-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="2d9f6-105">Parameters</span></span>  
 `cchName`  
 <span data-ttu-id="2d9f6-106">podczas Liczba znaków w buforze `szName`.</span><span class="sxs-lookup"><span data-stu-id="2d9f6-106">[in] The number of characters in the `szName` buffer.</span></span>  
  
 `pcchName`  
 <span data-ttu-id="2d9f6-107">określoną Wskaźnik do liczby znaków rzeczywiście zapisywana w buforze `szName`.</span><span class="sxs-lookup"><span data-stu-id="2d9f6-107">[out] A pointer to the number of characters actually written to the `szName` buffer.</span></span>  
  
 `szName`  
 <span data-ttu-id="2d9f6-108">określoną Tablica znaków przechowująca zwróconą nazwę.</span><span class="sxs-lookup"><span data-stu-id="2d9f6-108">[out] A character array that stores the returned name.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="2d9f6-109">Uwagi</span><span class="sxs-lookup"><span data-stu-id="2d9f6-109">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="2d9f6-110">Ta metoda jest dostępna tylko z .NET Native.</span><span class="sxs-lookup"><span data-stu-id="2d9f6-110">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2d9f6-111">Wymagania</span><span class="sxs-lookup"><span data-stu-id="2d9f6-111">Requirements</span></span>  
 <span data-ttu-id="2d9f6-112">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2d9f6-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2d9f6-113">**Nagłówek:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="2d9f6-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="2d9f6-114">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="2d9f6-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="2d9f6-115">**Wersje .NET Framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2d9f6-115">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2d9f6-116">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="2d9f6-116">See also</span></span>

- [<span data-ttu-id="2d9f6-117">ICorDebugStaticFieldSymbol, interfejs</span><span class="sxs-lookup"><span data-stu-id="2d9f6-117">ICorDebugStaticFieldSymbol Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugstaticfieldsymbol-interface.md)
- [<span data-ttu-id="2d9f6-118">Debugowanie, interfejsy</span><span class="sxs-lookup"><span data-stu-id="2d9f6-118">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
