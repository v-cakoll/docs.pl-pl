---
title: 'ICorDebugInstanceFieldSymbol:: GetOffset — Metoda'
ms.date: 03/30/2017
ms.assetid: 7e470150-2b92-4425-989c-315f48964fd2
ms.openlocfilehash: f7c13d397b39698bdf1a22f14820680e1fd0a25f
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/28/2020
ms.locfileid: "76782293"
---
# <a name="icordebuginstancefieldsymbolgetoffset-method"></a><span data-ttu-id="ed019-102">ICorDebugInstanceFieldSymbol:: GetOffset — Metoda</span><span class="sxs-lookup"><span data-stu-id="ed019-102">ICorDebugInstanceFieldSymbol::GetOffset Method</span></span>
<span data-ttu-id="ed019-103">Pobiera przesunięcie w bajtach tego pola wystąpienia w jego klasie nadrzędnej.</span><span class="sxs-lookup"><span data-stu-id="ed019-103">Gets the offset in bytes of this instance field in its parent class.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ed019-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="ed019-104">Syntax</span></span>  
  
```cpp  
HRESULT GetOffset(  
   [out] ULONG32 *pcbOffset  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ed019-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="ed019-105">Parameters</span></span>  
 `pcbOffset`  
 <span data-ttu-id="ed019-106">Wskaźnik do liczby bajtów, które to pole wystąpienia jest przesunięte w swojej klasie nadrzędnej.</span><span class="sxs-lookup"><span data-stu-id="ed019-106">A pointer to the number of bytes that this instance field is offset in its parent class.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ed019-107">Uwagi</span><span class="sxs-lookup"><span data-stu-id="ed019-107">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="ed019-108">Ta metoda jest dostępna tylko z .NET Native.</span><span class="sxs-lookup"><span data-stu-id="ed019-108">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ed019-109">Wymagania</span><span class="sxs-lookup"><span data-stu-id="ed019-109">Requirements</span></span>  
 <span data-ttu-id="ed019-110">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ed019-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ed019-111">**Nagłówek:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="ed019-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="ed019-112">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="ed019-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="ed019-113">**Wersje .NET Framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ed019-113">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ed019-114">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="ed019-114">See also</span></span>

- [<span data-ttu-id="ed019-115">ICorDebugInstanceFieldSymbol, interfejs</span><span class="sxs-lookup"><span data-stu-id="ed019-115">ICorDebugInstanceFieldSymbol Interface</span></span>](icordebuginstancefieldsymbol-interface.md)
- [<span data-ttu-id="ed019-116">Debugowanie, interfejsy</span><span class="sxs-lookup"><span data-stu-id="ed019-116">Debugging Interfaces</span></span>](debugging-interfaces.md)
