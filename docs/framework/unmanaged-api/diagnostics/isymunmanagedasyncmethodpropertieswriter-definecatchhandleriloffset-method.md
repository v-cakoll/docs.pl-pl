---
title: ISymUnmanagedAsyncMethodPropertiesWriter::DefineCatchHandlerILOffset — Metoda
ms.date: 03/30/2017
ms.assetid: 92af7896-2201-408d-8b1b-23e28001eeac
ms.openlocfilehash: 58dde2fcce3f4bf578907171e5b575c30c678cfc
ms.sourcegitcommit: 7b1497c1927cb449cefd313bc5126ae37df30746
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/16/2020
ms.locfileid: "83441776"
---
# <a name="isymunmanagedasyncmethodpropertieswriterdefinecatchhandleriloffset-method"></a><span data-ttu-id="1dc1f-102">ISymUnmanagedAsyncMethodPropertiesWriter::DefineCatchHandlerILOffset — Metoda</span><span class="sxs-lookup"><span data-stu-id="1dc1f-102">ISymUnmanagedAsyncMethodPropertiesWriter::DefineCatchHandlerILOffset Method</span></span>
<span data-ttu-id="1dc1f-103">Ustawia przesunięcie IL dla wygenerowanego przez kompilator procedury obsługi catch, która otacza metodę asynchroniczną.</span><span class="sxs-lookup"><span data-stu-id="1dc1f-103">Sets the IL offset for the compiler-generated catch handler that wraps an async method.</span></span>  
  
 <span data-ttu-id="1dc1f-104">Przesunięcie IL wygenerowanego catch jest używane przez debuger do obsługi catch tak, jakby była kodem nieużytkownika, nawet jeśli może wystąpić w metodzie kodu użytkownika.</span><span class="sxs-lookup"><span data-stu-id="1dc1f-104">The IL offset of the generated catch is used by the debugger to handle the catch as if it were non-user code even though it might occur in a user code method.</span></span> <span data-ttu-id="1dc1f-105">W szczególności jest używany w odpowiedzi na zdarzenie wyjątku **CatchHandlerFound** .</span><span class="sxs-lookup"><span data-stu-id="1dc1f-105">In particular, it is used in response to a **CatchHandlerFound** exception event.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1dc1f-106">Składnia</span><span class="sxs-lookup"><span data-stu-id="1dc1f-106">Syntax</span></span>  
  
```idl  
HRESULT DefineCatchHandlerILOffset(    [in] ULONG32 catchHandlerOffset);  
```  
  
## <a name="parameters"></a><span data-ttu-id="1dc1f-107">Parametry</span><span class="sxs-lookup"><span data-stu-id="1dc1f-107">Parameters</span></span>  
  
|<span data-ttu-id="1dc1f-108">Parametr</span><span class="sxs-lookup"><span data-stu-id="1dc1f-108">Parameter</span></span>|<span data-ttu-id="1dc1f-109">Opis</span><span class="sxs-lookup"><span data-stu-id="1dc1f-109">Description</span></span>|  
|---------------|-----------------|  
|`catchHandlerOffset`||  
  
## <a name="return-value"></a><span data-ttu-id="1dc1f-110">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="1dc1f-110">Return Value</span></span>  
 <span data-ttu-id="1dc1f-111">Zwraca wartość `HRESULT`.</span><span class="sxs-lookup"><span data-stu-id="1dc1f-111">Returns `HRESULT`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1dc1f-112">Wymagania</span><span class="sxs-lookup"><span data-stu-id="1dc1f-112">Requirements</span></span>  
 <span data-ttu-id="1dc1f-113">**Nagłówek:** CorSym. idl, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="1dc1f-113">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1dc1f-114">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="1dc1f-114">See also</span></span>

- [<span data-ttu-id="1dc1f-115">ISymUnmanagedAsyncMethodPropertiesWriter — Interfejs</span><span class="sxs-lookup"><span data-stu-id="1dc1f-115">ISymUnmanagedAsyncMethodPropertiesWriter Interface</span></span>](isymunmanagedasyncmethodpropertieswriter-interface.md)
