---
title: ISymUnmanagedSymbolSearchInfo — Interfejs
ms.date: 03/30/2017
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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: d573264bb7a3cac02dd41afacaa2bc4a6f9e6dcd
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59207555"
---
# <a name="isymunmanagedsymbolsearchinfo-interface"></a><span data-ttu-id="5fe9d-102">ISymUnmanagedSymbolSearchInfo — Interfejs</span><span class="sxs-lookup"><span data-stu-id="5fe9d-102">ISymUnmanagedSymbolSearchInfo Interface</span></span>
<span data-ttu-id="5fe9d-103">Udostępnia metody, które zawierają informacje o ścieżce wyszukiwania.</span><span class="sxs-lookup"><span data-stu-id="5fe9d-103">Provides methods that get information about the search path.</span></span> <span data-ttu-id="5fe9d-104">Uzyskanie tego interfejsu, wywołując `QueryInterface` na obiekt, który implementuje [isymunmanagedreader —](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-interface.md) interfejsu.</span><span class="sxs-lookup"><span data-stu-id="5fe9d-104">Obtain this interface by calling `QueryInterface` on an object that implements the [ISymUnmanagedReader](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-interface.md) interface.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="5fe9d-105">Metody</span><span class="sxs-lookup"><span data-stu-id="5fe9d-105">Methods</span></span>  
  
|<span data-ttu-id="5fe9d-106">Metoda</span><span class="sxs-lookup"><span data-stu-id="5fe9d-106">Method</span></span>|<span data-ttu-id="5fe9d-107">Opis</span><span class="sxs-lookup"><span data-stu-id="5fe9d-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="5fe9d-108">GetHRESULT, metoda</span><span class="sxs-lookup"><span data-stu-id="5fe9d-108">GetHRESULT Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedsymbolsearchinfo-gethresult-method.md)|<span data-ttu-id="5fe9d-109">Pobiera wartość HRESULT.</span><span class="sxs-lookup"><span data-stu-id="5fe9d-109">Gets the HRESULT.</span></span>|  
|[<span data-ttu-id="5fe9d-110">GetSearchPath, metoda</span><span class="sxs-lookup"><span data-stu-id="5fe9d-110">GetSearchPath Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedsymbolsearchinfo-getsearchpath-method.md)|<span data-ttu-id="5fe9d-111">Pobiera ścieżkę wyszukiwania.</span><span class="sxs-lookup"><span data-stu-id="5fe9d-111">Gets the search path.</span></span>|  
|[<span data-ttu-id="5fe9d-112">GetSearchPathLength, metoda</span><span class="sxs-lookup"><span data-stu-id="5fe9d-112">GetSearchPathLength Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedsymbolsearchinfo-getsearchpathlength-method.md)|<span data-ttu-id="5fe9d-113">Pobiera długość ścieżki wyszukiwania.</span><span class="sxs-lookup"><span data-stu-id="5fe9d-113">Gets the search path length.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="5fe9d-114">Wymagania</span><span class="sxs-lookup"><span data-stu-id="5fe9d-114">Requirements</span></span>  
 <span data-ttu-id="5fe9d-115">**Nagłówek:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="5fe9d-115">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5fe9d-116">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="5fe9d-116">See also</span></span>

- [<span data-ttu-id="5fe9d-117">Interfejsy magazynu symboli diagnostycznych</span><span class="sxs-lookup"><span data-stu-id="5fe9d-117">Diagnostics Symbol Store Interfaces</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/diagnostics-symbol-store-interfaces.md)
