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
ms.openlocfilehash: bc41acd6a4f2ef2557d3b39523c5e398c887c454
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33427911"
---
# <a name="isymunmanagedwriteropenmethod-method"></a><span data-ttu-id="c07ca-102">ISymUnmanagedWriter::OpenMethod — Metoda</span><span class="sxs-lookup"><span data-stu-id="c07ca-102">ISymUnmanagedWriter::OpenMethod Method</span></span>
<span data-ttu-id="c07ca-103">Zostanie otwarty w którym symbol informacje są emitowane metody.</span><span class="sxs-lookup"><span data-stu-id="c07ca-103">Opens a method into which symbol information is emitted.</span></span> <span data-ttu-id="c07ca-104">Podanej metody staje się bieżącej metody dla wywołania do definiowania punkty sekwencji, parametrów i leksykalne zakresów.</span><span class="sxs-lookup"><span data-stu-id="c07ca-104">The given method becomes the current method for calls to define sequence points, parameters, and lexical scopes.</span></span> <span data-ttu-id="c07ca-105">Istnieje niejawna zakres leksykalne wokół całej metody.</span><span class="sxs-lookup"><span data-stu-id="c07ca-105">There is an implicit lexical scope around the entire method.</span></span> <span data-ttu-id="c07ca-106">Otworzyć ponownie metodę, która została wcześniej zamknięta usuwa żadnych wcześniej zdefiniowanych symboli dla tej metody.</span><span class="sxs-lookup"><span data-stu-id="c07ca-106">Reopening a method that was previously closed erases any previously defined symbols for that method.</span></span> <span data-ttu-id="c07ca-107">Jednocześnie może istnieć tylko jedna metoda open.</span><span class="sxs-lookup"><span data-stu-id="c07ca-107">There can be only one open method at a time.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c07ca-108">Składnia</span><span class="sxs-lookup"><span data-stu-id="c07ca-108">Syntax</span></span>  
  
```  
HRESULT OpenMethod(  
    [in] mdMethodDef method);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="c07ca-109">Parametry</span><span class="sxs-lookup"><span data-stu-id="c07ca-109">Parameters</span></span>  
 `method`  
 <span data-ttu-id="c07ca-110">[in] Token metadanych metody, która ma zostać otwarty.</span><span class="sxs-lookup"><span data-stu-id="c07ca-110">[in] The metadata token for the method to be opened.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="c07ca-111">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="c07ca-111">Return Value</span></span>  
 <span data-ttu-id="c07ca-112">Wartość S_OK, jeśli metoda zakończy się pomyślnie; w przeciwnym razie E_FAIL lub inny kod błędu.</span><span class="sxs-lookup"><span data-stu-id="c07ca-112">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c07ca-113">Wymagania</span><span class="sxs-lookup"><span data-stu-id="c07ca-113">Requirements</span></span>  
 <span data-ttu-id="c07ca-114">**Header:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="c07ca-114">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c07ca-115">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="c07ca-115">See Also</span></span>  
 [<span data-ttu-id="c07ca-116">ISymUnmanagedWriter, interfejs</span><span class="sxs-lookup"><span data-stu-id="c07ca-116">ISymUnmanagedWriter Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-interface.md)  
 [<span data-ttu-id="c07ca-117">CloseMethod, metoda</span><span class="sxs-lookup"><span data-stu-id="c07ca-117">CloseMethod Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-closemethod-method.md)  
 [<span data-ttu-id="c07ca-118">OpenMethod2, metoda</span><span class="sxs-lookup"><span data-stu-id="c07ca-118">OpenMethod2 Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter3-openmethod2-method.md)
