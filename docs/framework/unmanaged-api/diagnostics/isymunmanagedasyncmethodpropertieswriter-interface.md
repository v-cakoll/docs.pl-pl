---
title: "ISymUnmanagedAsyncMethodPropertiesWriter — Interfejs"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: caa71820-8058-4b6a-93a2-25ee757d92d3
caps.latest.revision: "6"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: dd84ea5ee00df3e59d4907cdf97bc36b7f06d993
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="isymunmanagedasyncmethodpropertieswriter-interface"></a><span data-ttu-id="ae504-102">ISymUnmanagedAsyncMethodPropertiesWriter — Interfejs</span><span class="sxs-lookup"><span data-stu-id="ae504-102">ISymUnmanagedAsyncMethodPropertiesWriter Interface</span></span>
<span data-ttu-id="ae504-103">Można zdefiniować informacje dotyczące metody asynchronicznej opcjonalne dla każdego symbolu — metoda.</span><span class="sxs-lookup"><span data-stu-id="ae504-103">Allows you to define optional async method information for each method symbol.</span></span> <span data-ttu-id="ae504-104">Zawsze używaj metodą otwarty; oznacza to, że między wywołań [OpenMethod — metoda](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-openmethod-method.md) i [CloseMethod — metoda](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-closemethod-method.md).</span><span class="sxs-lookup"><span data-stu-id="ae504-104">Always use with an opened method; that is, between calls to the [OpenMethod Method](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-openmethod-method.md) and the [CloseMethod Method](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-closemethod-method.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ae504-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="ae504-105">Syntax</span></span>  
  
```idl  
[object,uuid(FC073774-1739-4232-BD56-A027294BEC15),pointer_default(unique)]interface ISymUnmanagedAsyncMethodPropertiesWriter : IUnknown  
```  
  
## <a name="methods"></a><span data-ttu-id="ae504-106">Metody</span><span class="sxs-lookup"><span data-stu-id="ae504-106">Methods</span></span>  
 <span data-ttu-id="ae504-107">Ten interfejs zawiera następujące metody:</span><span class="sxs-lookup"><span data-stu-id="ae504-107">This interface contains the following methods:</span></span>  
  
|<span data-ttu-id="ae504-108">Metoda</span><span class="sxs-lookup"><span data-stu-id="ae504-108">Method</span></span>|<span data-ttu-id="ae504-109">Opis</span><span class="sxs-lookup"><span data-stu-id="ae504-109">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="ae504-110">DefineAsyncStepInfo — metoda</span><span class="sxs-lookup"><span data-stu-id="ae504-110">DefineAsyncStepInfo Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedasyncmethodpropertieswriter-defineasyncstepinfo-method.md)|<span data-ttu-id="ae504-111">Zdefiniuj grupę asynchronicznych operacji w bieżącej metodzie await.</span><span class="sxs-lookup"><span data-stu-id="ae504-111">Define a group of async await operations in the current method.</span></span><br /><br /> <span data-ttu-id="ae504-112">Przesunięcie każdego yield odpowiada instrukcji return await, identyfikowanie potencjalnej wydajności.</span><span class="sxs-lookup"><span data-stu-id="ae504-112">Each yield offset matches an await's return instruction, identifying a potential yield.</span></span> <span data-ttu-id="ae504-113">Każdy `breakpointMethod` / `breakpointOffset` pary identyfikuje, gdy operacja asynchroniczna wznowi; być może jest ona w innej metody.</span><span class="sxs-lookup"><span data-stu-id="ae504-113">Each `breakpointMethod`/`breakpointOffset` pair identifies where the asynchronous operation will resume; it may be in a different method.</span></span>|  
|[<span data-ttu-id="ae504-114">DefineCatchHandlerILOffset — metoda</span><span class="sxs-lookup"><span data-stu-id="ae504-114">DefineCatchHandlerILOffset Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedasyncmethodpropertieswriter-definecatchhandleriloffset-method.md)|<span data-ttu-id="ae504-115">Ustawia IL przesunięcie obsługi catch generowane przez kompilator, który opakowuje metody asynchronicznej.</span><span class="sxs-lookup"><span data-stu-id="ae504-115">Sets the IL offset for the compiler-generated catch handler that wraps an async method.</span></span><br /><br /> <span data-ttu-id="ae504-116">Przesunięcie IL wygenerowanego catch jest używany przez debuger do obsługi catch, tak jakby był on kodu innych użytkowników, mimo że może wystąpić w metody kodu użytkownika.</span><span class="sxs-lookup"><span data-stu-id="ae504-116">The IL offset of the generated catch is used by the debugger to handle the catch as if it were non-user code, even though it may occur in a user code method.</span></span> <span data-ttu-id="ae504-117">W szczególności, jest on używany w odpowiedzi na **CatchHandlerFound** zdarzeniu wyjątku.</span><span class="sxs-lookup"><span data-stu-id="ae504-117">In particular, it is used in response to a **CatchHandlerFound** exception event.</span></span>|  
|[<span data-ttu-id="ae504-118">DefineKickoffMethod — metoda</span><span class="sxs-lookup"><span data-stu-id="ae504-118">DefineKickoffMethod Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedasyncmethodpropertieswriter-definekickoffmethod-method.md)|<span data-ttu-id="ae504-119">Ustawia metodę początkową, który inicjuje operacji asynchronicznej.</span><span class="sxs-lookup"><span data-stu-id="ae504-119">Sets the starting method that initiates the async operation.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="ae504-120">Wymagania</span><span class="sxs-lookup"><span data-stu-id="ae504-120">Requirements</span></span>  
 <span data-ttu-id="ae504-121">**Nagłówek:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="ae504-121">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ae504-122">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="ae504-122">See Also</span></span>  
 [<span data-ttu-id="ae504-123">Interfejsy magazynu symboli diagnostycznych</span><span class="sxs-lookup"><span data-stu-id="ae504-123">Diagnostics Symbol Store Interfaces</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/diagnostics-symbol-store-interfaces.md)
