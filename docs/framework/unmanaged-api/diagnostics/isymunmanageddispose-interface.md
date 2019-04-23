---
title: ISymUnmanagedDispose — Interfejs
ms.date: 03/30/2017
api_name:
- ISymUnmanagedDispose
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedDispose
helpviewer_keywords:
- ISymUnmanagedDispose interface [.NET Framework debugging]
ms.assetid: b1d74e83-a200-4d00-8fbd-27918808616d
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 8e81cea13fb8d25701ccbe163f112904baf47a9f
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59143172"
---
# <a name="isymunmanageddispose-interface"></a><span data-ttu-id="41874-102">ISymUnmanagedDispose — Interfejs</span><span class="sxs-lookup"><span data-stu-id="41874-102">ISymUnmanagedDispose Interface</span></span>
<span data-ttu-id="41874-103">Usuwa zasoby niezarządzane.</span><span class="sxs-lookup"><span data-stu-id="41874-103">Disposes of unmanaged resources.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="41874-104">Metody</span><span class="sxs-lookup"><span data-stu-id="41874-104">Methods</span></span>  
  
|<span data-ttu-id="41874-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="41874-105">Method</span></span>|<span data-ttu-id="41874-106">Opis</span><span class="sxs-lookup"><span data-stu-id="41874-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="41874-107">destroy, metoda</span><span class="sxs-lookup"><span data-stu-id="41874-107">Destroy Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanageddispose-destroy-method.md)|<span data-ttu-id="41874-108">Powoduje, że obiekt jest zwolnienie wszystkich odwołań wewnętrznego i zwraca błąd na dowolne wywołania metody kolejne.</span><span class="sxs-lookup"><span data-stu-id="41874-108">Causes the underlying object to release all internal references and return failure on any subsequent method calls.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="41874-109">Wymagania</span><span class="sxs-lookup"><span data-stu-id="41874-109">Requirements</span></span>  
 <span data-ttu-id="41874-110">**Nagłówek:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="41874-110">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="41874-111">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="41874-111">See also</span></span>

- [<span data-ttu-id="41874-112">Interfejsy magazynu symboli diagnostycznych</span><span class="sxs-lookup"><span data-stu-id="41874-112">Diagnostics Symbol Store Interfaces</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/diagnostics-symbol-store-interfaces.md)
