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
ms.openlocfilehash: a33d8b489551dc69542e1b12bcf83602ec5a2008
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33427251"
---
# <a name="isymunmanagedscope2-interface"></a><span data-ttu-id="16c23-102">ISymUnmanagedScope2 — Interfejs</span><span class="sxs-lookup"><span data-stu-id="16c23-102">ISymUnmanagedScope2 Interface</span></span>
<span data-ttu-id="16c23-103">Reprezentuje leksykalne zakresu w metodzie.</span><span class="sxs-lookup"><span data-stu-id="16c23-103">Represents a lexical scope within a method.</span></span> <span data-ttu-id="16c23-104">Ten interfejs stanowi rozszerzenie [ISymUnmanagedScope](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedscope-interface.md) interfejs za pomocą metody pobierające informacje o stałych zdefiniowane w ramach zakresu.</span><span class="sxs-lookup"><span data-stu-id="16c23-104">This interface extends the [ISymUnmanagedScope](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedscope-interface.md) interface with methods that get information about constants defined within the scope.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="16c23-105">Metody</span><span class="sxs-lookup"><span data-stu-id="16c23-105">Methods</span></span>  
  
|<span data-ttu-id="16c23-106">Metoda</span><span class="sxs-lookup"><span data-stu-id="16c23-106">Method</span></span>|<span data-ttu-id="16c23-107">Opis</span><span class="sxs-lookup"><span data-stu-id="16c23-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="16c23-108">GetConstantCount, metoda</span><span class="sxs-lookup"><span data-stu-id="16c23-108">GetConstantCount Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedscope2-getconstantcount-method.md)|<span data-ttu-id="16c23-109">Pobiera liczbę stałe zdefiniowane w tym zakresie.</span><span class="sxs-lookup"><span data-stu-id="16c23-109">Gets a count of the constants defined within this scope.</span></span>|  
|[<span data-ttu-id="16c23-110">GetConstants, metoda</span><span class="sxs-lookup"><span data-stu-id="16c23-110">GetConstants Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedscope2-getconstants-method.md)|<span data-ttu-id="16c23-111">Pobiera lokalne stałe zdefiniowane w tym zakresie.</span><span class="sxs-lookup"><span data-stu-id="16c23-111">Gets the local constants defined within this scope.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="16c23-112">Wymagania</span><span class="sxs-lookup"><span data-stu-id="16c23-112">Requirements</span></span>  
 <span data-ttu-id="16c23-113">**Header:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="16c23-113">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="16c23-114">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="16c23-114">See Also</span></span>  
 [<span data-ttu-id="16c23-115">Interfejsy magazynu symboli diagnostycznych</span><span class="sxs-lookup"><span data-stu-id="16c23-115">Diagnostics Symbol Store Interfaces</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/diagnostics-symbol-store-interfaces.md)  
 [<span data-ttu-id="16c23-116">ISymUnmanagedScope, interfejs</span><span class="sxs-lookup"><span data-stu-id="16c23-116">ISymUnmanagedScope Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedscope-interface.md)
