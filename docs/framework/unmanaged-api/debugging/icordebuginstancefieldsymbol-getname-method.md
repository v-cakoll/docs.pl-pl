---
title: 'ICorDebugInstanceFieldSymbol:: GetName — Metoda'
ms.date: 03/30/2017
ms.assetid: d9c12b1f-9c1d-4943-8e9e-93b55faf085f
ms.openlocfilehash: 05914863dfbc2aca608a5d74f298f81c64345fe8
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/28/2020
ms.locfileid: "76782388"
---
# <a name="icordebuginstancefieldsymbolgetname-method"></a><span data-ttu-id="2556d-102">ICorDebugInstanceFieldSymbol:: GetName — Metoda</span><span class="sxs-lookup"><span data-stu-id="2556d-102">ICorDebugInstanceFieldSymbol::GetName Method</span></span>
<span data-ttu-id="2556d-103">Pobiera nazwę pola wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="2556d-103">Gets the name of the instance field.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2556d-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="2556d-104">Syntax</span></span>  
  
```cpp  
HRESULT GetName(  
   [in] ULONG32 cchName,   
   [out] ULONG32 *pcchName,   
   [out, size_is(cchName), length_is(*pcchName)] WCHAR szName[]  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="2556d-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="2556d-105">Parameters</span></span>  
 `cchName`  
 <span data-ttu-id="2556d-106">podczas Liczba znaków w buforze `szName`.</span><span class="sxs-lookup"><span data-stu-id="2556d-106">[in] The number of characters in the `szName` buffer.</span></span>  
  
 `pcchName`  
 <span data-ttu-id="2556d-107">określoną Wskaźnik do liczby znaków rzeczywiście zapisywana w buforze `szName`.</span><span class="sxs-lookup"><span data-stu-id="2556d-107">[out] A pointer to the number of characters actually written to the `szName` buffer.</span></span>  
  
 `szName`  
 <span data-ttu-id="2556d-108">określoną Tablica znaków przechowująca zwróconą nazwę.</span><span class="sxs-lookup"><span data-stu-id="2556d-108">[out] A character array that stores the returned name.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="2556d-109">Uwagi</span><span class="sxs-lookup"><span data-stu-id="2556d-109">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="2556d-110">Ta metoda jest dostępna tylko z .NET Native.</span><span class="sxs-lookup"><span data-stu-id="2556d-110">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2556d-111">Wymagania</span><span class="sxs-lookup"><span data-stu-id="2556d-111">Requirements</span></span>  
 <span data-ttu-id="2556d-112">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2556d-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2556d-113">**Nagłówek:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="2556d-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="2556d-114">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="2556d-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="2556d-115">**Wersje .NET Framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2556d-115">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2556d-116">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="2556d-116">See also</span></span>

- [<span data-ttu-id="2556d-117">ICorDebugInstanceFieldSymbol, interfejs</span><span class="sxs-lookup"><span data-stu-id="2556d-117">ICorDebugInstanceFieldSymbol Interface</span></span>](icordebuginstancefieldsymbol-interface.md)
- [<span data-ttu-id="2556d-118">Debugowanie, interfejsy</span><span class="sxs-lookup"><span data-stu-id="2556d-118">Debugging Interfaces</span></span>](debugging-interfaces.md)
