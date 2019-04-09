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
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59131459"
---
# <a name="isymunmanagedscope2-interface"></a><span data-ttu-id="52b2f-102">ISymUnmanagedScope2 — Interfejs</span><span class="sxs-lookup"><span data-stu-id="52b2f-102">ISymUnmanagedScope2 Interface</span></span>
<span data-ttu-id="52b2f-103">Reprezentuje zakresie leksykalnym wewnątrz metody.</span><span class="sxs-lookup"><span data-stu-id="52b2f-103">Represents a lexical scope within a method.</span></span> <span data-ttu-id="52b2f-104">Ten interfejs rozszerza [isymunmanagedscope —](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedscope-interface.md) interfejs, za pomocą metod, które uzyskać informacje na temat stałe zdefiniowane w zakresie.</span><span class="sxs-lookup"><span data-stu-id="52b2f-104">This interface extends the [ISymUnmanagedScope](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedscope-interface.md) interface with methods that get information about constants defined within the scope.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="52b2f-105">Metody</span><span class="sxs-lookup"><span data-stu-id="52b2f-105">Methods</span></span>  
  
|<span data-ttu-id="52b2f-106">Metoda</span><span class="sxs-lookup"><span data-stu-id="52b2f-106">Method</span></span>|<span data-ttu-id="52b2f-107">Opis</span><span class="sxs-lookup"><span data-stu-id="52b2f-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="52b2f-108">GetConstantCount, metoda</span><span class="sxs-lookup"><span data-stu-id="52b2f-108">GetConstantCount Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedscope2-getconstantcount-method.md)|<span data-ttu-id="52b2f-109">Pobiera liczbę stałe zdefiniowane w tym zakresie.</span><span class="sxs-lookup"><span data-stu-id="52b2f-109">Gets a count of the constants defined within this scope.</span></span>|  
|[<span data-ttu-id="52b2f-110">GetConstants, metoda</span><span class="sxs-lookup"><span data-stu-id="52b2f-110">GetConstants Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedscope2-getconstants-method.md)|<span data-ttu-id="52b2f-111">Pobiera lokalne stałe zdefiniowane w tym zakresie.</span><span class="sxs-lookup"><span data-stu-id="52b2f-111">Gets the local constants defined within this scope.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="52b2f-112">Wymagania</span><span class="sxs-lookup"><span data-stu-id="52b2f-112">Requirements</span></span>  
 <span data-ttu-id="52b2f-113">**Nagłówek:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="52b2f-113">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="52b2f-114">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="52b2f-114">See also</span></span>

- [<span data-ttu-id="52b2f-115">Interfejsy magazynu symboli diagnostycznych</span><span class="sxs-lookup"><span data-stu-id="52b2f-115">Diagnostics Symbol Store Interfaces</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/diagnostics-symbol-store-interfaces.md)
- [<span data-ttu-id="52b2f-116">ISymUnmanagedScope — Interfejs</span><span class="sxs-lookup"><span data-stu-id="52b2f-116">ISymUnmanagedScope Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedscope-interface.md)
