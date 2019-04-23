---
title: ISymUnmanagedSourceServerModule — Interfejs
ms.date: 03/30/2017
api_name:
- ISymUnmanagedSourceServerModule
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedSourceServerModule
helpviewer_keywords:
- ISymUnmanagedSourceServerModule interface [.NET Framework debugging]
ms.assetid: a19b23bd-2061-476e-b67d-252f57404f8b
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 3ba81c208c4b49342c6a055e09ba898871db1851
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59157615"
---
# <a name="isymunmanagedsourceservermodule-interface"></a><span data-ttu-id="c9928-102">ISymUnmanagedSourceServerModule — Interfejs</span><span class="sxs-lookup"><span data-stu-id="c9928-102">ISymUnmanagedSourceServerModule Interface</span></span>
<span data-ttu-id="c9928-103">Udostępnia dane z serwera źródłowego dla modułu.</span><span class="sxs-lookup"><span data-stu-id="c9928-103">Provides source server data for a module.</span></span> <span data-ttu-id="c9928-104">Uzyskanie tego interfejsu, wywołując `QueryInterface` na obiekt, który implementuje [isymunmanagedreader —](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-interface.md) interfejsu.</span><span class="sxs-lookup"><span data-stu-id="c9928-104">Obtain this interface by calling `QueryInterface` on an object that implements the [ISymUnmanagedReader](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-interface.md) interface.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="c9928-105">Metody</span><span class="sxs-lookup"><span data-stu-id="c9928-105">Methods</span></span>  
  
|<span data-ttu-id="c9928-106">Metoda</span><span class="sxs-lookup"><span data-stu-id="c9928-106">Method</span></span>|<span data-ttu-id="c9928-107">Opis</span><span class="sxs-lookup"><span data-stu-id="c9928-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="c9928-108">GetSourceServerData, metoda</span><span class="sxs-lookup"><span data-stu-id="c9928-108">GetSourceServerData Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedsourceservermodule-getsourceserverdata-method.md)|<span data-ttu-id="c9928-109">Zwraca dane serwera źródłowego dla modułu.</span><span class="sxs-lookup"><span data-stu-id="c9928-109">Returns the source server data for the module.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="c9928-110">Wymagania</span><span class="sxs-lookup"><span data-stu-id="c9928-110">Requirements</span></span>  
 <span data-ttu-id="c9928-111">**Nagłówek:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="c9928-111">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c9928-112">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="c9928-112">See also</span></span>

- [<span data-ttu-id="c9928-113">Interfejsy magazynu symboli diagnostycznych</span><span class="sxs-lookup"><span data-stu-id="c9928-113">Diagnostics Symbol Store Interfaces</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/diagnostics-symbol-store-interfaces.md)
