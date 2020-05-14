---
title: ICorDebugVirtualUnwinder — interfejs
ms.date: 03/30/2017
ms.assetid: a09e9ccc-0b37-43e3-95c1-bc5fa7ee5f42
ms.openlocfilehash: 59ecf3da4b44af7b04dec26fbc3ea182c185d04a
ms.sourcegitcommit: 046a9c22487551360e20ec39fc21eef99820a254
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/14/2020
ms.locfileid: "83396450"
---
# <a name="icordebugvirtualunwinder-interface"></a><span data-ttu-id="82da1-102">ICorDebugVirtualUnwinder — interfejs</span><span class="sxs-lookup"><span data-stu-id="82da1-102">ICorDebugVirtualUnwinder Interface</span></span>
<span data-ttu-id="82da1-103">Zapewnia metody pomagające w rozwinięcia stosu.</span><span class="sxs-lookup"><span data-stu-id="82da1-103">Provides methods to help in stack unwinding.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="82da1-104">Metody</span><span class="sxs-lookup"><span data-stu-id="82da1-104">Methods</span></span>  
  
|<span data-ttu-id="82da1-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="82da1-105">Method</span></span>|<span data-ttu-id="82da1-106">Nazwa</span><span class="sxs-lookup"><span data-stu-id="82da1-106">Name</span></span>|  
|------------|----------|  
|[<span data-ttu-id="82da1-107">GetContext — Metoda</span><span class="sxs-lookup"><span data-stu-id="82da1-107">GetContext Method</span></span>](icordebugvirtualunwinder-getcontext-method.md)|<span data-ttu-id="82da1-108">Pobiera bieżący kontekst tego elementu unwiatrer.</span><span class="sxs-lookup"><span data-stu-id="82da1-108">Gets the current context of this unwinder.</span></span>|  
|[<span data-ttu-id="82da1-109">Next — Metoda</span><span class="sxs-lookup"><span data-stu-id="82da1-109">Next Method</span></span>](icordebugvirtualunwinder-next-method.md)|<span data-ttu-id="82da1-110">Przechodzi do kontekstu obiektu wywołującego.</span><span class="sxs-lookup"><span data-stu-id="82da1-110">Advances to the caller's context.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="82da1-111">Uwagi</span><span class="sxs-lookup"><span data-stu-id="82da1-111">Remarks</span></span>  
 <span data-ttu-id="82da1-112">Elementy członkowskie `ICorDebugVirtualUnwinder` interfejsu są implementowane przez debuger, aby pomóc w rozwinięcia stosu.</span><span class="sxs-lookup"><span data-stu-id="82da1-112">The members of the `ICorDebugVirtualUnwinder` interface are implemented by the debugger to help in stack unwinding.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="82da1-113">Ten interfejs jest dostępny tylko dla .NET Native.</span><span class="sxs-lookup"><span data-stu-id="82da1-113">This interface is available with .NET Native only.</span></span> <span data-ttu-id="82da1-114">W przypadku zaimplementowania tego interfejsu dla scenariuszy ICorDebug poza .NET Native, środowisko uruchomieniowe języka wspólnego zignoruje ten interfejs.</span><span class="sxs-lookup"><span data-stu-id="82da1-114">If you implement this interface for ICorDebug scenarios outside of .NET Native, the common language runtime will ignore this interface.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="82da1-115">Wymagania</span><span class="sxs-lookup"><span data-stu-id="82da1-115">Requirements</span></span>  
 <span data-ttu-id="82da1-116">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="82da1-116">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="82da1-117">**Nagłówek:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="82da1-117">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="82da1-118">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="82da1-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="82da1-119">**.NET Framework wersje:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="82da1-119">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="82da1-120">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="82da1-120">See also</span></span>

- [<span data-ttu-id="82da1-121">Debugowanie — Interfejsy</span><span class="sxs-lookup"><span data-stu-id="82da1-121">Debugging Interfaces</span></span>](debugging-interfaces.md)
- [<span data-ttu-id="82da1-122">Debugowanie</span><span class="sxs-lookup"><span data-stu-id="82da1-122">Debugging</span></span>](index.md)
