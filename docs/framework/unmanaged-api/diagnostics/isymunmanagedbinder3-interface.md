---
title: "ISymUnmanagedBinder3 — Interfejs"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ISymUnmanagedBinder3
api_location: diasymreader.dll
api_type: COM
f1_keywords: ISymUnmanagedBinder3 Interface
helpviewer_keywords: ISymUnmanagedBinder3 interface [.NET Framework debugging]
ms.assetid: 37527a84-4b03-4f08-8135-94d898599089
topic_type: apiref
caps.latest.revision: "7"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: df5cd6d4015fad1baf98909ee9cc923cd9bce05e
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="isymunmanagedbinder3-interface"></a><span data-ttu-id="183f0-102">ISymUnmanagedBinder3 — Interfejs</span><span class="sxs-lookup"><span data-stu-id="183f0-102">ISymUnmanagedBinder3 Interface</span></span>
<span data-ttu-id="183f0-103">Rozszerzenie interfejsu integratora symbolu.</span><span class="sxs-lookup"><span data-stu-id="183f0-103">Extends the symbol binder interface.</span></span> <span data-ttu-id="183f0-104">Uzyskanie przez wywołanie metody tego interfejsu `QueryInterface` na obiekt, który implementuje `ISymUnmanagedBinder` interfejsu.</span><span class="sxs-lookup"><span data-stu-id="183f0-104">Obtain this interface by calling `QueryInterface` on an object that implements the `ISymUnmanagedBinder` interface.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="183f0-105">Jest to zagrożenie, aby otworzyć plik programu (PDB) bazy danych z niezaufanego źródła.</span><span class="sxs-lookup"><span data-stu-id="183f0-105">It is a security risk to open a program database (PDB) file from an untrusted source.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="183f0-106">Metody</span><span class="sxs-lookup"><span data-stu-id="183f0-106">Methods</span></span>  
  
|<span data-ttu-id="183f0-107">Metoda</span><span class="sxs-lookup"><span data-stu-id="183f0-107">Method</span></span>|<span data-ttu-id="183f0-108">Opis</span><span class="sxs-lookup"><span data-stu-id="183f0-108">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="183f0-109">GetReaderFromCallback — metoda</span><span class="sxs-lookup"><span data-stu-id="183f0-109">GetReaderFromCallback Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedbinder3-getreaderfromcallback-method.md)|<span data-ttu-id="183f0-110">Zezwala użytkownikowi na wdrożenie lub podać za pośrednictwem wywołania zwrotnego albo `IID_IDiaReadExeAtRVACallback` lub `IID_IDiaReadExeAtOffsetCallback` Aby uzyskać informacje o debugowaniu katalogu z pamięci</span><span class="sxs-lookup"><span data-stu-id="183f0-110">Allows the user to implement or supply via callback either an `IID_IDiaReadExeAtRVACallback` or `IID_IDiaReadExeAtOffsetCallback` to obtain the Debug directory information from memory</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="183f0-111">Wymagania</span><span class="sxs-lookup"><span data-stu-id="183f0-111">Requirements</span></span>  
 <span data-ttu-id="183f0-112">**Nagłówek:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="183f0-112">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="183f0-113">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="183f0-113">See Also</span></span>  
 [<span data-ttu-id="183f0-114">Interfejsy magazynu symboli diagnostycznych</span><span class="sxs-lookup"><span data-stu-id="183f0-114">Diagnostics Symbol Store Interfaces</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/diagnostics-symbol-store-interfaces.md)  
 [<span data-ttu-id="183f0-115">ISymUnmanagedBinder — interfejs</span><span class="sxs-lookup"><span data-stu-id="183f0-115">ISymUnmanagedBinder Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedbinder-interface.md)  
 [<span data-ttu-id="183f0-116">ISymUnmanagedBinder2 — interfejs</span><span class="sxs-lookup"><span data-stu-id="183f0-116">ISymUnmanagedBinder2 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedbinder2-interface.md)
