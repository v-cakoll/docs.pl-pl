---
title: ISymUnmanagedScope2 — Interfejs
ms.date: 03/30/2017
api_name:
- ISymUnmanagedScope2
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedScope2
helpviewer_keywords:
- ISymUnmanagedScope2 interface [.NET Framework debugging]
ms.assetid: 2ed6a387-ba45-483e-9a1e-b0c69f67998b
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: beb48835039f142ea1d9e18871f77ada1b6f4f3e
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54706316"
---
# <a name="isymunmanagedscope2-interface"></a><span data-ttu-id="fcadb-102">ISymUnmanagedScope2 — Interfejs</span><span class="sxs-lookup"><span data-stu-id="fcadb-102">ISymUnmanagedScope2 Interface</span></span>
<span data-ttu-id="fcadb-103">Reprezentuje zakresie leksykalnym wewnątrz metody.</span><span class="sxs-lookup"><span data-stu-id="fcadb-103">Represents a lexical scope within a method.</span></span> <span data-ttu-id="fcadb-104">Ten interfejs rozszerza [isymunmanagedscope —](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedscope-interface.md) interfejs, za pomocą metod, które uzyskać informacje na temat stałe zdefiniowane w zakresie.</span><span class="sxs-lookup"><span data-stu-id="fcadb-104">This interface extends the [ISymUnmanagedScope](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedscope-interface.md) interface with methods that get information about constants defined within the scope.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="fcadb-105">Metody</span><span class="sxs-lookup"><span data-stu-id="fcadb-105">Methods</span></span>  
  
|<span data-ttu-id="fcadb-106">Metoda</span><span class="sxs-lookup"><span data-stu-id="fcadb-106">Method</span></span>|<span data-ttu-id="fcadb-107">Opis</span><span class="sxs-lookup"><span data-stu-id="fcadb-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="fcadb-108">GetConstantCount, metoda</span><span class="sxs-lookup"><span data-stu-id="fcadb-108">GetConstantCount Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedscope2-getconstantcount-method.md)|<span data-ttu-id="fcadb-109">Pobiera liczbę stałe zdefiniowane w tym zakresie.</span><span class="sxs-lookup"><span data-stu-id="fcadb-109">Gets a count of the constants defined within this scope.</span></span>|  
|[<span data-ttu-id="fcadb-110">GetConstants, metoda</span><span class="sxs-lookup"><span data-stu-id="fcadb-110">GetConstants Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedscope2-getconstants-method.md)|<span data-ttu-id="fcadb-111">Pobiera lokalne stałe zdefiniowane w tym zakresie.</span><span class="sxs-lookup"><span data-stu-id="fcadb-111">Gets the local constants defined within this scope.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="fcadb-112">Wymagania</span><span class="sxs-lookup"><span data-stu-id="fcadb-112">Requirements</span></span>  
 <span data-ttu-id="fcadb-113">**Nagłówek:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="fcadb-113">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fcadb-114">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="fcadb-114">See also</span></span>
- [<span data-ttu-id="fcadb-115">Interfejsy magazynu symboli diagnostycznych</span><span class="sxs-lookup"><span data-stu-id="fcadb-115">Diagnostics Symbol Store Interfaces</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/diagnostics-symbol-store-interfaces.md)
- [<span data-ttu-id="fcadb-116">ISymUnmanagedScope, interfejs</span><span class="sxs-lookup"><span data-stu-id="fcadb-116">ISymUnmanagedScope Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedscope-interface.md)
