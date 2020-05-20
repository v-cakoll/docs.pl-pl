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
ms.openlocfilehash: 006045ce101884119f676e4f6324815eb21a10a4
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/19/2020
ms.locfileid: "83614659"
---
# <a name="isymunmanagedwriter3-interface"></a><span data-ttu-id="46ff1-102">ISymUnmanagedWriter3 — Interfejs</span><span class="sxs-lookup"><span data-stu-id="46ff1-102">ISymUnmanagedWriter3 Interface</span></span>
<span data-ttu-id="46ff1-103">Reprezentuje moduł zapisujący symboli i zawiera metody definiowania dokumentów, punktów sekwencji, zakresów leksykalnych i zmiennych.</span><span class="sxs-lookup"><span data-stu-id="46ff1-103">Represents a symbol writer, and provides methods to define documents, sequence points, lexical scopes, and variables.</span></span> <span data-ttu-id="46ff1-104">Ten interfejs rozszerza interfejs [ISymUnmanagedWriter](isymunmanagedwriter-interface.md) .</span><span class="sxs-lookup"><span data-stu-id="46ff1-104">This interface extends the [ISymUnmanagedWriter](isymunmanagedwriter-interface.md) interface.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="46ff1-105">Metody</span><span class="sxs-lookup"><span data-stu-id="46ff1-105">Methods</span></span>  
  
|<span data-ttu-id="46ff1-106">Metoda</span><span class="sxs-lookup"><span data-stu-id="46ff1-106">Method</span></span>|<span data-ttu-id="46ff1-107">Opis</span><span class="sxs-lookup"><span data-stu-id="46ff1-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="46ff1-108">Commit — metoda</span><span class="sxs-lookup"><span data-stu-id="46ff1-108">Commit Method</span></span>](isymunmanagedwriter3-commit-method.md)|<span data-ttu-id="46ff1-109">Zatwierdza zmiany zapisywane do strumienia.</span><span class="sxs-lookup"><span data-stu-id="46ff1-109">Commits the changes written so far to the stream.</span></span>|  
|[<span data-ttu-id="46ff1-110">OpenMethod2, metoda</span><span class="sxs-lookup"><span data-stu-id="46ff1-110">OpenMethod2 Method</span></span>](isymunmanagedwriter3-openmethod2-method.md)|<span data-ttu-id="46ff1-111">Otwiera metodę i udostępnia jej rzeczywiste przesunięcie sekcji w obrazie.</span><span class="sxs-lookup"><span data-stu-id="46ff1-111">Opens a method and provides its real section offset in the image.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="46ff1-112">Wymagania</span><span class="sxs-lookup"><span data-stu-id="46ff1-112">Requirements</span></span>  
 <span data-ttu-id="46ff1-113">**Nagłówek:** CorSym. idl, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="46ff1-113">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="46ff1-114">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="46ff1-114">See also</span></span>

- [<span data-ttu-id="46ff1-115">Interfejsy magazynu symboli diagnostycznych</span><span class="sxs-lookup"><span data-stu-id="46ff1-115">Diagnostics Symbol Store Interfaces</span></span>](diagnostics-symbol-store-interfaces.md)
- [<span data-ttu-id="46ff1-116">ISymUnmanagedWriter — Interfejs</span><span class="sxs-lookup"><span data-stu-id="46ff1-116">ISymUnmanagedWriter Interface</span></span>](isymunmanagedwriter-interface.md)
- [<span data-ttu-id="46ff1-117">ISymUnmanagedWriter2 — Interfejs</span><span class="sxs-lookup"><span data-stu-id="46ff1-117">ISymUnmanagedWriter2 Interface</span></span>](isymunmanagedwriter2-interface.md)
