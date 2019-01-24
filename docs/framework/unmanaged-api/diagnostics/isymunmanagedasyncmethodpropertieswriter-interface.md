---
title: ISymUnmanagedAsyncMethodPropertiesWriter — Interfejs
ms.date: 03/30/2017
ms.assetid: caa71820-8058-4b6a-93a2-25ee757d92d3
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: d83270d0e7f5dabff8402f5f81dae20d4457d147
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54604261"
---
# <a name="isymunmanagedasyncmethodpropertieswriter-interface"></a><span data-ttu-id="0202b-102">ISymUnmanagedAsyncMethodPropertiesWriter — Interfejs</span><span class="sxs-lookup"><span data-stu-id="0202b-102">ISymUnmanagedAsyncMethodPropertiesWriter Interface</span></span>
<span data-ttu-id="0202b-103">Pozwala zdefiniować informacje dotyczące metody async opcjonalne dla każdej metody symbolu.</span><span class="sxs-lookup"><span data-stu-id="0202b-103">Allows you to define optional async method information for each method symbol.</span></span> <span data-ttu-id="0202b-104">Zawsze używaj metodą otwarte; oznacza to między wywołaniami [openmethod — metoda](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-openmethod-method.md) i [closemethod — metoda](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-closemethod-method.md).</span><span class="sxs-lookup"><span data-stu-id="0202b-104">Always use with an opened method; that is, between calls to the [OpenMethod Method](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-openmethod-method.md) and the [CloseMethod Method](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-closemethod-method.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0202b-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="0202b-105">Syntax</span></span>  
  
```idl  
[object,uuid(FC073774-1739-4232-BD56-A027294BEC15),pointer_default(unique)]interface ISymUnmanagedAsyncMethodPropertiesWriter : IUnknown  
```  
  
## <a name="methods"></a><span data-ttu-id="0202b-106">Metody</span><span class="sxs-lookup"><span data-stu-id="0202b-106">Methods</span></span>  
 <span data-ttu-id="0202b-107">Ten interfejs zawiera następujące metody:</span><span class="sxs-lookup"><span data-stu-id="0202b-107">This interface contains the following methods:</span></span>  
  
|<span data-ttu-id="0202b-108">Metoda</span><span class="sxs-lookup"><span data-stu-id="0202b-108">Method</span></span>|<span data-ttu-id="0202b-109">Opis</span><span class="sxs-lookup"><span data-stu-id="0202b-109">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="0202b-110">DefineAsyncStepInfo, metoda</span><span class="sxs-lookup"><span data-stu-id="0202b-110">DefineAsyncStepInfo Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedasyncmethodpropertieswriter-defineasyncstepinfo-method.md)|<span data-ttu-id="0202b-111">Zdefiniuj grupę async operator await operacji w bieżącej metodzie.</span><span class="sxs-lookup"><span data-stu-id="0202b-111">Define a group of async await operations in the current method.</span></span><br /><br /> <span data-ttu-id="0202b-112">Przesunięcie każdego yield pasuje do zwrotu instrukcji await, identyfikowanie potencjalnej wydajności.</span><span class="sxs-lookup"><span data-stu-id="0202b-112">Each yield offset matches an await's return instruction, identifying a potential yield.</span></span> <span data-ttu-id="0202b-113">Każdy `breakpointMethod` / `breakpointOffset` pary identyfikuje, gdy operacja asynchroniczna zostanie wznowiona; może być w innej metody.</span><span class="sxs-lookup"><span data-stu-id="0202b-113">Each `breakpointMethod`/`breakpointOffset` pair identifies where the asynchronous operation will resume; it may be in a different method.</span></span>|  
|[<span data-ttu-id="0202b-114">DefineCatchHandlerILOffset, metoda</span><span class="sxs-lookup"><span data-stu-id="0202b-114">DefineCatchHandlerILOffset Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedasyncmethodpropertieswriter-definecatchhandleriloffset-method.md)|<span data-ttu-id="0202b-115">Ustawia IL przesunięcie obsługi catch generowanych przez kompilator, który otacza metody asynchronicznej.</span><span class="sxs-lookup"><span data-stu-id="0202b-115">Sets the IL offset for the compiler-generated catch handler that wraps an async method.</span></span><br /><br /> <span data-ttu-id="0202b-116">Przesunięcie IL wygenerowanego catch jest używany przez debuger do obsługi catch, tak jakby kod niezwiązany z użytkownikiem, mimo że może występować w metodzie kodu użytkownika.</span><span class="sxs-lookup"><span data-stu-id="0202b-116">The IL offset of the generated catch is used by the debugger to handle the catch as if it were non-user code, even though it may occur in a user code method.</span></span> <span data-ttu-id="0202b-117">W szczególności jest używany w odpowiedzi na **CatchHandlerFound** zdarzenie wyjątku.</span><span class="sxs-lookup"><span data-stu-id="0202b-117">In particular, it is used in response to a **CatchHandlerFound** exception event.</span></span>|  
|[<span data-ttu-id="0202b-118">DefineKickoffMethod, metoda</span><span class="sxs-lookup"><span data-stu-id="0202b-118">DefineKickoffMethod Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedasyncmethodpropertieswriter-definekickoffmethod-method.md)|<span data-ttu-id="0202b-119">Ustawia metodę początkową, która inicjuje operacji asynchronicznej.</span><span class="sxs-lookup"><span data-stu-id="0202b-119">Sets the starting method that initiates the async operation.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="0202b-120">Wymagania</span><span class="sxs-lookup"><span data-stu-id="0202b-120">Requirements</span></span>  
 <span data-ttu-id="0202b-121">**Nagłówek:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="0202b-121">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0202b-122">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="0202b-122">See also</span></span>
- [<span data-ttu-id="0202b-123">Interfejsy magazynu symboli diagnostycznych</span><span class="sxs-lookup"><span data-stu-id="0202b-123">Diagnostics Symbol Store Interfaces</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/diagnostics-symbol-store-interfaces.md)
