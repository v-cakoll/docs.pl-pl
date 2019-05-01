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
ms.openlocfilehash: 97df6d6ec9a446e89eef8a9f8a5e5e8ddc85c0f7
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61970199"
---
# <a name="isymunmanagedwriter2-interface"></a><span data-ttu-id="e58f2-102">ISymUnmanagedWriter2 — Interfejs</span><span class="sxs-lookup"><span data-stu-id="e58f2-102">ISymUnmanagedWriter2 Interface</span></span>
<span data-ttu-id="e58f2-103">Reprezentuje edytor symboli i zapewnia metody do definiowania dokumentów, punktów sekwencji, leksykalne zakresy i zmienne.</span><span class="sxs-lookup"><span data-stu-id="e58f2-103">Represents a symbol writer, and provides methods to define documents, sequence points, lexical scopes, and variables.</span></span> <span data-ttu-id="e58f2-104">Ten interfejs rozszerza [isymunmanagedwriter —](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-interface.md) interfejsu.</span><span class="sxs-lookup"><span data-stu-id="e58f2-104">This interface extends the [ISymUnmanagedWriter](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-interface.md) interface.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="e58f2-105">Metody</span><span class="sxs-lookup"><span data-stu-id="e58f2-105">Methods</span></span>  
  
|<span data-ttu-id="e58f2-106">Metoda</span><span class="sxs-lookup"><span data-stu-id="e58f2-106">Method</span></span>|<span data-ttu-id="e58f2-107">Opis</span><span class="sxs-lookup"><span data-stu-id="e58f2-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="e58f2-108">DefineConstant2, metoda</span><span class="sxs-lookup"><span data-stu-id="e58f2-108">DefineConstant2 Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter2-defineconstant2-method.md)|<span data-ttu-id="e58f2-109">Definiuje nazwę wartości stałej.</span><span class="sxs-lookup"><span data-stu-id="e58f2-109">Defines a name for a constant value.</span></span>|  
|[<span data-ttu-id="e58f2-110">DefineGlobalVariable2, metoda</span><span class="sxs-lookup"><span data-stu-id="e58f2-110">DefineGlobalVariable2 Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter2-defineglobalvariable2-method.md)|<span data-ttu-id="e58f2-111">Definiuje jednej zmiennej globalnej.</span><span class="sxs-lookup"><span data-stu-id="e58f2-111">Defines a single global variable.</span></span>|  
|[<span data-ttu-id="e58f2-112">DefineLocalVariable2, metoda</span><span class="sxs-lookup"><span data-stu-id="e58f2-112">DefineLocalVariable2 Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter2-definelocalvariable2-method.md)|<span data-ttu-id="e58f2-113">Definiuje pojedynczą zmienną w bieżącym zakresie leksykalnym.</span><span class="sxs-lookup"><span data-stu-id="e58f2-113">Defines a single variable in the current lexical scope.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="e58f2-114">Wymagania</span><span class="sxs-lookup"><span data-stu-id="e58f2-114">Requirements</span></span>  
 <span data-ttu-id="e58f2-115">**Nagłówek:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="e58f2-115">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e58f2-116">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="e58f2-116">See also</span></span>

- [<span data-ttu-id="e58f2-117">Interfejsy magazynu symboli diagnostycznych</span><span class="sxs-lookup"><span data-stu-id="e58f2-117">Diagnostics Symbol Store Interfaces</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/diagnostics-symbol-store-interfaces.md)
- [<span data-ttu-id="e58f2-118">ISymUnmanagedWriter, interfejs</span><span class="sxs-lookup"><span data-stu-id="e58f2-118">ISymUnmanagedWriter Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-interface.md)
- [<span data-ttu-id="e58f2-119">ISymUnmanagedWriter3, interfejs</span><span class="sxs-lookup"><span data-stu-id="e58f2-119">ISymUnmanagedWriter3 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter3-interface.md)
