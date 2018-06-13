---
title: ISymUnmanagedAsyncMethodPropertiesWriter::DefineCatchHandlerILOffset — Metoda
ms.date: 03/30/2017
ms.assetid: 92af7896-2201-408d-8b1b-23e28001eeac
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: ce462c4e7e9c8fb11ee74a91f3ece2465a44a834
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33425434"
---
# <a name="isymunmanagedasyncmethodpropertieswriterdefinecatchhandleriloffset-method"></a><span data-ttu-id="350f3-102">ISymUnmanagedAsyncMethodPropertiesWriter::DefineCatchHandlerILOffset — Metoda</span><span class="sxs-lookup"><span data-stu-id="350f3-102">ISymUnmanagedAsyncMethodPropertiesWriter::DefineCatchHandlerILOffset Method</span></span>
<span data-ttu-id="350f3-103">Ustawia IL przesunięcie obsługi catch generowane przez kompilator, który opakowuje metody asynchronicznej.</span><span class="sxs-lookup"><span data-stu-id="350f3-103">Sets the IL offset for the compiler-generated catch handler that wraps an async method.</span></span>  
  
 <span data-ttu-id="350f3-104">Przesunięcie IL wygenerowanego catch jest używany przez debuger do obsługi catch, tak jakby był on kodu innych użytkowników, nawet jeśli mogą wystąpić w metody kodu użytkownika.</span><span class="sxs-lookup"><span data-stu-id="350f3-104">The IL offset of the generated catch is used by the debugger to handle the catch as if it were non-user code even though it might occur in a user code method.</span></span> <span data-ttu-id="350f3-105">W szczególności, jest on używany w odpowiedzi na **CatchHandlerFound** zdarzeniu wyjątku.</span><span class="sxs-lookup"><span data-stu-id="350f3-105">In particular, it is used in response to a **CatchHandlerFound** exception event.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="350f3-106">Składnia</span><span class="sxs-lookup"><span data-stu-id="350f3-106">Syntax</span></span>  
  
```idl  
HRESULT DefineCatchHandlerILOffset(    [in] ULONG32 catchHandlerOffset);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="350f3-107">Parametry</span><span class="sxs-lookup"><span data-stu-id="350f3-107">Parameters</span></span>  
  
|<span data-ttu-id="350f3-108">Parametr</span><span class="sxs-lookup"><span data-stu-id="350f3-108">Parameter</span></span>|<span data-ttu-id="350f3-109">Opis</span><span class="sxs-lookup"><span data-stu-id="350f3-109">Description</span></span>|  
|---------------|-----------------|  
|`catchHandlerOffset`||  
  
## <a name="return-value"></a><span data-ttu-id="350f3-110">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="350f3-110">Return Value</span></span>  
 <span data-ttu-id="350f3-111">Zwraca `HRESULT`.</span><span class="sxs-lookup"><span data-stu-id="350f3-111">Returns `HRESULT`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="350f3-112">Wymagania</span><span class="sxs-lookup"><span data-stu-id="350f3-112">Requirements</span></span>  
 <span data-ttu-id="350f3-113">**Header:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="350f3-113">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="350f3-114">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="350f3-114">See Also</span></span>  
 [<span data-ttu-id="350f3-115">ISymUnmanagedAsyncMethodPropertiesWriter, interfejs</span><span class="sxs-lookup"><span data-stu-id="350f3-115">ISymUnmanagedAsyncMethodPropertiesWriter Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedasyncmethodpropertieswriter-interface.md)
