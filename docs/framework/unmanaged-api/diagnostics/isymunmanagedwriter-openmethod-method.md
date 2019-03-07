---
title: ISymUnmanagedWriter::OpenMethod — Metoda
ms.date: 03/30/2017
api_name:
- ISymUnmanagedWriter.OpenMethod
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedWriter::OpenMethod
helpviewer_keywords:
- ISymUnmanagedWriter::OpenMethod method [.NET Framework debugging]
- OpenMethod method [.NET Framework debugging]
ms.assetid: fb90cb7f-af88-45e8-a99f-80a0bbddb08b
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 3e6ee68fe3ffed0ae19c2f528a49a863b99fa7f7
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/06/2019
ms.locfileid: "57499553"
---
# <a name="isymunmanagedwriteropenmethod-method"></a><span data-ttu-id="7a59a-102">ISymUnmanagedWriter::OpenMethod — Metoda</span><span class="sxs-lookup"><span data-stu-id="7a59a-102">ISymUnmanagedWriter::OpenMethod Method</span></span>
<span data-ttu-id="7a59a-103">Zostanie otwarty metody, w której symbol informacje są emitowane.</span><span class="sxs-lookup"><span data-stu-id="7a59a-103">Opens a method into which symbol information is emitted.</span></span> <span data-ttu-id="7a59a-104">Danej metody staje się bieżącą metodę dla wywołań do definiowania punktów sekwencji, parametrów i leksykalne zakresów.</span><span class="sxs-lookup"><span data-stu-id="7a59a-104">The given method becomes the current method for calls to define sequence points, parameters, and lexical scopes.</span></span> <span data-ttu-id="7a59a-105">Istnieje niejawna zakresie leksykalnym, wokół całej metody.</span><span class="sxs-lookup"><span data-stu-id="7a59a-105">There is an implicit lexical scope around the entire method.</span></span> <span data-ttu-id="7a59a-106">Zamknij metodę, która została wcześniej zamknięta usuwa wszystkie uprzednio zdefiniowany symboli dla tej metody.</span><span class="sxs-lookup"><span data-stu-id="7a59a-106">Reopening a method that was previously closed erases any previously defined symbols for that method.</span></span> <span data-ttu-id="7a59a-107">Jednocześnie może istnieć tylko jedna metoda open.</span><span class="sxs-lookup"><span data-stu-id="7a59a-107">There can be only one open method at a time.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7a59a-108">Składnia</span><span class="sxs-lookup"><span data-stu-id="7a59a-108">Syntax</span></span>  
  
```  
HRESULT OpenMethod(  
    [in] mdMethodDef method);  
```  
  
## <a name="parameters"></a><span data-ttu-id="7a59a-109">Parametry</span><span class="sxs-lookup"><span data-stu-id="7a59a-109">Parameters</span></span>  
 `method`  
 <span data-ttu-id="7a59a-110">[in] Token metadanych dla metody, które ma zostać otwarty.</span><span class="sxs-lookup"><span data-stu-id="7a59a-110">[in] The metadata token for the method to be opened.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="7a59a-111">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="7a59a-111">Return Value</span></span>  
 <span data-ttu-id="7a59a-112">S_OK, jeśli metoda się powiedzie; w przeciwnym razie E_FAIL lub innego kodu błędu.</span><span class="sxs-lookup"><span data-stu-id="7a59a-112">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7a59a-113">Wymagania</span><span class="sxs-lookup"><span data-stu-id="7a59a-113">Requirements</span></span>  
 <span data-ttu-id="7a59a-114">**Nagłówek:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="7a59a-114">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7a59a-115">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="7a59a-115">See also</span></span>
- [<span data-ttu-id="7a59a-116">ISymUnmanagedWriter, interfejs</span><span class="sxs-lookup"><span data-stu-id="7a59a-116">ISymUnmanagedWriter Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-interface.md)
- [<span data-ttu-id="7a59a-117">CloseMethod, metoda</span><span class="sxs-lookup"><span data-stu-id="7a59a-117">CloseMethod Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-closemethod-method.md)
- [<span data-ttu-id="7a59a-118">OpenMethod2, metoda</span><span class="sxs-lookup"><span data-stu-id="7a59a-118">OpenMethod2 Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter3-openmethod2-method.md)
