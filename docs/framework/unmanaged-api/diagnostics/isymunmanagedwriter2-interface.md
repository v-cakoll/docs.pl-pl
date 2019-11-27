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
ms.openlocfilehash: c7f0235aa7096a790a0fd956081e330c8fdad9fe
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/23/2019
ms.locfileid: "74438254"
---
# <a name="isymunmanagedwriter2-interface"></a><span data-ttu-id="c7021-102">ISymUnmanagedWriter2 — Interfejs</span><span class="sxs-lookup"><span data-stu-id="c7021-102">ISymUnmanagedWriter2 Interface</span></span>
<span data-ttu-id="c7021-103">Reprezentuje moduł zapisujący symboli i zawiera metody definiowania dokumentów, punktów sekwencji, zakresów leksykalnych i zmiennych.</span><span class="sxs-lookup"><span data-stu-id="c7021-103">Represents a symbol writer, and provides methods to define documents, sequence points, lexical scopes, and variables.</span></span> <span data-ttu-id="c7021-104">Ten interfejs rozszerza interfejs [ISymUnmanagedWriter](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-interface.md) .</span><span class="sxs-lookup"><span data-stu-id="c7021-104">This interface extends the [ISymUnmanagedWriter](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-interface.md) interface.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="c7021-105">Metody</span><span class="sxs-lookup"><span data-stu-id="c7021-105">Methods</span></span>  
  
|<span data-ttu-id="c7021-106">Metoda</span><span class="sxs-lookup"><span data-stu-id="c7021-106">Method</span></span>|<span data-ttu-id="c7021-107">Opis</span><span class="sxs-lookup"><span data-stu-id="c7021-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="c7021-108">DefineConstant2, metoda</span><span class="sxs-lookup"><span data-stu-id="c7021-108">DefineConstant2 Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter2-defineconstant2-method.md)|<span data-ttu-id="c7021-109">Definiuje nazwę wartości stałej.</span><span class="sxs-lookup"><span data-stu-id="c7021-109">Defines a name for a constant value.</span></span>|  
|[<span data-ttu-id="c7021-110">DefineGlobalVariable2, metoda</span><span class="sxs-lookup"><span data-stu-id="c7021-110">DefineGlobalVariable2 Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter2-defineglobalvariable2-method.md)|<span data-ttu-id="c7021-111">Definiuje pojedynczą zmienną globalną.</span><span class="sxs-lookup"><span data-stu-id="c7021-111">Defines a single global variable.</span></span>|  
|[<span data-ttu-id="c7021-112">DefineLocalVariable2, metoda</span><span class="sxs-lookup"><span data-stu-id="c7021-112">DefineLocalVariable2 Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter2-definelocalvariable2-method.md)|<span data-ttu-id="c7021-113">Definiuje pojedynczą zmienną w bieżącym zakresie leksykalnym.</span><span class="sxs-lookup"><span data-stu-id="c7021-113">Defines a single variable in the current lexical scope.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="c7021-114">Wymagania</span><span class="sxs-lookup"><span data-stu-id="c7021-114">Requirements</span></span>  
 <span data-ttu-id="c7021-115">**Nagłówek:** CorSym. idl, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="c7021-115">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c7021-116">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="c7021-116">See also</span></span>

- [<span data-ttu-id="c7021-117">Interfejsy magazynu symboli diagnostycznych</span><span class="sxs-lookup"><span data-stu-id="c7021-117">Diagnostics Symbol Store Interfaces</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/diagnostics-symbol-store-interfaces.md)
- [<span data-ttu-id="c7021-118">ISymUnmanagedWriter, interfejs</span><span class="sxs-lookup"><span data-stu-id="c7021-118">ISymUnmanagedWriter Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-interface.md)
- [<span data-ttu-id="c7021-119">ISymUnmanagedWriter3, interfejs</span><span class="sxs-lookup"><span data-stu-id="c7021-119">ISymUnmanagedWriter3 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter3-interface.md)
