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
ms.openlocfilehash: 965e8058d44ebb5dc87ade3b6025c6291a9c3bcd
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54492131"
---
# <a name="isymunmanagedscope-interface"></a><span data-ttu-id="ee683-102">ISymUnmanagedScope — Interfejs</span><span class="sxs-lookup"><span data-stu-id="ee683-102">ISymUnmanagedScope Interface</span></span>
<span data-ttu-id="ee683-103">Reprezentuje zakresie leksykalnym wewnątrz metody.</span><span class="sxs-lookup"><span data-stu-id="ee683-103">Represents a lexical scope within a method.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="ee683-104">Metody</span><span class="sxs-lookup"><span data-stu-id="ee683-104">Methods</span></span>  
  
|<span data-ttu-id="ee683-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="ee683-105">Method</span></span>|<span data-ttu-id="ee683-106">Opis</span><span class="sxs-lookup"><span data-stu-id="ee683-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="ee683-107">GetChildren, metoda</span><span class="sxs-lookup"><span data-stu-id="ee683-107">GetChildren Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedscope-getchildren-method.md)|<span data-ttu-id="ee683-108">Pobiera elementy podrzędne tego zakresu.</span><span class="sxs-lookup"><span data-stu-id="ee683-108">Gets the children of this scope.</span></span>|  
|[<span data-ttu-id="ee683-109">GetEndOffset, metoda</span><span class="sxs-lookup"><span data-stu-id="ee683-109">GetEndOffset Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedscope-getendoffset-method.md)|<span data-ttu-id="ee683-110">Pobiera wartość przesunięcia końcowego dla tego zakresu.</span><span class="sxs-lookup"><span data-stu-id="ee683-110">Gets the end offset for this scope.</span></span>|  
|[<span data-ttu-id="ee683-111">GetLocalCount, metoda</span><span class="sxs-lookup"><span data-stu-id="ee683-111">GetLocalCount Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedscope-getlocalcount-method.md)|<span data-ttu-id="ee683-112">Pobiera liczbę zmiennych lokalnych zdefiniowanych w tym zakresie.</span><span class="sxs-lookup"><span data-stu-id="ee683-112">Gets a count of the local variables defined within this scope.</span></span>|  
|[<span data-ttu-id="ee683-113">GetLocals, metoda</span><span class="sxs-lookup"><span data-stu-id="ee683-113">GetLocals Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedscope-getlocals-method.md)|<span data-ttu-id="ee683-114">Pobiera zmienne lokalne zdefiniowane w tym zakresie.</span><span class="sxs-lookup"><span data-stu-id="ee683-114">Gets the local variables defined within this scope.</span></span>|  
|[<span data-ttu-id="ee683-115">GetMethod, metoda</span><span class="sxs-lookup"><span data-stu-id="ee683-115">GetMethod Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedscope-getmethod-method.md)|<span data-ttu-id="ee683-116">Pobiera metodę, która zawiera ten zakres.</span><span class="sxs-lookup"><span data-stu-id="ee683-116">Gets the method that contains this scope.</span></span>|  
|[<span data-ttu-id="ee683-117">GetNamespaces, metoda</span><span class="sxs-lookup"><span data-stu-id="ee683-117">GetNamespaces Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedscope-getnamespaces-method.md)|<span data-ttu-id="ee683-118">Pobiera przestrzenie nazw, które są używane w tym zakresie.</span><span class="sxs-lookup"><span data-stu-id="ee683-118">Gets the namespaces that are being used within this scope.</span></span>|  
|[<span data-ttu-id="ee683-119">GetParent, metoda</span><span class="sxs-lookup"><span data-stu-id="ee683-119">GetParent Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedscope-getparent-method.md)|<span data-ttu-id="ee683-120">Pobiera zakres nadrzędny tego zakresu.</span><span class="sxs-lookup"><span data-stu-id="ee683-120">Gets the parent scope of this scope.</span></span>|  
|[<span data-ttu-id="ee683-121">GetStartOffset, metoda</span><span class="sxs-lookup"><span data-stu-id="ee683-121">GetStartOffset Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedscope-getstartoffset-method.md)|<span data-ttu-id="ee683-122">Pobiera Przesunięcie początkowe dla tego zakresu.</span><span class="sxs-lookup"><span data-stu-id="ee683-122">Gets the start offset for this scope.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="ee683-123">Wymagania</span><span class="sxs-lookup"><span data-stu-id="ee683-123">Requirements</span></span>  
 <span data-ttu-id="ee683-124">**Nagłówek:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="ee683-124">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ee683-125">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="ee683-125">See also</span></span>
- [<span data-ttu-id="ee683-126">Interfejsy magazynu symboli diagnostycznych</span><span class="sxs-lookup"><span data-stu-id="ee683-126">Diagnostics Symbol Store Interfaces</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/diagnostics-symbol-store-interfaces.md)
- [<span data-ttu-id="ee683-127">ISymUnmanagedScope2, interfejs</span><span class="sxs-lookup"><span data-stu-id="ee683-127">ISymUnmanagedScope2 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedscope2-interface.md)
