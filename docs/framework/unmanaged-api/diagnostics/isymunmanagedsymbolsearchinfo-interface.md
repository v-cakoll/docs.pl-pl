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
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61944574"
---
# <a name="isymunmanagedsymbolsearchinfo-interface"></a><span data-ttu-id="0a5d7-102">ISymUnmanagedSymbolSearchInfo — Interfejs</span><span class="sxs-lookup"><span data-stu-id="0a5d7-102">ISymUnmanagedSymbolSearchInfo Interface</span></span>
<span data-ttu-id="0a5d7-103">Udostępnia metody, które zawierają informacje o ścieżce wyszukiwania.</span><span class="sxs-lookup"><span data-stu-id="0a5d7-103">Provides methods that get information about the search path.</span></span> <span data-ttu-id="0a5d7-104">Uzyskanie tego interfejsu, wywołując `QueryInterface` na obiekt, który implementuje [isymunmanagedreader —](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-interface.md) interfejsu.</span><span class="sxs-lookup"><span data-stu-id="0a5d7-104">Obtain this interface by calling `QueryInterface` on an object that implements the [ISymUnmanagedReader](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-interface.md) interface.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="0a5d7-105">Metody</span><span class="sxs-lookup"><span data-stu-id="0a5d7-105">Methods</span></span>  
  
|<span data-ttu-id="0a5d7-106">Metoda</span><span class="sxs-lookup"><span data-stu-id="0a5d7-106">Method</span></span>|<span data-ttu-id="0a5d7-107">Opis</span><span class="sxs-lookup"><span data-stu-id="0a5d7-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="0a5d7-108">GetHRESULT, metoda</span><span class="sxs-lookup"><span data-stu-id="0a5d7-108">GetHRESULT Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedsymbolsearchinfo-gethresult-method.md)|<span data-ttu-id="0a5d7-109">Pobiera wartość HRESULT.</span><span class="sxs-lookup"><span data-stu-id="0a5d7-109">Gets the HRESULT.</span></span>|  
|[<span data-ttu-id="0a5d7-110">GetSearchPath, metoda</span><span class="sxs-lookup"><span data-stu-id="0a5d7-110">GetSearchPath Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedsymbolsearchinfo-getsearchpath-method.md)|<span data-ttu-id="0a5d7-111">Pobiera ścieżkę wyszukiwania.</span><span class="sxs-lookup"><span data-stu-id="0a5d7-111">Gets the search path.</span></span>|  
|[<span data-ttu-id="0a5d7-112">GetSearchPathLength, metoda</span><span class="sxs-lookup"><span data-stu-id="0a5d7-112">GetSearchPathLength Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedsymbolsearchinfo-getsearchpathlength-method.md)|<span data-ttu-id="0a5d7-113">Pobiera długość ścieżki wyszukiwania.</span><span class="sxs-lookup"><span data-stu-id="0a5d7-113">Gets the search path length.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="0a5d7-114">Wymagania</span><span class="sxs-lookup"><span data-stu-id="0a5d7-114">Requirements</span></span>  
 <span data-ttu-id="0a5d7-115">**Nagłówek:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="0a5d7-115">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0a5d7-116">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="0a5d7-116">See also</span></span>

- [<span data-ttu-id="0a5d7-117">Interfejsy magazynu symboli diagnostycznych</span><span class="sxs-lookup"><span data-stu-id="0a5d7-117">Diagnostics Symbol Store Interfaces</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/diagnostics-symbol-store-interfaces.md)
