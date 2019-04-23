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
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59228162"
---
# <a name="isymunmanagedscope-interface"></a><span data-ttu-id="e60a0-102">ISymUnmanagedScope — Interfejs</span><span class="sxs-lookup"><span data-stu-id="e60a0-102">ISymUnmanagedScope Interface</span></span>
<span data-ttu-id="e60a0-103">Reprezentuje zakresie leksykalnym wewnątrz metody.</span><span class="sxs-lookup"><span data-stu-id="e60a0-103">Represents a lexical scope within a method.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="e60a0-104">Metody</span><span class="sxs-lookup"><span data-stu-id="e60a0-104">Methods</span></span>  
  
|<span data-ttu-id="e60a0-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="e60a0-105">Method</span></span>|<span data-ttu-id="e60a0-106">Opis</span><span class="sxs-lookup"><span data-stu-id="e60a0-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="e60a0-107">GetChildren, metoda</span><span class="sxs-lookup"><span data-stu-id="e60a0-107">GetChildren Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedscope-getchildren-method.md)|<span data-ttu-id="e60a0-108">Pobiera elementy podrzędne tego zakresu.</span><span class="sxs-lookup"><span data-stu-id="e60a0-108">Gets the children of this scope.</span></span>|  
|[<span data-ttu-id="e60a0-109">GetEndOffset, metoda</span><span class="sxs-lookup"><span data-stu-id="e60a0-109">GetEndOffset Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedscope-getendoffset-method.md)|<span data-ttu-id="e60a0-110">Pobiera wartość przesunięcia końcowego dla tego zakresu.</span><span class="sxs-lookup"><span data-stu-id="e60a0-110">Gets the end offset for this scope.</span></span>|  
|[<span data-ttu-id="e60a0-111">GetLocalCount, metoda</span><span class="sxs-lookup"><span data-stu-id="e60a0-111">GetLocalCount Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedscope-getlocalcount-method.md)|<span data-ttu-id="e60a0-112">Pobiera liczbę zmiennych lokalnych zdefiniowanych w tym zakresie.</span><span class="sxs-lookup"><span data-stu-id="e60a0-112">Gets a count of the local variables defined within this scope.</span></span>|  
|[<span data-ttu-id="e60a0-113">GetLocals, metoda</span><span class="sxs-lookup"><span data-stu-id="e60a0-113">GetLocals Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedscope-getlocals-method.md)|<span data-ttu-id="e60a0-114">Pobiera zmienne lokalne zdefiniowane w tym zakresie.</span><span class="sxs-lookup"><span data-stu-id="e60a0-114">Gets the local variables defined within this scope.</span></span>|  
|[<span data-ttu-id="e60a0-115">GetMethod, metoda</span><span class="sxs-lookup"><span data-stu-id="e60a0-115">GetMethod Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedscope-getmethod-method.md)|<span data-ttu-id="e60a0-116">Pobiera metodę, która zawiera ten zakres.</span><span class="sxs-lookup"><span data-stu-id="e60a0-116">Gets the method that contains this scope.</span></span>|  
|[<span data-ttu-id="e60a0-117">GetNamespaces, metoda</span><span class="sxs-lookup"><span data-stu-id="e60a0-117">GetNamespaces Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedscope-getnamespaces-method.md)|<span data-ttu-id="e60a0-118">Pobiera przestrzenie nazw, które są używane w tym zakresie.</span><span class="sxs-lookup"><span data-stu-id="e60a0-118">Gets the namespaces that are being used within this scope.</span></span>|  
|[<span data-ttu-id="e60a0-119">GetParent, metoda</span><span class="sxs-lookup"><span data-stu-id="e60a0-119">GetParent Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedscope-getparent-method.md)|<span data-ttu-id="e60a0-120">Pobiera zakres nadrzędny tego zakresu.</span><span class="sxs-lookup"><span data-stu-id="e60a0-120">Gets the parent scope of this scope.</span></span>|  
|[<span data-ttu-id="e60a0-121">GetStartOffset, metoda</span><span class="sxs-lookup"><span data-stu-id="e60a0-121">GetStartOffset Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedscope-getstartoffset-method.md)|<span data-ttu-id="e60a0-122">Pobiera Przesunięcie początkowe dla tego zakresu.</span><span class="sxs-lookup"><span data-stu-id="e60a0-122">Gets the start offset for this scope.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="e60a0-123">Wymagania</span><span class="sxs-lookup"><span data-stu-id="e60a0-123">Requirements</span></span>  
 <span data-ttu-id="e60a0-124">**Nagłówek:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="e60a0-124">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e60a0-125">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="e60a0-125">See also</span></span>

- [<span data-ttu-id="e60a0-126">Interfejsy magazynu symboli diagnostycznych</span><span class="sxs-lookup"><span data-stu-id="e60a0-126">Diagnostics Symbol Store Interfaces</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/diagnostics-symbol-store-interfaces.md)
- [<span data-ttu-id="e60a0-127">ISymUnmanagedScope2, interfejs</span><span class="sxs-lookup"><span data-stu-id="e60a0-127">ISymUnmanagedScope2 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedscope2-interface.md)
