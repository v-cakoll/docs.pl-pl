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
ms.openlocfilehash: 0109b25b1cdc42204fc4873577e495641c4ec4fd
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61761575"
---
# <a name="isymunmanagedscope2-interface"></a><span data-ttu-id="1ffc9-102">ISymUnmanagedScope2 — Interfejs</span><span class="sxs-lookup"><span data-stu-id="1ffc9-102">ISymUnmanagedScope2 Interface</span></span>
<span data-ttu-id="1ffc9-103">Reprezentuje zakresie leksykalnym wewnątrz metody.</span><span class="sxs-lookup"><span data-stu-id="1ffc9-103">Represents a lexical scope within a method.</span></span> <span data-ttu-id="1ffc9-104">Ten interfejs rozszerza [isymunmanagedscope —](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedscope-interface.md) interfejs, za pomocą metod, które uzyskać informacje na temat stałe zdefiniowane w zakresie.</span><span class="sxs-lookup"><span data-stu-id="1ffc9-104">This interface extends the [ISymUnmanagedScope](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedscope-interface.md) interface with methods that get information about constants defined within the scope.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="1ffc9-105">Metody</span><span class="sxs-lookup"><span data-stu-id="1ffc9-105">Methods</span></span>  
  
|<span data-ttu-id="1ffc9-106">Metoda</span><span class="sxs-lookup"><span data-stu-id="1ffc9-106">Method</span></span>|<span data-ttu-id="1ffc9-107">Opis</span><span class="sxs-lookup"><span data-stu-id="1ffc9-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="1ffc9-108">GetConstantCount, metoda</span><span class="sxs-lookup"><span data-stu-id="1ffc9-108">GetConstantCount Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedscope2-getconstantcount-method.md)|<span data-ttu-id="1ffc9-109">Pobiera liczbę stałe zdefiniowane w tym zakresie.</span><span class="sxs-lookup"><span data-stu-id="1ffc9-109">Gets a count of the constants defined within this scope.</span></span>|  
|[<span data-ttu-id="1ffc9-110">GetConstants, metoda</span><span class="sxs-lookup"><span data-stu-id="1ffc9-110">GetConstants Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedscope2-getconstants-method.md)|<span data-ttu-id="1ffc9-111">Pobiera lokalne stałe zdefiniowane w tym zakresie.</span><span class="sxs-lookup"><span data-stu-id="1ffc9-111">Gets the local constants defined within this scope.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="1ffc9-112">Wymagania</span><span class="sxs-lookup"><span data-stu-id="1ffc9-112">Requirements</span></span>  
 <span data-ttu-id="1ffc9-113">**Nagłówek:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="1ffc9-113">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1ffc9-114">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="1ffc9-114">See also</span></span>

- [<span data-ttu-id="1ffc9-115">Interfejsy magazynu symboli diagnostycznych</span><span class="sxs-lookup"><span data-stu-id="1ffc9-115">Diagnostics Symbol Store Interfaces</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/diagnostics-symbol-store-interfaces.md)
- [<span data-ttu-id="1ffc9-116">ISymUnmanagedScope, interfejs</span><span class="sxs-lookup"><span data-stu-id="1ffc9-116">ISymUnmanagedScope Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedscope-interface.md)
