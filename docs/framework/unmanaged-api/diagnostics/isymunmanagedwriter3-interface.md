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
ms.openlocfilehash: 7c14706068e50fd79fb39ac9d75afacd181f7ab4
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54504083"
---
# <a name="isymunmanagedwriter3-interface"></a><span data-ttu-id="45be8-102">ISymUnmanagedWriter3 — Interfejs</span><span class="sxs-lookup"><span data-stu-id="45be8-102">ISymUnmanagedWriter3 Interface</span></span>
<span data-ttu-id="45be8-103">Reprezentuje edytor symboli i zapewnia metody do definiowania dokumentów, punktów sekwencji, leksykalne zakresy i zmienne.</span><span class="sxs-lookup"><span data-stu-id="45be8-103">Represents a symbol writer, and provides methods to define documents, sequence points, lexical scopes, and variables.</span></span> <span data-ttu-id="45be8-104">Ten interfejs rozszerza [isymunmanagedwriter —](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-interface.md) interfejsu.</span><span class="sxs-lookup"><span data-stu-id="45be8-104">This interface extends the [ISymUnmanagedWriter](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-interface.md) interface.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="45be8-105">Metody</span><span class="sxs-lookup"><span data-stu-id="45be8-105">Methods</span></span>  
  
|<span data-ttu-id="45be8-106">Metoda</span><span class="sxs-lookup"><span data-stu-id="45be8-106">Method</span></span>|<span data-ttu-id="45be8-107">Opis</span><span class="sxs-lookup"><span data-stu-id="45be8-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="45be8-108">Commit, metoda</span><span class="sxs-lookup"><span data-stu-id="45be8-108">Commit Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter3-commit-method.md)|<span data-ttu-id="45be8-109">Zatwierdza zmiany do tej pory zapisywane do strumienia.</span><span class="sxs-lookup"><span data-stu-id="45be8-109">Commits the changes written so far to the stream.</span></span>|  
|[<span data-ttu-id="45be8-110">OpenMethod2, metoda</span><span class="sxs-lookup"><span data-stu-id="45be8-110">OpenMethod2 Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter3-openmethod2-method.md)|<span data-ttu-id="45be8-111">Otwiera metody i zawiera przesunięcie rzeczywistych sekcji w obrazie.</span><span class="sxs-lookup"><span data-stu-id="45be8-111">Opens a method and provides its real section offset in the image.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="45be8-112">Wymagania</span><span class="sxs-lookup"><span data-stu-id="45be8-112">Requirements</span></span>  
 <span data-ttu-id="45be8-113">**Nagłówek:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="45be8-113">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="45be8-114">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="45be8-114">See also</span></span>
- [<span data-ttu-id="45be8-115">Interfejsy magazynu symboli diagnostycznych</span><span class="sxs-lookup"><span data-stu-id="45be8-115">Diagnostics Symbol Store Interfaces</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/diagnostics-symbol-store-interfaces.md)
- [<span data-ttu-id="45be8-116">ISymUnmanagedWriter, interfejs</span><span class="sxs-lookup"><span data-stu-id="45be8-116">ISymUnmanagedWriter Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-interface.md)
- [<span data-ttu-id="45be8-117">ISymUnmanagedWriter2, interfejs</span><span class="sxs-lookup"><span data-stu-id="45be8-117">ISymUnmanagedWriter2 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter2-interface.md)
