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
ms.openlocfilehash: b05ba185a9ad4ab076d29d7d609734d41677b760
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61986053"
---
# <a name="isymunmanagedwriteropenmethod-method"></a><span data-ttu-id="27896-102">ISymUnmanagedWriter::OpenMethod — Metoda</span><span class="sxs-lookup"><span data-stu-id="27896-102">ISymUnmanagedWriter::OpenMethod Method</span></span>
<span data-ttu-id="27896-103">Zostanie otwarty metody, w której symbol informacje są emitowane.</span><span class="sxs-lookup"><span data-stu-id="27896-103">Opens a method into which symbol information is emitted.</span></span> <span data-ttu-id="27896-104">Danej metody staje się bieżącą metodę dla wywołań do definiowania punktów sekwencji, parametrów i leksykalne zakresów.</span><span class="sxs-lookup"><span data-stu-id="27896-104">The given method becomes the current method for calls to define sequence points, parameters, and lexical scopes.</span></span> <span data-ttu-id="27896-105">Istnieje niejawna zakresie leksykalnym, wokół całej metody.</span><span class="sxs-lookup"><span data-stu-id="27896-105">There is an implicit lexical scope around the entire method.</span></span> <span data-ttu-id="27896-106">Zamknij metodę, która została wcześniej zamknięta usuwa wszystkie uprzednio zdefiniowany symboli dla tej metody.</span><span class="sxs-lookup"><span data-stu-id="27896-106">Reopening a method that was previously closed erases any previously defined symbols for that method.</span></span> <span data-ttu-id="27896-107">Jednocześnie może istnieć tylko jedna metoda open.</span><span class="sxs-lookup"><span data-stu-id="27896-107">There can be only one open method at a time.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="27896-108">Składnia</span><span class="sxs-lookup"><span data-stu-id="27896-108">Syntax</span></span>  
  
```  
HRESULT OpenMethod(  
    [in] mdMethodDef method);  
```  
  
## <a name="parameters"></a><span data-ttu-id="27896-109">Parametry</span><span class="sxs-lookup"><span data-stu-id="27896-109">Parameters</span></span>  
 `method`  
 <span data-ttu-id="27896-110">[in] Token metadanych dla metody, które ma zostać otwarty.</span><span class="sxs-lookup"><span data-stu-id="27896-110">[in] The metadata token for the method to be opened.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="27896-111">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="27896-111">Return Value</span></span>  
 <span data-ttu-id="27896-112">S_OK, jeśli metoda się powiedzie; w przeciwnym razie E_FAIL lub innego kodu błędu.</span><span class="sxs-lookup"><span data-stu-id="27896-112">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="27896-113">Wymagania</span><span class="sxs-lookup"><span data-stu-id="27896-113">Requirements</span></span>  
 <span data-ttu-id="27896-114">**Nagłówek:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="27896-114">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="27896-115">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="27896-115">See also</span></span>

- [<span data-ttu-id="27896-116">ISymUnmanagedWriter, interfejs</span><span class="sxs-lookup"><span data-stu-id="27896-116">ISymUnmanagedWriter Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-interface.md)
- [<span data-ttu-id="27896-117">CloseMethod, metoda</span><span class="sxs-lookup"><span data-stu-id="27896-117">CloseMethod Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-closemethod-method.md)
- [<span data-ttu-id="27896-118">OpenMethod2, metoda</span><span class="sxs-lookup"><span data-stu-id="27896-118">OpenMethod2 Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter3-openmethod2-method.md)
