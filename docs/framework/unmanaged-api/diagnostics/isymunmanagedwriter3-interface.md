---
title: "ISymUnmanagedWriter3 — Interfejs"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
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
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 49928044bcf2c598cdc0e4315d569f2c4eb02f1d
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="isymunmanagedwriter3-interface"></a><span data-ttu-id="a3014-102">ISymUnmanagedWriter3 — Interfejs</span><span class="sxs-lookup"><span data-stu-id="a3014-102">ISymUnmanagedWriter3 Interface</span></span>
<span data-ttu-id="a3014-103">Reprezentuje edytor symboli i udostępnia metody, aby zdefiniować dokumenty, punkty sekwencji leksykalne zakresy i zmienne.</span><span class="sxs-lookup"><span data-stu-id="a3014-103">Represents a symbol writer, and provides methods to define documents, sequence points, lexical scopes, and variables.</span></span> <span data-ttu-id="a3014-104">Ten interfejs stanowi rozszerzenie [ISymUnmanagedWriter](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-interface.md) interfejsu.</span><span class="sxs-lookup"><span data-stu-id="a3014-104">This interface extends the [ISymUnmanagedWriter](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-interface.md) interface.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="a3014-105">Metody</span><span class="sxs-lookup"><span data-stu-id="a3014-105">Methods</span></span>  
  
|<span data-ttu-id="a3014-106">Metoda</span><span class="sxs-lookup"><span data-stu-id="a3014-106">Method</span></span>|<span data-ttu-id="a3014-107">Opis</span><span class="sxs-lookup"><span data-stu-id="a3014-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="a3014-108">Commit, metoda</span><span class="sxs-lookup"><span data-stu-id="a3014-108">Commit Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter3-commit-method.md)|<span data-ttu-id="a3014-109">Zatwierdza zmiany do tej pory zapisywane do strumienia.</span><span class="sxs-lookup"><span data-stu-id="a3014-109">Commits the changes written so far to the stream.</span></span>|  
|[<span data-ttu-id="a3014-110">OpenMethod2, metoda</span><span class="sxs-lookup"><span data-stu-id="a3014-110">OpenMethod2 Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter3-openmethod2-method.md)|<span data-ttu-id="a3014-111">Otwiera metody i zapewnia jego przesunięcie rzeczywistych sekcji w obrazie.</span><span class="sxs-lookup"><span data-stu-id="a3014-111">Opens a method and provides its real section offset in the image.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="a3014-112">Wymagania</span><span class="sxs-lookup"><span data-stu-id="a3014-112">Requirements</span></span>  
 <span data-ttu-id="a3014-113">**Nagłówek:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="a3014-113">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a3014-114">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="a3014-114">See Also</span></span>  
 [<span data-ttu-id="a3014-115">Interfejsy magazynu symboli diagnostycznych</span><span class="sxs-lookup"><span data-stu-id="a3014-115">Diagnostics Symbol Store Interfaces</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/diagnostics-symbol-store-interfaces.md)  
 [<span data-ttu-id="a3014-116">ISymUnmanagedWriter, interfejs</span><span class="sxs-lookup"><span data-stu-id="a3014-116">ISymUnmanagedWriter Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-interface.md)  
 [<span data-ttu-id="a3014-117">ISymUnmanagedWriter2, interfejs</span><span class="sxs-lookup"><span data-stu-id="a3014-117">ISymUnmanagedWriter2 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter2-interface.md)
