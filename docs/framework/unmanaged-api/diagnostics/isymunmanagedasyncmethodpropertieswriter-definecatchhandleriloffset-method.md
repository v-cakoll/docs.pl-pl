---
title: ISymUnmanagedAsyncMethodPropertiesWriter::DefineCatchHandlerILOffset — Metoda
ms.date: 03/30/2017
ms.assetid: 92af7896-2201-408d-8b1b-23e28001eeac
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 923c85a9dff11753a338fcfd3673d3590fca607a
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59196752"
---
# <a name="isymunmanagedasyncmethodpropertieswriterdefinecatchhandleriloffset-method"></a><span data-ttu-id="03710-102">ISymUnmanagedAsyncMethodPropertiesWriter::DefineCatchHandlerILOffset — Metoda</span><span class="sxs-lookup"><span data-stu-id="03710-102">ISymUnmanagedAsyncMethodPropertiesWriter::DefineCatchHandlerILOffset Method</span></span>
<span data-ttu-id="03710-103">Ustawia IL przesunięcie obsługi catch generowanych przez kompilator, który otacza metody asynchronicznej.</span><span class="sxs-lookup"><span data-stu-id="03710-103">Sets the IL offset for the compiler-generated catch handler that wraps an async method.</span></span>  
  
 <span data-ttu-id="03710-104">Przesunięcie IL wygenerowanego catch jest używany przez debuger do obsługi catch, tak jakby był on niebędący kodem użytkownika, mimo że może wystąpić w metodzie kodu użytkownika.</span><span class="sxs-lookup"><span data-stu-id="03710-104">The IL offset of the generated catch is used by the debugger to handle the catch as if it were non-user code even though it might occur in a user code method.</span></span> <span data-ttu-id="03710-105">W szczególności jest używany w odpowiedzi na **CatchHandlerFound** zdarzenie wyjątku.</span><span class="sxs-lookup"><span data-stu-id="03710-105">In particular, it is used in response to a **CatchHandlerFound** exception event.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="03710-106">Składnia</span><span class="sxs-lookup"><span data-stu-id="03710-106">Syntax</span></span>  
  
```idl  
HRESULT DefineCatchHandlerILOffset(    [in] ULONG32 catchHandlerOffset);  
```  
  
## <a name="parameters"></a><span data-ttu-id="03710-107">Parametry</span><span class="sxs-lookup"><span data-stu-id="03710-107">Parameters</span></span>  
  
|<span data-ttu-id="03710-108">Parametr</span><span class="sxs-lookup"><span data-stu-id="03710-108">Parameter</span></span>|<span data-ttu-id="03710-109">Opis</span><span class="sxs-lookup"><span data-stu-id="03710-109">Description</span></span>|  
|---------------|-----------------|  
|`catchHandlerOffset`||  
  
## <a name="return-value"></a><span data-ttu-id="03710-110">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="03710-110">Return Value</span></span>  
 <span data-ttu-id="03710-111">Zwraca `HRESULT`.</span><span class="sxs-lookup"><span data-stu-id="03710-111">Returns `HRESULT`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="03710-112">Wymagania</span><span class="sxs-lookup"><span data-stu-id="03710-112">Requirements</span></span>  
 <span data-ttu-id="03710-113">**Nagłówek:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="03710-113">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="03710-114">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="03710-114">See also</span></span>

- [<span data-ttu-id="03710-115">ISymUnmanagedAsyncMethodPropertiesWriter, interfejs</span><span class="sxs-lookup"><span data-stu-id="03710-115">ISymUnmanagedAsyncMethodPropertiesWriter Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedasyncmethodpropertieswriter-interface.md)
