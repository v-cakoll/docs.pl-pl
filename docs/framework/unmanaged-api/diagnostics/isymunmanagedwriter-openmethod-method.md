---
title: "ISymUnmanagedWriter::OpenMethod — Metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ISymUnmanagedWriter.OpenMethod
api_location: diasymreader.dll
api_type: COM
f1_keywords: ISymUnmanagedWriter::OpenMethod
helpviewer_keywords:
- ISymUnmanagedWriter::OpenMethod method [.NET Framework debugging]
- OpenMethod method [.NET Framework debugging]
ms.assetid: fb90cb7f-af88-45e8-a99f-80a0bbddb08b
topic_type: apiref
caps.latest.revision: "7"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 61d63fb96635e34e07c3997c1aad838e67c70742
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="isymunmanagedwriteropenmethod-method"></a><span data-ttu-id="4425c-102">ISymUnmanagedWriter::OpenMethod — Metoda</span><span class="sxs-lookup"><span data-stu-id="4425c-102">ISymUnmanagedWriter::OpenMethod Method</span></span>
<span data-ttu-id="4425c-103">Zostanie otwarty w którym symbol informacje są emitowane metody.</span><span class="sxs-lookup"><span data-stu-id="4425c-103">Opens a method into which symbol information is emitted.</span></span> <span data-ttu-id="4425c-104">Podanej metody staje się bieżącej metody dla wywołania do definiowania punkty sekwencji, parametrów i leksykalne zakresów.</span><span class="sxs-lookup"><span data-stu-id="4425c-104">The given method becomes the current method for calls to define sequence points, parameters, and lexical scopes.</span></span> <span data-ttu-id="4425c-105">Istnieje niejawna zakres leksykalne wokół całej metody.</span><span class="sxs-lookup"><span data-stu-id="4425c-105">There is an implicit lexical scope around the entire method.</span></span> <span data-ttu-id="4425c-106">Otworzyć ponownie metodę, która została wcześniej zamknięta usuwa żadnych wcześniej zdefiniowanych symboli dla tej metody.</span><span class="sxs-lookup"><span data-stu-id="4425c-106">Reopening a method that was previously closed erases any previously defined symbols for that method.</span></span> <span data-ttu-id="4425c-107">Jednocześnie może istnieć tylko jedna metoda open.</span><span class="sxs-lookup"><span data-stu-id="4425c-107">There can be only one open method at a time.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4425c-108">Składnia</span><span class="sxs-lookup"><span data-stu-id="4425c-108">Syntax</span></span>  
  
```  
HRESULT OpenMethod(  
    [in] mdMethodDef method);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="4425c-109">Parametry</span><span class="sxs-lookup"><span data-stu-id="4425c-109">Parameters</span></span>  
 `method`  
 <span data-ttu-id="4425c-110">[in] Token metadanych metody, która ma zostać otwarty.</span><span class="sxs-lookup"><span data-stu-id="4425c-110">[in] The metadata token for the method to be opened.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="4425c-111">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="4425c-111">Return Value</span></span>  
 <span data-ttu-id="4425c-112">Wartość S_OK, jeśli metoda zakończy się pomyślnie; w przeciwnym razie E_FAIL lub inny kod błędu.</span><span class="sxs-lookup"><span data-stu-id="4425c-112">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4425c-113">Wymagania</span><span class="sxs-lookup"><span data-stu-id="4425c-113">Requirements</span></span>  
 <span data-ttu-id="4425c-114">**Nagłówek:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="4425c-114">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4425c-115">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="4425c-115">See Also</span></span>  
 [<span data-ttu-id="4425c-116">ISymUnmanagedWriter — interfejs</span><span class="sxs-lookup"><span data-stu-id="4425c-116">ISymUnmanagedWriter Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-interface.md)  
 [<span data-ttu-id="4425c-117">CloseMethod — metoda</span><span class="sxs-lookup"><span data-stu-id="4425c-117">CloseMethod Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-closemethod-method.md)  
 [<span data-ttu-id="4425c-118">OpenMethod2 — metoda</span><span class="sxs-lookup"><span data-stu-id="4425c-118">OpenMethod2 Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter3-openmethod2-method.md)
