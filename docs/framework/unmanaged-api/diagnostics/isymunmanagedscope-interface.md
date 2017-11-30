---
title: "ISymUnmanagedScope — Interfejs"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ISymUnmanagedScope
api_location: diasymreader.dll
api_type: COM
f1_keywords: ISymUnmanagedScope
helpviewer_keywords: ISymUnmanagedScope interface [.NET Framework debugging]
ms.assetid: 3db7a220-cfe9-4810-8ca8-a094bb8e0f5b
topic_type: apiref
caps.latest.revision: "5"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: d25d62dd42e3e93124c9a3bd8945be265f192663
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="isymunmanagedscope-interface"></a><span data-ttu-id="c375c-102">ISymUnmanagedScope — Interfejs</span><span class="sxs-lookup"><span data-stu-id="c375c-102">ISymUnmanagedScope Interface</span></span>
<span data-ttu-id="c375c-103">Reprezentuje leksykalne zakresu w metodzie.</span><span class="sxs-lookup"><span data-stu-id="c375c-103">Represents a lexical scope within a method.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="c375c-104">Metody</span><span class="sxs-lookup"><span data-stu-id="c375c-104">Methods</span></span>  
  
|<span data-ttu-id="c375c-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="c375c-105">Method</span></span>|<span data-ttu-id="c375c-106">Opis</span><span class="sxs-lookup"><span data-stu-id="c375c-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="c375c-107">GetChildren — metoda</span><span class="sxs-lookup"><span data-stu-id="c375c-107">GetChildren Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedscope-getchildren-method.md)|<span data-ttu-id="c375c-108">Pobiera elementy podrzędne tego zakresu.</span><span class="sxs-lookup"><span data-stu-id="c375c-108">Gets the children of this scope.</span></span>|  
|[<span data-ttu-id="c375c-109">GetEndOffset — metoda</span><span class="sxs-lookup"><span data-stu-id="c375c-109">GetEndOffset Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedscope-getendoffset-method.md)|<span data-ttu-id="c375c-110">Pobiera przesunięcie zakończenia dla tego zakresu.</span><span class="sxs-lookup"><span data-stu-id="c375c-110">Gets the end offset for this scope.</span></span>|  
|[<span data-ttu-id="c375c-111">GetLocalCount — metoda</span><span class="sxs-lookup"><span data-stu-id="c375c-111">GetLocalCount Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedscope-getlocalcount-method.md)|<span data-ttu-id="c375c-112">Pobiera liczbę zmiennych lokalnych, zdefiniowanego w tym zakresie.</span><span class="sxs-lookup"><span data-stu-id="c375c-112">Gets a count of the local variables defined within this scope.</span></span>|  
|[<span data-ttu-id="c375c-113">GetLocals — metoda</span><span class="sxs-lookup"><span data-stu-id="c375c-113">GetLocals Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedscope-getlocals-method.md)|<span data-ttu-id="c375c-114">Pobiera zmienne lokalne, zdefiniowanego w tym zakresie.</span><span class="sxs-lookup"><span data-stu-id="c375c-114">Gets the local variables defined within this scope.</span></span>|  
|[<span data-ttu-id="c375c-115">GetMethod — metoda</span><span class="sxs-lookup"><span data-stu-id="c375c-115">GetMethod Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedscope-getmethod-method.md)|<span data-ttu-id="c375c-116">Pobiera metodę, która zawiera ten zakres.</span><span class="sxs-lookup"><span data-stu-id="c375c-116">Gets the method that contains this scope.</span></span>|  
|[<span data-ttu-id="c375c-117">GetNamespaces — metoda</span><span class="sxs-lookup"><span data-stu-id="c375c-117">GetNamespaces Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedscope-getnamespaces-method.md)|<span data-ttu-id="c375c-118">Pobiera przestrzenie nazw, które są używane w tym zakresie.</span><span class="sxs-lookup"><span data-stu-id="c375c-118">Gets the namespaces that are being used within this scope.</span></span>|  
|[<span data-ttu-id="c375c-119">GetParent — metoda</span><span class="sxs-lookup"><span data-stu-id="c375c-119">GetParent Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedscope-getparent-method.md)|<span data-ttu-id="c375c-120">Pobiera zakres nadrzędny tego zakresu.</span><span class="sxs-lookup"><span data-stu-id="c375c-120">Gets the parent scope of this scope.</span></span>|  
|[<span data-ttu-id="c375c-121">GetStartOffset — metoda</span><span class="sxs-lookup"><span data-stu-id="c375c-121">GetStartOffset Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedscope-getstartoffset-method.md)|<span data-ttu-id="c375c-122">Pobiera Przesunięcie początkowe dla tego zakresu.</span><span class="sxs-lookup"><span data-stu-id="c375c-122">Gets the start offset for this scope.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="c375c-123">Wymagania</span><span class="sxs-lookup"><span data-stu-id="c375c-123">Requirements</span></span>  
 <span data-ttu-id="c375c-124">**Nagłówek:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="c375c-124">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c375c-125">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="c375c-125">See Also</span></span>  
 [<span data-ttu-id="c375c-126">Interfejsy magazynu symboli diagnostycznych</span><span class="sxs-lookup"><span data-stu-id="c375c-126">Diagnostics Symbol Store Interfaces</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/diagnostics-symbol-store-interfaces.md)  
 [<span data-ttu-id="c375c-127">ISymUnmanagedScope2 — interfejs</span><span class="sxs-lookup"><span data-stu-id="c375c-127">ISymUnmanagedScope2 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedscope2-interface.md)
