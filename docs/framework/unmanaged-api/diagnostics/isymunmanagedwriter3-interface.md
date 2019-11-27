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
ms.openlocfilehash: 115d4b58b01606c29719fb88ab7dbf5a858b1251
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/23/2019
ms.locfileid: "74438169"
---
# <a name="isymunmanagedwriter3-interface"></a><span data-ttu-id="c696a-102">ISymUnmanagedWriter3 — Interfejs</span><span class="sxs-lookup"><span data-stu-id="c696a-102">ISymUnmanagedWriter3 Interface</span></span>
<span data-ttu-id="c696a-103">Reprezentuje moduł zapisujący symboli i zawiera metody definiowania dokumentów, punktów sekwencji, zakresów leksykalnych i zmiennych.</span><span class="sxs-lookup"><span data-stu-id="c696a-103">Represents a symbol writer, and provides methods to define documents, sequence points, lexical scopes, and variables.</span></span> <span data-ttu-id="c696a-104">Ten interfejs rozszerza interfejs [ISymUnmanagedWriter](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-interface.md) .</span><span class="sxs-lookup"><span data-stu-id="c696a-104">This interface extends the [ISymUnmanagedWriter](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-interface.md) interface.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="c696a-105">Metody</span><span class="sxs-lookup"><span data-stu-id="c696a-105">Methods</span></span>  
  
|<span data-ttu-id="c696a-106">Metoda</span><span class="sxs-lookup"><span data-stu-id="c696a-106">Method</span></span>|<span data-ttu-id="c696a-107">Opis</span><span class="sxs-lookup"><span data-stu-id="c696a-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="c696a-108">Commit, metoda</span><span class="sxs-lookup"><span data-stu-id="c696a-108">Commit Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter3-commit-method.md)|<span data-ttu-id="c696a-109">Zatwierdza zmiany zapisywane do strumienia.</span><span class="sxs-lookup"><span data-stu-id="c696a-109">Commits the changes written so far to the stream.</span></span>|  
|[<span data-ttu-id="c696a-110">OpenMethod2, metoda</span><span class="sxs-lookup"><span data-stu-id="c696a-110">OpenMethod2 Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter3-openmethod2-method.md)|<span data-ttu-id="c696a-111">Otwiera metodę i udostępnia jej rzeczywiste przesunięcie sekcji w obrazie.</span><span class="sxs-lookup"><span data-stu-id="c696a-111">Opens a method and provides its real section offset in the image.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="c696a-112">Wymagania</span><span class="sxs-lookup"><span data-stu-id="c696a-112">Requirements</span></span>  
 <span data-ttu-id="c696a-113">**Nagłówek:** CorSym. idl, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="c696a-113">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c696a-114">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="c696a-114">See also</span></span>

- [<span data-ttu-id="c696a-115">Interfejsy magazynu symboli diagnostycznych</span><span class="sxs-lookup"><span data-stu-id="c696a-115">Diagnostics Symbol Store Interfaces</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/diagnostics-symbol-store-interfaces.md)
- [<span data-ttu-id="c696a-116">ISymUnmanagedWriter, interfejs</span><span class="sxs-lookup"><span data-stu-id="c696a-116">ISymUnmanagedWriter Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-interface.md)
- [<span data-ttu-id="c696a-117">ISymUnmanagedWriter2, interfejs</span><span class="sxs-lookup"><span data-stu-id="c696a-117">ISymUnmanagedWriter2 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter2-interface.md)
