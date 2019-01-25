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
ms.openlocfilehash: 90f5924bc03a9896442fd61a4c618d18ed999faf
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54638876"
---
# <a name="isymunmanageddispose-interface"></a><span data-ttu-id="4b794-102">ISymUnmanagedDispose — Interfejs</span><span class="sxs-lookup"><span data-stu-id="4b794-102">ISymUnmanagedDispose Interface</span></span>
<span data-ttu-id="4b794-103">Usuwa zasoby niezarządzane.</span><span class="sxs-lookup"><span data-stu-id="4b794-103">Disposes of unmanaged resources.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="4b794-104">Metody</span><span class="sxs-lookup"><span data-stu-id="4b794-104">Methods</span></span>  
  
|<span data-ttu-id="4b794-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="4b794-105">Method</span></span>|<span data-ttu-id="4b794-106">Opis</span><span class="sxs-lookup"><span data-stu-id="4b794-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="4b794-107">destroy, metoda</span><span class="sxs-lookup"><span data-stu-id="4b794-107">Destroy Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanageddispose-destroy-method.md)|<span data-ttu-id="4b794-108">Powoduje, że obiekt jest zwolnienie wszystkich odwołań wewnętrznego i zwraca błąd na dowolne wywołania metody kolejne.</span><span class="sxs-lookup"><span data-stu-id="4b794-108">Causes the underlying object to release all internal references and return failure on any subsequent method calls.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="4b794-109">Wymagania</span><span class="sxs-lookup"><span data-stu-id="4b794-109">Requirements</span></span>  
 <span data-ttu-id="4b794-110">**Nagłówek:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="4b794-110">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4b794-111">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="4b794-111">See also</span></span>
- [<span data-ttu-id="4b794-112">Interfejsy magazynu symboli diagnostycznych</span><span class="sxs-lookup"><span data-stu-id="4b794-112">Diagnostics Symbol Store Interfaces</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/diagnostics-symbol-store-interfaces.md)
