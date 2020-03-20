---
title: ICorDebugInstanceFieldSymbol::Metoda GetName
ms.date: 03/30/2017
ms.assetid: d9c12b1f-9c1d-4943-8e9e-93b55faf085f
ms.openlocfilehash: dd925cc213ed8a6c5d1def85b3e6335751c1b594
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79178762"
---
# <a name="icordebuginstancefieldsymbolgetname-method"></a><span data-ttu-id="ab8b7-102">ICorDebugInstanceFieldSymbol::Metoda GetName</span><span class="sxs-lookup"><span data-stu-id="ab8b7-102">ICorDebugInstanceFieldSymbol::GetName Method</span></span>
<span data-ttu-id="ab8b7-103">Pobiera nazwę pola wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="ab8b7-103">Gets the name of the instance field.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ab8b7-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="ab8b7-104">Syntax</span></span>  
  
```cpp  
HRESULT GetName(  
   [in] ULONG32 cchName,
   [out] ULONG32 *pcchName,
   [out, size_is(cchName), length_is(*pcchName)] WCHAR szName[]  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ab8b7-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="ab8b7-105">Parameters</span></span>  
 `cchName`  
 <span data-ttu-id="ab8b7-106">[w] Liczba znaków w `szName` buforze.</span><span class="sxs-lookup"><span data-stu-id="ab8b7-106">[in] The number of characters in the `szName` buffer.</span></span>  
  
 `pcchName`  
 <span data-ttu-id="ab8b7-107">[na zewnątrz] Wskaźnik do liczby znaków faktycznie zapisane `szName` w buforze.</span><span class="sxs-lookup"><span data-stu-id="ab8b7-107">[out] A pointer to the number of characters actually written to the `szName` buffer.</span></span>  
  
 `szName`  
 <span data-ttu-id="ab8b7-108">[na zewnątrz] Tablica znaków, która przechowuje zwróconą nazwę.</span><span class="sxs-lookup"><span data-stu-id="ab8b7-108">[out] A character array that stores the returned name.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ab8b7-109">Uwagi</span><span class="sxs-lookup"><span data-stu-id="ab8b7-109">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="ab8b7-110">Ta metoda jest dostępna tylko w przypadku platformy .NET Native.</span><span class="sxs-lookup"><span data-stu-id="ab8b7-110">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ab8b7-111">Wymagania</span><span class="sxs-lookup"><span data-stu-id="ab8b7-111">Requirements</span></span>  
 <span data-ttu-id="ab8b7-112">**Platformy:** Zobacz [Wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ab8b7-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ab8b7-113">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="ab8b7-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="ab8b7-114">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="ab8b7-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="ab8b7-115">**Wersje programu .NET Framework:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ab8b7-115">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ab8b7-116">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="ab8b7-116">See also</span></span>

- [<span data-ttu-id="ab8b7-117">ICorDebugInstanceFieldSymbol, interfejs</span><span class="sxs-lookup"><span data-stu-id="ab8b7-117">ICorDebugInstanceFieldSymbol Interface</span></span>](icordebuginstancefieldsymbol-interface.md)
- [<span data-ttu-id="ab8b7-118">Debugowanie — Interfejsy</span><span class="sxs-lookup"><span data-stu-id="ab8b7-118">Debugging Interfaces</span></span>](debugging-interfaces.md)
