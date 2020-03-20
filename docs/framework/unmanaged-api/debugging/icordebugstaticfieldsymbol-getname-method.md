---
title: ICorDebugStaticFieldSymbol::Metoda GetName
ms.date: 03/30/2017
ms.assetid: e2be4af2-15d1-4e6a-8b68-1d78c93294a4
ms.openlocfilehash: b1f5ca266f51df730dfb840c7bf003c47f31ece9
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79178516"
---
# <a name="icordebugstaticfieldsymbolgetname-method"></a><span data-ttu-id="01167-102">ICorDebugStaticFieldSymbol::Metoda GetName</span><span class="sxs-lookup"><span data-stu-id="01167-102">ICorDebugStaticFieldSymbol::GetName Method</span></span>
<span data-ttu-id="01167-103">Pobiera nazwę pola statycznego.</span><span class="sxs-lookup"><span data-stu-id="01167-103">Gets the name of the static field.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="01167-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="01167-104">Syntax</span></span>  
  
```cpp  
HRESULT GetName(  
   [in] ULONG32 cchName,
   [out] ULONG32 *pcchName,
   [out, size_is(cchName), length_is(*pcchName)] WCHAR szName[]  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="01167-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="01167-105">Parameters</span></span>  
 `cchName`  
 <span data-ttu-id="01167-106">[w] Liczba znaków w `szName` buforze.</span><span class="sxs-lookup"><span data-stu-id="01167-106">[in] The number of characters in the `szName` buffer.</span></span>  
  
 `pcchName`  
 <span data-ttu-id="01167-107">[na zewnątrz] Wskaźnik do liczby znaków faktycznie zapisane `szName` w buforze.</span><span class="sxs-lookup"><span data-stu-id="01167-107">[out] A pointer to the number of characters actually written to the `szName` buffer.</span></span>  
  
 `szName`  
 <span data-ttu-id="01167-108">[na zewnątrz] Tablica znaków, która przechowuje zwróconą nazwę.</span><span class="sxs-lookup"><span data-stu-id="01167-108">[out] A character array that stores the returned name.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="01167-109">Uwagi</span><span class="sxs-lookup"><span data-stu-id="01167-109">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="01167-110">Ta metoda jest dostępna tylko w przypadku platformy .NET Native.</span><span class="sxs-lookup"><span data-stu-id="01167-110">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="01167-111">Wymagania</span><span class="sxs-lookup"><span data-stu-id="01167-111">Requirements</span></span>  
 <span data-ttu-id="01167-112">**Platformy:** Zobacz [Wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="01167-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="01167-113">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="01167-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="01167-114">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="01167-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="01167-115">**Wersje programu .NET Framework:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="01167-115">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="01167-116">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="01167-116">See also</span></span>

- [<span data-ttu-id="01167-117">ICorDebugStaticFieldSymbol, interfejs</span><span class="sxs-lookup"><span data-stu-id="01167-117">ICorDebugStaticFieldSymbol Interface</span></span>](icordebugstaticfieldsymbol-interface.md)
- [<span data-ttu-id="01167-118">Debugowanie — Interfejsy</span><span class="sxs-lookup"><span data-stu-id="01167-118">Debugging Interfaces</span></span>](debugging-interfaces.md)
