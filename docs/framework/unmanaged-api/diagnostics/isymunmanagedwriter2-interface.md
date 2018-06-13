---
title: ISymUnmanagedWriter2 — Interfejs
ms.date: 03/30/2017
api_name:
- ISymUnmanagedWriter2
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedWriter2
helpviewer_keywords:
- ISymUnmanagedWriter2 interface [.NET Framework debugging]
ms.assetid: 8e78faa4-cf43-44fb-a91d-94d6df692a25
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: cbafe39fffd28a9bfccaa275c9009bc03549cda6
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33429433"
---
# <a name="isymunmanagedwriter2-interface"></a><span data-ttu-id="ef3db-102">ISymUnmanagedWriter2 — Interfejs</span><span class="sxs-lookup"><span data-stu-id="ef3db-102">ISymUnmanagedWriter2 Interface</span></span>
<span data-ttu-id="ef3db-103">Reprezentuje edytor symboli i udostępnia metody, aby zdefiniować dokumenty, punkty sekwencji leksykalne zakresy i zmienne.</span><span class="sxs-lookup"><span data-stu-id="ef3db-103">Represents a symbol writer, and provides methods to define documents, sequence points, lexical scopes, and variables.</span></span> <span data-ttu-id="ef3db-104">Ten interfejs stanowi rozszerzenie [ISymUnmanagedWriter](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-interface.md) interfejsu.</span><span class="sxs-lookup"><span data-stu-id="ef3db-104">This interface extends the [ISymUnmanagedWriter](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-interface.md) interface.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="ef3db-105">Metody</span><span class="sxs-lookup"><span data-stu-id="ef3db-105">Methods</span></span>  
  
|<span data-ttu-id="ef3db-106">Metoda</span><span class="sxs-lookup"><span data-stu-id="ef3db-106">Method</span></span>|<span data-ttu-id="ef3db-107">Opis</span><span class="sxs-lookup"><span data-stu-id="ef3db-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="ef3db-108">DefineConstant2, metoda</span><span class="sxs-lookup"><span data-stu-id="ef3db-108">DefineConstant2 Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter2-defineconstant2-method.md)|<span data-ttu-id="ef3db-109">Definiuje nazwę wartości stałej.</span><span class="sxs-lookup"><span data-stu-id="ef3db-109">Defines a name for a constant value.</span></span>|  
|[<span data-ttu-id="ef3db-110">DefineGlobalVariable2, metoda</span><span class="sxs-lookup"><span data-stu-id="ef3db-110">DefineGlobalVariable2 Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter2-defineglobalvariable2-method.md)|<span data-ttu-id="ef3db-111">Definiuje pojedynczą zmienną globalnego.</span><span class="sxs-lookup"><span data-stu-id="ef3db-111">Defines a single global variable.</span></span>|  
|[<span data-ttu-id="ef3db-112">DefineLocalVariable2, metoda</span><span class="sxs-lookup"><span data-stu-id="ef3db-112">DefineLocalVariable2 Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter2-definelocalvariable2-method.md)|<span data-ttu-id="ef3db-113">Definiuje pojedynczą zmienną w bieżącym zakresie leksykalne.</span><span class="sxs-lookup"><span data-stu-id="ef3db-113">Defines a single variable in the current lexical scope.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="ef3db-114">Wymagania</span><span class="sxs-lookup"><span data-stu-id="ef3db-114">Requirements</span></span>  
 <span data-ttu-id="ef3db-115">**Header:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="ef3db-115">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ef3db-116">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="ef3db-116">See Also</span></span>  
 [<span data-ttu-id="ef3db-117">Interfejsy magazynu symboli diagnostycznych</span><span class="sxs-lookup"><span data-stu-id="ef3db-117">Diagnostics Symbol Store Interfaces</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/diagnostics-symbol-store-interfaces.md)  
 [<span data-ttu-id="ef3db-118">ISymUnmanagedWriter, interfejs</span><span class="sxs-lookup"><span data-stu-id="ef3db-118">ISymUnmanagedWriter Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-interface.md)  
 [<span data-ttu-id="ef3db-119">ISymUnmanagedWriter3, interfejs</span><span class="sxs-lookup"><span data-stu-id="ef3db-119">ISymUnmanagedWriter3 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter3-interface.md)
