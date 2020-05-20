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
ms.openlocfilehash: d90a55b53ba00540137e44fc190790c4710903e3
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/19/2020
ms.locfileid: "83610798"
---
# <a name="isymunmanagedsourceservermodule-interface"></a><span data-ttu-id="e20f9-102">ISymUnmanagedSourceServerModule — Interfejs</span><span class="sxs-lookup"><span data-stu-id="e20f9-102">ISymUnmanagedSourceServerModule Interface</span></span>
<span data-ttu-id="e20f9-103">Zapewnia dane serwera źródłowego dla modułu.</span><span class="sxs-lookup"><span data-stu-id="e20f9-103">Provides source server data for a module.</span></span> <span data-ttu-id="e20f9-104">Uzyskaj ten interfejs, wywołując `QueryInterface` obiekt, który implementuje interfejs [ISymUnmanagedReader](isymunmanagedreader-interface.md) .</span><span class="sxs-lookup"><span data-stu-id="e20f9-104">Obtain this interface by calling `QueryInterface` on an object that implements the [ISymUnmanagedReader](isymunmanagedreader-interface.md) interface.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="e20f9-105">Metody</span><span class="sxs-lookup"><span data-stu-id="e20f9-105">Methods</span></span>  
  
|<span data-ttu-id="e20f9-106">Metoda</span><span class="sxs-lookup"><span data-stu-id="e20f9-106">Method</span></span>|<span data-ttu-id="e20f9-107">Opis</span><span class="sxs-lookup"><span data-stu-id="e20f9-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="e20f9-108">GetSourceServerData, metoda</span><span class="sxs-lookup"><span data-stu-id="e20f9-108">GetSourceServerData Method</span></span>](isymunmanagedsourceservermodule-getsourceserverdata-method.md)|<span data-ttu-id="e20f9-109">Zwraca dane serwera źródłowego dla modułu.</span><span class="sxs-lookup"><span data-stu-id="e20f9-109">Returns the source server data for the module.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="e20f9-110">Wymagania</span><span class="sxs-lookup"><span data-stu-id="e20f9-110">Requirements</span></span>  
 <span data-ttu-id="e20f9-111">**Nagłówek:** CorSym. idl, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="e20f9-111">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e20f9-112">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="e20f9-112">See also</span></span>

- [<span data-ttu-id="e20f9-113">Interfejsy magazynu symboli diagnostycznych</span><span class="sxs-lookup"><span data-stu-id="e20f9-113">Diagnostics Symbol Store Interfaces</span></span>](diagnostics-symbol-store-interfaces.md)
