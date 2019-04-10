---
title: ISymUnmanagedScope — Interfejs
ms.date: 03/30/2017
api_name:
- ISymUnmanagedScope
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedScope
helpviewer_keywords:
- ISymUnmanagedScope interface [.NET Framework debugging]
ms.assetid: 3db7a220-cfe9-4810-8ca8-a094bb8e0f5b
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 809368ea19528a7ce00d4fcada06ef5724eb79a6
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59228162"
---
# <a name="isymunmanagedscope-interface"></a><span data-ttu-id="58cf7-102">ISymUnmanagedScope — Interfejs</span><span class="sxs-lookup"><span data-stu-id="58cf7-102">ISymUnmanagedScope Interface</span></span>
<span data-ttu-id="58cf7-103">Reprezentuje zakresie leksykalnym wewnątrz metody.</span><span class="sxs-lookup"><span data-stu-id="58cf7-103">Represents a lexical scope within a method.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="58cf7-104">Metody</span><span class="sxs-lookup"><span data-stu-id="58cf7-104">Methods</span></span>  
  
|<span data-ttu-id="58cf7-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="58cf7-105">Method</span></span>|<span data-ttu-id="58cf7-106">Opis</span><span class="sxs-lookup"><span data-stu-id="58cf7-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="58cf7-107">GetChildren, metoda</span><span class="sxs-lookup"><span data-stu-id="58cf7-107">GetChildren Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedscope-getchildren-method.md)|<span data-ttu-id="58cf7-108">Pobiera elementy podrzędne tego zakresu.</span><span class="sxs-lookup"><span data-stu-id="58cf7-108">Gets the children of this scope.</span></span>|  
|[<span data-ttu-id="58cf7-109">GetEndOffset, metoda</span><span class="sxs-lookup"><span data-stu-id="58cf7-109">GetEndOffset Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedscope-getendoffset-method.md)|<span data-ttu-id="58cf7-110">Pobiera wartość przesunięcia końcowego dla tego zakresu.</span><span class="sxs-lookup"><span data-stu-id="58cf7-110">Gets the end offset for this scope.</span></span>|  
|[<span data-ttu-id="58cf7-111">GetLocalCount, metoda</span><span class="sxs-lookup"><span data-stu-id="58cf7-111">GetLocalCount Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedscope-getlocalcount-method.md)|<span data-ttu-id="58cf7-112">Pobiera liczbę zmiennych lokalnych zdefiniowanych w tym zakresie.</span><span class="sxs-lookup"><span data-stu-id="58cf7-112">Gets a count of the local variables defined within this scope.</span></span>|  
|[<span data-ttu-id="58cf7-113">GetLocals, metoda</span><span class="sxs-lookup"><span data-stu-id="58cf7-113">GetLocals Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedscope-getlocals-method.md)|<span data-ttu-id="58cf7-114">Pobiera zmienne lokalne zdefiniowane w tym zakresie.</span><span class="sxs-lookup"><span data-stu-id="58cf7-114">Gets the local variables defined within this scope.</span></span>|  
|[<span data-ttu-id="58cf7-115">GetMethod, metoda</span><span class="sxs-lookup"><span data-stu-id="58cf7-115">GetMethod Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedscope-getmethod-method.md)|<span data-ttu-id="58cf7-116">Pobiera metodę, która zawiera ten zakres.</span><span class="sxs-lookup"><span data-stu-id="58cf7-116">Gets the method that contains this scope.</span></span>|  
|[<span data-ttu-id="58cf7-117">GetNamespaces, metoda</span><span class="sxs-lookup"><span data-stu-id="58cf7-117">GetNamespaces Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedscope-getnamespaces-method.md)|<span data-ttu-id="58cf7-118">Pobiera przestrzenie nazw, które są używane w tym zakresie.</span><span class="sxs-lookup"><span data-stu-id="58cf7-118">Gets the namespaces that are being used within this scope.</span></span>|  
|[<span data-ttu-id="58cf7-119">GetParent, metoda</span><span class="sxs-lookup"><span data-stu-id="58cf7-119">GetParent Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedscope-getparent-method.md)|<span data-ttu-id="58cf7-120">Pobiera zakres nadrzędny tego zakresu.</span><span class="sxs-lookup"><span data-stu-id="58cf7-120">Gets the parent scope of this scope.</span></span>|  
|[<span data-ttu-id="58cf7-121">GetStartOffset, metoda</span><span class="sxs-lookup"><span data-stu-id="58cf7-121">GetStartOffset Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedscope-getstartoffset-method.md)|<span data-ttu-id="58cf7-122">Pobiera Przesunięcie początkowe dla tego zakresu.</span><span class="sxs-lookup"><span data-stu-id="58cf7-122">Gets the start offset for this scope.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="58cf7-123">Wymagania</span><span class="sxs-lookup"><span data-stu-id="58cf7-123">Requirements</span></span>  
 <span data-ttu-id="58cf7-124">**Nagłówek:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="58cf7-124">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="58cf7-125">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="58cf7-125">See also</span></span>

- [<span data-ttu-id="58cf7-126">Interfejsy magazynu symboli diagnostycznych</span><span class="sxs-lookup"><span data-stu-id="58cf7-126">Diagnostics Symbol Store Interfaces</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/diagnostics-symbol-store-interfaces.md)
- [<span data-ttu-id="58cf7-127">ISymUnmanagedScope2 — Interfejs</span><span class="sxs-lookup"><span data-stu-id="58cf7-127">ISymUnmanagedScope2 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedscope2-interface.md)
