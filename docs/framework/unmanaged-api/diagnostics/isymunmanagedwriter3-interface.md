---
title: ISymUnmanagedWriter3 — Interfejs
ms.date: 03/30/2017
api_name:
- ISymUnmanagedWriter3
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedWriter3
helpviewer_keywords:
- ISymUnmanagedWriter3 interface [.NET Framework debugging]
ms.assetid: a034c21e-e371-4360-b470-29e88288948f
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: c1315d54e93769772772d536e9688c754a96c67c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33429397"
---
# <a name="isymunmanagedwriter3-interface"></a><span data-ttu-id="e4c7d-102">ISymUnmanagedWriter3 — Interfejs</span><span class="sxs-lookup"><span data-stu-id="e4c7d-102">ISymUnmanagedWriter3 Interface</span></span>
<span data-ttu-id="e4c7d-103">Reprezentuje edytor symboli i udostępnia metody, aby zdefiniować dokumenty, punkty sekwencji leksykalne zakresy i zmienne.</span><span class="sxs-lookup"><span data-stu-id="e4c7d-103">Represents a symbol writer, and provides methods to define documents, sequence points, lexical scopes, and variables.</span></span> <span data-ttu-id="e4c7d-104">Ten interfejs stanowi rozszerzenie [ISymUnmanagedWriter](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-interface.md) interfejsu.</span><span class="sxs-lookup"><span data-stu-id="e4c7d-104">This interface extends the [ISymUnmanagedWriter](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-interface.md) interface.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="e4c7d-105">Metody</span><span class="sxs-lookup"><span data-stu-id="e4c7d-105">Methods</span></span>  
  
|<span data-ttu-id="e4c7d-106">Metoda</span><span class="sxs-lookup"><span data-stu-id="e4c7d-106">Method</span></span>|<span data-ttu-id="e4c7d-107">Opis</span><span class="sxs-lookup"><span data-stu-id="e4c7d-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="e4c7d-108">Commit, metoda</span><span class="sxs-lookup"><span data-stu-id="e4c7d-108">Commit Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter3-commit-method.md)|<span data-ttu-id="e4c7d-109">Zatwierdza zmiany do tej pory zapisywane do strumienia.</span><span class="sxs-lookup"><span data-stu-id="e4c7d-109">Commits the changes written so far to the stream.</span></span>|  
|[<span data-ttu-id="e4c7d-110">OpenMethod2, metoda</span><span class="sxs-lookup"><span data-stu-id="e4c7d-110">OpenMethod2 Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter3-openmethod2-method.md)|<span data-ttu-id="e4c7d-111">Otwiera metody i zapewnia jego przesunięcie rzeczywistych sekcji w obrazie.</span><span class="sxs-lookup"><span data-stu-id="e4c7d-111">Opens a method and provides its real section offset in the image.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="e4c7d-112">Wymagania</span><span class="sxs-lookup"><span data-stu-id="e4c7d-112">Requirements</span></span>  
 <span data-ttu-id="e4c7d-113">**Header:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="e4c7d-113">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e4c7d-114">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="e4c7d-114">See Also</span></span>  
 [<span data-ttu-id="e4c7d-115">Interfejsy magazynu symboli diagnostycznych</span><span class="sxs-lookup"><span data-stu-id="e4c7d-115">Diagnostics Symbol Store Interfaces</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/diagnostics-symbol-store-interfaces.md)  
 [<span data-ttu-id="e4c7d-116">ISymUnmanagedWriter, interfejs</span><span class="sxs-lookup"><span data-stu-id="e4c7d-116">ISymUnmanagedWriter Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-interface.md)  
 [<span data-ttu-id="e4c7d-117">ISymUnmanagedWriter2, interfejs</span><span class="sxs-lookup"><span data-stu-id="e4c7d-117">ISymUnmanagedWriter2 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter2-interface.md)
