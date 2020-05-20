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
ms.openlocfilehash: 886ba693183a6b99eb03635e95a9661d105de40e
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/19/2020
ms.locfileid: "83610863"
---
# <a name="isymunmanagedscope2-interface"></a><span data-ttu-id="33bfc-102">ISymUnmanagedScope2 — Interfejs</span><span class="sxs-lookup"><span data-stu-id="33bfc-102">ISymUnmanagedScope2 Interface</span></span>
<span data-ttu-id="33bfc-103">Reprezentuje zakres leksykalny w ramach metody.</span><span class="sxs-lookup"><span data-stu-id="33bfc-103">Represents a lexical scope within a method.</span></span> <span data-ttu-id="33bfc-104">Ten interfejs rozszerza interfejs [ISymUnmanagedScope](isymunmanagedscope-interface.md) z metodami, które pobierają informacje o stałych zdefiniowanych w zakresie.</span><span class="sxs-lookup"><span data-stu-id="33bfc-104">This interface extends the [ISymUnmanagedScope](isymunmanagedscope-interface.md) interface with methods that get information about constants defined within the scope.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="33bfc-105">Metody</span><span class="sxs-lookup"><span data-stu-id="33bfc-105">Methods</span></span>  
  
|<span data-ttu-id="33bfc-106">Metoda</span><span class="sxs-lookup"><span data-stu-id="33bfc-106">Method</span></span>|<span data-ttu-id="33bfc-107">Opis</span><span class="sxs-lookup"><span data-stu-id="33bfc-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="33bfc-108">GetConstantCount, metoda</span><span class="sxs-lookup"><span data-stu-id="33bfc-108">GetConstantCount Method</span></span>](isymunmanagedscope2-getconstantcount-method.md)|<span data-ttu-id="33bfc-109">Pobiera liczbę stałych zdefiniowanych w tym zakresie.</span><span class="sxs-lookup"><span data-stu-id="33bfc-109">Gets a count of the constants defined within this scope.</span></span>|  
|[<span data-ttu-id="33bfc-110">GetConstants, metoda</span><span class="sxs-lookup"><span data-stu-id="33bfc-110">GetConstants Method</span></span>](isymunmanagedscope2-getconstants-method.md)|<span data-ttu-id="33bfc-111">Pobiera stałe lokalne zdefiniowane w tym zakresie.</span><span class="sxs-lookup"><span data-stu-id="33bfc-111">Gets the local constants defined within this scope.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="33bfc-112">Wymagania</span><span class="sxs-lookup"><span data-stu-id="33bfc-112">Requirements</span></span>  
 <span data-ttu-id="33bfc-113">**Nagłówek:** CorSym. idl, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="33bfc-113">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="33bfc-114">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="33bfc-114">See also</span></span>

- [<span data-ttu-id="33bfc-115">Interfejsy magazynu symboli diagnostycznych</span><span class="sxs-lookup"><span data-stu-id="33bfc-115">Diagnostics Symbol Store Interfaces</span></span>](diagnostics-symbol-store-interfaces.md)
- [<span data-ttu-id="33bfc-116">ISymUnmanagedScope — Interfejs</span><span class="sxs-lookup"><span data-stu-id="33bfc-116">ISymUnmanagedScope Interface</span></span>](isymunmanagedscope-interface.md)
