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
ms.openlocfilehash: 3bae0e2dfb56883a674b282acd385ba45a25bebb
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="isymunmanagedasyncmethodpropertieswriterdefinecatchhandleriloffset-method"></a><span data-ttu-id="40b3a-102">ISymUnmanagedAsyncMethodPropertiesWriter::DefineCatchHandlerILOffset — Metoda</span><span class="sxs-lookup"><span data-stu-id="40b3a-102">ISymUnmanagedAsyncMethodPropertiesWriter::DefineCatchHandlerILOffset Method</span></span>
<span data-ttu-id="40b3a-103">Ustawia IL przesunięcie obsługi catch generowane przez kompilator, który opakowuje metody asynchronicznej.</span><span class="sxs-lookup"><span data-stu-id="40b3a-103">Sets the IL offset for the compiler-generated catch handler that wraps an async method.</span></span>  
  
 <span data-ttu-id="40b3a-104">Przesunięcie IL wygenerowanego catch jest używany przez debuger do obsługi catch, tak jakby był on kodu innych użytkowników, nawet jeśli mogą wystąpić w metody kodu użytkownika.</span><span class="sxs-lookup"><span data-stu-id="40b3a-104">The IL offset of the generated catch is used by the debugger to handle the catch as if it were non-user code even though it might occur in a user code method.</span></span> <span data-ttu-id="40b3a-105">W szczególności, jest on używany w odpowiedzi na **CatchHandlerFound** zdarzeniu wyjątku.</span><span class="sxs-lookup"><span data-stu-id="40b3a-105">In particular, it is used in response to a **CatchHandlerFound** exception event.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="40b3a-106">Składnia</span><span class="sxs-lookup"><span data-stu-id="40b3a-106">Syntax</span></span>  
  
```idl  
HRESULT DefineCatchHandlerILOffset(    [in] ULONG32 catchHandlerOffset);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="40b3a-107">Parametry</span><span class="sxs-lookup"><span data-stu-id="40b3a-107">Parameters</span></span>  
  
|<span data-ttu-id="40b3a-108">Parametr</span><span class="sxs-lookup"><span data-stu-id="40b3a-108">Parameter</span></span>|<span data-ttu-id="40b3a-109">Opis</span><span class="sxs-lookup"><span data-stu-id="40b3a-109">Description</span></span>|  
|---------------|-----------------|  
|`catchHandlerOffset`||  
  
## <a name="return-value"></a><span data-ttu-id="40b3a-110">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="40b3a-110">Return Value</span></span>  
 <span data-ttu-id="40b3a-111">Zwraca `HRESULT`.</span><span class="sxs-lookup"><span data-stu-id="40b3a-111">Returns `HRESULT`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="40b3a-112">Wymagania</span><span class="sxs-lookup"><span data-stu-id="40b3a-112">Requirements</span></span>  
 <span data-ttu-id="40b3a-113">**Nagłówek:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="40b3a-113">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="40b3a-114">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="40b3a-114">See Also</span></span>  
 [<span data-ttu-id="40b3a-115">Isymunmanagedasyncmethodpropertieswriter — interfejs</span><span class="sxs-lookup"><span data-stu-id="40b3a-115">ISymUnmanagedAsyncMethodPropertiesWriter Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedasyncmethodpropertieswriter-interface.md)
