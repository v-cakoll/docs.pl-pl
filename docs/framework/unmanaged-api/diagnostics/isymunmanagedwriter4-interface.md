---
title: "ISymUnmanagedWriter4 — Interfejs"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: 4af5e8c0-987d-405e-b934-8b9e70fcae6e
caps.latest.revision: "4"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: f7ab7f06ba280675ca8349500e766364d30f9349
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="isymunmanagedwriter4-interface"></a><span data-ttu-id="9fd8e-102">ISymUnmanagedWriter4 — Interfejs</span><span class="sxs-lookup"><span data-stu-id="9fd8e-102">ISymUnmanagedWriter4 Interface</span></span>
<span data-ttu-id="9fd8e-103">Isymunmanagedwriter4 — interfejs.</span><span class="sxs-lookup"><span data-stu-id="9fd8e-103">ISymUnmanagedWriter4 interface.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9fd8e-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="9fd8e-104">Syntax</span></span>  
  
```idl  
[object,uuid(BC7E3F53-F458-4C23-9DBD-A189E6E96594),pointer_default(unique)]interface ISymUnmanagedWriter4 : ISymUnmanagedWriter3  
```  
  
## <a name="methods"></a><span data-ttu-id="9fd8e-105">Metody</span><span class="sxs-lookup"><span data-stu-id="9fd8e-105">Methods</span></span>  
 <span data-ttu-id="9fd8e-106">Ten interfejs zawiera następujące metody:</span><span class="sxs-lookup"><span data-stu-id="9fd8e-106">This interface contains the following methods:</span></span>  
  
|<span data-ttu-id="9fd8e-107">Metoda</span><span class="sxs-lookup"><span data-stu-id="9fd8e-107">Method</span></span>|<span data-ttu-id="9fd8e-108">Opis</span><span class="sxs-lookup"><span data-stu-id="9fd8e-108">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="9fd8e-109">GetDebugInfoWithPadding — metoda</span><span class="sxs-lookup"><span data-stu-id="9fd8e-109">GetDebugInfoWithPadding Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter4-getdebuginfowithpadding-method.md)|<span data-ttu-id="9fd8e-110">Działa tak samo, jak [GetDebugInfo — metoda](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-getdebuginfo-method.md) z tą różnicą, że ciąg ścieżki jest uzupełniana zerami po znak końcowy null, aby udostępnić dane ciąg stały rozmiar `MAX_PATH`.</span><span class="sxs-lookup"><span data-stu-id="9fd8e-110">Functions the same as [GetDebugInfo Method](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-getdebuginfo-method.md) except that the path string is padded with zeros following the terminating null character to make the string data a fixed size of `MAX_PATH`.</span></span> <span data-ttu-id="9fd8e-111">Dopełnienie tylko otrzyma, jeśli długość ciągu ścieżki sam jest mniejsza niż `MAX_PATH`.</span><span class="sxs-lookup"><span data-stu-id="9fd8e-111">Padding is only given if the path string length itself is less than `MAX_PATH`.</span></span><br /><br /> <span data-ttu-id="9fd8e-112">Ułatwia to zapisać narzędzia pliki tej różnicy PE.</span><span class="sxs-lookup"><span data-stu-id="9fd8e-112">This makes it easier to write tools that difference PE files.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="9fd8e-113">Wymagania</span><span class="sxs-lookup"><span data-stu-id="9fd8e-113">Requirements</span></span>  
 <span data-ttu-id="9fd8e-114">**Nagłówek:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="9fd8e-114">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9fd8e-115">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="9fd8e-115">See Also</span></span>  
 [<span data-ttu-id="9fd8e-116">Interfejsy magazynu symboli diagnostycznych</span><span class="sxs-lookup"><span data-stu-id="9fd8e-116">Diagnostics Symbol Store Interfaces</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/diagnostics-symbol-store-interfaces.md)  
 [<span data-ttu-id="9fd8e-117">ISymUnmanagedWriter3 — interfejs</span><span class="sxs-lookup"><span data-stu-id="9fd8e-117">ISymUnmanagedWriter3 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter3-interface.md)
