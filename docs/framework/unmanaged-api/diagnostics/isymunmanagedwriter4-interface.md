---
title: ISymUnmanagedWriter4 — Interfejs
ms.date: 03/30/2017
ms.assetid: 4af5e8c0-987d-405e-b934-8b9e70fcae6e
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 5e8478aed662142b9ff4b73f9cb192f8d2306e2a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33429689"
---
# <a name="isymunmanagedwriter4-interface"></a><span data-ttu-id="baf93-102">ISymUnmanagedWriter4 — Interfejs</span><span class="sxs-lookup"><span data-stu-id="baf93-102">ISymUnmanagedWriter4 Interface</span></span>
<span data-ttu-id="baf93-103">Isymunmanagedwriter4 — interfejs.</span><span class="sxs-lookup"><span data-stu-id="baf93-103">ISymUnmanagedWriter4 interface.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="baf93-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="baf93-104">Syntax</span></span>  
  
```idl  
[object,uuid(BC7E3F53-F458-4C23-9DBD-A189E6E96594),pointer_default(unique)]interface ISymUnmanagedWriter4 : ISymUnmanagedWriter3  
```  
  
## <a name="methods"></a><span data-ttu-id="baf93-105">Metody</span><span class="sxs-lookup"><span data-stu-id="baf93-105">Methods</span></span>  
 <span data-ttu-id="baf93-106">Ten interfejs zawiera następujące metody:</span><span class="sxs-lookup"><span data-stu-id="baf93-106">This interface contains the following methods:</span></span>  
  
|<span data-ttu-id="baf93-107">Metoda</span><span class="sxs-lookup"><span data-stu-id="baf93-107">Method</span></span>|<span data-ttu-id="baf93-108">Opis</span><span class="sxs-lookup"><span data-stu-id="baf93-108">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="baf93-109">GetDebugInfoWithPadding, metoda</span><span class="sxs-lookup"><span data-stu-id="baf93-109">GetDebugInfoWithPadding Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter4-getdebuginfowithpadding-method.md)|<span data-ttu-id="baf93-110">Działa tak samo, jak [GetDebugInfo — metoda](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-getdebuginfo-method.md) z tą różnicą, że ciąg ścieżki jest uzupełniana zerami po znak końcowy null, aby udostępnić dane ciąg stały rozmiar `MAX_PATH`.</span><span class="sxs-lookup"><span data-stu-id="baf93-110">Functions the same as [GetDebugInfo Method](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-getdebuginfo-method.md) except that the path string is padded with zeros following the terminating null character to make the string data a fixed size of `MAX_PATH`.</span></span> <span data-ttu-id="baf93-111">Dopełnienie tylko otrzyma, jeśli długość ciągu ścieżki sam jest mniejsza niż `MAX_PATH`.</span><span class="sxs-lookup"><span data-stu-id="baf93-111">Padding is only given if the path string length itself is less than `MAX_PATH`.</span></span><br /><br /> <span data-ttu-id="baf93-112">Ułatwia to zapisać narzędzia pliki tej różnicy PE.</span><span class="sxs-lookup"><span data-stu-id="baf93-112">This makes it easier to write tools that difference PE files.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="baf93-113">Wymagania</span><span class="sxs-lookup"><span data-stu-id="baf93-113">Requirements</span></span>  
 <span data-ttu-id="baf93-114">**Header:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="baf93-114">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="baf93-115">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="baf93-115">See Also</span></span>  
 [<span data-ttu-id="baf93-116">Interfejsy magazynu symboli diagnostycznych</span><span class="sxs-lookup"><span data-stu-id="baf93-116">Diagnostics Symbol Store Interfaces</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/diagnostics-symbol-store-interfaces.md)  
 [<span data-ttu-id="baf93-117">ISymUnmanagedWriter3, interfejs</span><span class="sxs-lookup"><span data-stu-id="baf93-117">ISymUnmanagedWriter3 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter3-interface.md)
