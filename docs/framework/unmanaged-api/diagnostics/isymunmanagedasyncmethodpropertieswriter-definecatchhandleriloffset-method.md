---
title: "ISymUnmanagedAsyncMethodPropertiesWriter::DefineCatchHandlerILOffset — Metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: 92af7896-2201-408d-8b1b-23e28001eeac
caps.latest.revision: "4"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 54cc369b309d1ffe20d0f3e6a2d4ae4e0443c85f
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="isymunmanagedasyncmethodpropertieswriterdefinecatchhandleriloffset-method"></a><span data-ttu-id="4e771-102">ISymUnmanagedAsyncMethodPropertiesWriter::DefineCatchHandlerILOffset — Metoda</span><span class="sxs-lookup"><span data-stu-id="4e771-102">ISymUnmanagedAsyncMethodPropertiesWriter::DefineCatchHandlerILOffset Method</span></span>
<span data-ttu-id="4e771-103">Ustawia IL przesunięcie obsługi catch generowane przez kompilator, który opakowuje metody asynchronicznej.</span><span class="sxs-lookup"><span data-stu-id="4e771-103">Sets the IL offset for the compiler-generated catch handler that wraps an async method.</span></span>  
  
 <span data-ttu-id="4e771-104">Przesunięcie IL wygenerowanego catch jest używany przez debuger do obsługi catch, tak jakby był on kodu innych użytkowników, nawet jeśli mogą wystąpić w metody kodu użytkownika.</span><span class="sxs-lookup"><span data-stu-id="4e771-104">The IL offset of the generated catch is used by the debugger to handle the catch as if it were non-user code even though it might occur in a user code method.</span></span> <span data-ttu-id="4e771-105">W szczególności, jest on używany w odpowiedzi na **CatchHandlerFound** zdarzeniu wyjątku.</span><span class="sxs-lookup"><span data-stu-id="4e771-105">In particular, it is used in response to a **CatchHandlerFound** exception event.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4e771-106">Składnia</span><span class="sxs-lookup"><span data-stu-id="4e771-106">Syntax</span></span>  
  
```idl  
HRESULT DefineCatchHandlerILOffset(    [in] ULONG32 catchHandlerOffset);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="4e771-107">Parametry</span><span class="sxs-lookup"><span data-stu-id="4e771-107">Parameters</span></span>  
  
|<span data-ttu-id="4e771-108">Parametr</span><span class="sxs-lookup"><span data-stu-id="4e771-108">Parameter</span></span>|<span data-ttu-id="4e771-109">Opis</span><span class="sxs-lookup"><span data-stu-id="4e771-109">Description</span></span>|  
|---------------|-----------------|  
|`catchHandlerOffset`||  
  
## <a name="return-value"></a><span data-ttu-id="4e771-110">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="4e771-110">Return Value</span></span>  
 <span data-ttu-id="4e771-111">Zwraca `HRESULT`.</span><span class="sxs-lookup"><span data-stu-id="4e771-111">Returns `HRESULT`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4e771-112">Wymagania</span><span class="sxs-lookup"><span data-stu-id="4e771-112">Requirements</span></span>  
 <span data-ttu-id="4e771-113">**Nagłówek:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="4e771-113">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4e771-114">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="4e771-114">See Also</span></span>  
 [<span data-ttu-id="4e771-115">ISymUnmanagedAsyncMethodPropertiesWriter, interfejs</span><span class="sxs-lookup"><span data-stu-id="4e771-115">ISymUnmanagedAsyncMethodPropertiesWriter Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedasyncmethodpropertieswriter-interface.md)
