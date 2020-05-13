---
title: 'ICorDebugInstanceFieldSymbol:: GetSize — metoda'
ms.date: 03/30/2017
ms.assetid: a4af1e3b-6a9f-4855-95ba-5317565c8e2b
ms.openlocfilehash: 3d3c6881ecd54fc48be92e5ea0dc74a5cfdabd8f
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/12/2020
ms.locfileid: "83209956"
---
# <a name="icordebuginstancefieldsymbolgetsize-method"></a><span data-ttu-id="6d097-102">ICorDebugInstanceFieldSymbol:: GetSize — metoda</span><span class="sxs-lookup"><span data-stu-id="6d097-102">ICorDebugInstanceFieldSymbol::GetSize Method</span></span>
<span data-ttu-id="6d097-103">Pobiera rozmiar w bajtach pola wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="6d097-103">Gets the size in bytes of the instance field.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6d097-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="6d097-104">Syntax</span></span>  
  
```cpp  
HRESULT GetSize(  
   [out] ULONG32 *pcbSize  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="6d097-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="6d097-105">Parameters</span></span>  
 `pcbSize`  
 <span data-ttu-id="6d097-106">określoną Wskaźnik do długości pola.</span><span class="sxs-lookup"><span data-stu-id="6d097-106">[out] A pointer to length of the field.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="6d097-107">Uwagi</span><span class="sxs-lookup"><span data-stu-id="6d097-107">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="6d097-108">Ta metoda jest dostępna tylko z .NET Native.</span><span class="sxs-lookup"><span data-stu-id="6d097-108">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6d097-109">Wymagania</span><span class="sxs-lookup"><span data-stu-id="6d097-109">Requirements</span></span>  
 <span data-ttu-id="6d097-110">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6d097-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6d097-111">**Nagłówek:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="6d097-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="6d097-112">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="6d097-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="6d097-113">**.NET Framework wersje:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6d097-113">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6d097-114">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="6d097-114">See also</span></span>

- [<span data-ttu-id="6d097-115">ICorDebugInstanceFieldSymbol, interfejs</span><span class="sxs-lookup"><span data-stu-id="6d097-115">ICorDebugInstanceFieldSymbol Interface</span></span>](icordebuginstancefieldsymbol-interface.md)
- [<span data-ttu-id="6d097-116">Debugowanie — Interfejsy</span><span class="sxs-lookup"><span data-stu-id="6d097-116">Debugging Interfaces</span></span>](debugging-interfaces.md)
