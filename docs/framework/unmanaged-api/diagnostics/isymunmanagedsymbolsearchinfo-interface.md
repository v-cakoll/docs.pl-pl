---
title: "ISymUnmanagedSymbolSearchInfo — Interfejs"
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
- ISymUnmanagedSymbolSearchInfo
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedSymbolSearchInfo
helpviewer_keywords:
- ISymUnmanagedSymbolSearchInfo interface [.NET Framework debugging]
ms.assetid: 30817373-0a21-49c1-a0c4-8e8daeecb8db
topic_type:
- apiref
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 441330471906a891646ad55eb73ec25b44800cbc
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="isymunmanagedsymbolsearchinfo-interface"></a><span data-ttu-id="3ef96-102">ISymUnmanagedSymbolSearchInfo — Interfejs</span><span class="sxs-lookup"><span data-stu-id="3ef96-102">ISymUnmanagedSymbolSearchInfo Interface</span></span>
<span data-ttu-id="3ef96-103">Udostępnia metody, które zawierają informacje o ścieżce wyszukiwania.</span><span class="sxs-lookup"><span data-stu-id="3ef96-103">Provides methods that get information about the search path.</span></span> <span data-ttu-id="3ef96-104">Uzyskanie przez wywołanie metody tego interfejsu `QueryInterface` na obiekt, który implementuje [ISymUnmanagedReader](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-interface.md) interfejsu.</span><span class="sxs-lookup"><span data-stu-id="3ef96-104">Obtain this interface by calling `QueryInterface` on an object that implements the [ISymUnmanagedReader](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-interface.md) interface.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="3ef96-105">Metody</span><span class="sxs-lookup"><span data-stu-id="3ef96-105">Methods</span></span>  
  
|<span data-ttu-id="3ef96-106">Metoda</span><span class="sxs-lookup"><span data-stu-id="3ef96-106">Method</span></span>|<span data-ttu-id="3ef96-107">Opis</span><span class="sxs-lookup"><span data-stu-id="3ef96-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="3ef96-108">GetHRESULT, metoda</span><span class="sxs-lookup"><span data-stu-id="3ef96-108">GetHRESULT Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedsymbolsearchinfo-gethresult-method.md)|<span data-ttu-id="3ef96-109">Pobiera wartość HRESULT.</span><span class="sxs-lookup"><span data-stu-id="3ef96-109">Gets the HRESULT.</span></span>|  
|[<span data-ttu-id="3ef96-110">GetSearchPath, metoda</span><span class="sxs-lookup"><span data-stu-id="3ef96-110">GetSearchPath Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedsymbolsearchinfo-getsearchpath-method.md)|<span data-ttu-id="3ef96-111">Pobiera ścieżkę wyszukiwania.</span><span class="sxs-lookup"><span data-stu-id="3ef96-111">Gets the search path.</span></span>|  
|[<span data-ttu-id="3ef96-112">GetSearchPathLength, metoda</span><span class="sxs-lookup"><span data-stu-id="3ef96-112">GetSearchPathLength Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedsymbolsearchinfo-getsearchpathlength-method.md)|<span data-ttu-id="3ef96-113">Pobiera długość ścieżki wyszukiwania.</span><span class="sxs-lookup"><span data-stu-id="3ef96-113">Gets the search path length.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="3ef96-114">Wymagania</span><span class="sxs-lookup"><span data-stu-id="3ef96-114">Requirements</span></span>  
 <span data-ttu-id="3ef96-115">**Nagłówek:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="3ef96-115">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3ef96-116">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="3ef96-116">See Also</span></span>  
 [<span data-ttu-id="3ef96-117">Interfejsy magazynu symboli diagnostycznych</span><span class="sxs-lookup"><span data-stu-id="3ef96-117">Diagnostics Symbol Store Interfaces</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/diagnostics-symbol-store-interfaces.md)
