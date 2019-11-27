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
ms.openlocfilehash: 8da4da38d23ed65a0fdc44a0f919ee8cad2fe18e
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/23/2019
ms.locfileid: "74446264"
---
# <a name="isymunmanagedscope-interface"></a><span data-ttu-id="310f7-102">ISymUnmanagedScope — Interfejs</span><span class="sxs-lookup"><span data-stu-id="310f7-102">ISymUnmanagedScope Interface</span></span>
<span data-ttu-id="310f7-103">Reprezentuje zakres leksykalny w ramach metody.</span><span class="sxs-lookup"><span data-stu-id="310f7-103">Represents a lexical scope within a method.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="310f7-104">Metody</span><span class="sxs-lookup"><span data-stu-id="310f7-104">Methods</span></span>  
  
|<span data-ttu-id="310f7-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="310f7-105">Method</span></span>|<span data-ttu-id="310f7-106">Opis</span><span class="sxs-lookup"><span data-stu-id="310f7-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="310f7-107">GetChildren, metoda</span><span class="sxs-lookup"><span data-stu-id="310f7-107">GetChildren Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedscope-getchildren-method.md)|<span data-ttu-id="310f7-108">Pobiera elementy podrzędne tego zakresu.</span><span class="sxs-lookup"><span data-stu-id="310f7-108">Gets the children of this scope.</span></span>|  
|[<span data-ttu-id="310f7-109">GetEndOffset, metoda</span><span class="sxs-lookup"><span data-stu-id="310f7-109">GetEndOffset Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedscope-getendoffset-method.md)|<span data-ttu-id="310f7-110">Pobiera przesunięcie końca dla tego zakresu.</span><span class="sxs-lookup"><span data-stu-id="310f7-110">Gets the end offset for this scope.</span></span>|  
|[<span data-ttu-id="310f7-111">GetLocalCount, metoda</span><span class="sxs-lookup"><span data-stu-id="310f7-111">GetLocalCount Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedscope-getlocalcount-method.md)|<span data-ttu-id="310f7-112">Pobiera liczbę zmiennych lokalnych zdefiniowanych w tym zakresie.</span><span class="sxs-lookup"><span data-stu-id="310f7-112">Gets a count of the local variables defined within this scope.</span></span>|  
|[<span data-ttu-id="310f7-113">GetLocals, metoda</span><span class="sxs-lookup"><span data-stu-id="310f7-113">GetLocals Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedscope-getlocals-method.md)|<span data-ttu-id="310f7-114">Pobiera zmienne lokalne zdefiniowane w tym zakresie.</span><span class="sxs-lookup"><span data-stu-id="310f7-114">Gets the local variables defined within this scope.</span></span>|  
|[<span data-ttu-id="310f7-115">GetMethod, metoda</span><span class="sxs-lookup"><span data-stu-id="310f7-115">GetMethod Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedscope-getmethod-method.md)|<span data-ttu-id="310f7-116">Pobiera metodę, która zawiera ten zakres.</span><span class="sxs-lookup"><span data-stu-id="310f7-116">Gets the method that contains this scope.</span></span>|  
|[<span data-ttu-id="310f7-117">GetNamespaces, metoda</span><span class="sxs-lookup"><span data-stu-id="310f7-117">GetNamespaces Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedscope-getnamespaces-method.md)|<span data-ttu-id="310f7-118">Pobiera przestrzenie nazw, które są używane w tym zakresie.</span><span class="sxs-lookup"><span data-stu-id="310f7-118">Gets the namespaces that are being used within this scope.</span></span>|  
|[<span data-ttu-id="310f7-119">GetParent, metoda</span><span class="sxs-lookup"><span data-stu-id="310f7-119">GetParent Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedscope-getparent-method.md)|<span data-ttu-id="310f7-120">Pobiera zakres nadrzędny tego zakresu.</span><span class="sxs-lookup"><span data-stu-id="310f7-120">Gets the parent scope of this scope.</span></span>|  
|[<span data-ttu-id="310f7-121">GetStartOffset, metoda</span><span class="sxs-lookup"><span data-stu-id="310f7-121">GetStartOffset Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedscope-getstartoffset-method.md)|<span data-ttu-id="310f7-122">Pobiera przesunięcie początku dla tego zakresu.</span><span class="sxs-lookup"><span data-stu-id="310f7-122">Gets the start offset for this scope.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="310f7-123">Wymagania</span><span class="sxs-lookup"><span data-stu-id="310f7-123">Requirements</span></span>  
 <span data-ttu-id="310f7-124">**Nagłówek:** CorSym. idl, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="310f7-124">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="310f7-125">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="310f7-125">See also</span></span>

- [<span data-ttu-id="310f7-126">Interfejsy magazynu symboli diagnostycznych</span><span class="sxs-lookup"><span data-stu-id="310f7-126">Diagnostics Symbol Store Interfaces</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/diagnostics-symbol-store-interfaces.md)
- [<span data-ttu-id="310f7-127">ISymUnmanagedScope2, interfejs</span><span class="sxs-lookup"><span data-stu-id="310f7-127">ISymUnmanagedScope2 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedscope2-interface.md)
