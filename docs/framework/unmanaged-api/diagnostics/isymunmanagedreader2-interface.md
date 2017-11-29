---
title: "ISymUnmanagedReader2 — Interfejs"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ISymUnmanagedReader2
api_location: diasymreader.dll
api_type: COM
f1_keywords: ISymUnmanagedReader2
helpviewer_keywords: ISymUnmanagedReader2 interface [.NET Framework debugging]
ms.assetid: a01a881b-82a3-4b3e-a3a9-9dc305c2e5f7
topic_type: apiref
caps.latest.revision: "8"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: b23e166249659b94d454070c01c003495d1018a9
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="isymunmanagedreader2-interface"></a><span data-ttu-id="fd6bc-102">ISymUnmanagedReader2 — Interfejs</span><span class="sxs-lookup"><span data-stu-id="fd6bc-102">ISymUnmanagedReader2 Interface</span></span>
<span data-ttu-id="fd6bc-103">Reprezentuje czytnika symboli, która zapewnia dostęp do dokumentów, metod i zmiennych w magazynie symboli.</span><span class="sxs-lookup"><span data-stu-id="fd6bc-103">Represents a symbol reader that provides access to documents, methods, and variables within a symbol store.</span></span> <span data-ttu-id="fd6bc-104">Ten interfejs stanowi rozszerzenie [ISymUnmanagedReader](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-interface.md) interfejsu.</span><span class="sxs-lookup"><span data-stu-id="fd6bc-104">This interface extends the [ISymUnmanagedReader](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-interface.md) interface.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="fd6bc-105">Metody</span><span class="sxs-lookup"><span data-stu-id="fd6bc-105">Methods</span></span>  
  
|<span data-ttu-id="fd6bc-106">Metoda</span><span class="sxs-lookup"><span data-stu-id="fd6bc-106">Method</span></span>|<span data-ttu-id="fd6bc-107">Opis</span><span class="sxs-lookup"><span data-stu-id="fd6bc-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="fd6bc-108">GetMethodByVersionPreRemap — metoda</span><span class="sxs-lookup"><span data-stu-id="fd6bc-108">GetMethodByVersionPreRemap Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader2-getmethodbyversionpreremap-method.md)|<span data-ttu-id="fd6bc-109">Pobierz metodę czytnika symboli podany token metody i numer wersji edit-and-continue.</span><span class="sxs-lookup"><span data-stu-id="fd6bc-109">Get a symbol reader method, given a method token and an edit-and-continue version number.</span></span>|  
|[<span data-ttu-id="fd6bc-110">GetMethodsInDocument — metoda</span><span class="sxs-lookup"><span data-stu-id="fd6bc-110">GetMethodsInDocument Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader2-getmethodsindocument-method.md)|<span data-ttu-id="fd6bc-111">Pobiera co metodę, która zawiera informacje dotyczące wiersza udostępnionego dokumentu.</span><span class="sxs-lookup"><span data-stu-id="fd6bc-111">Gets every method that has line information in the provided document.</span></span>|  
|[<span data-ttu-id="fd6bc-112">GetSymAttributePreRemap — metoda</span><span class="sxs-lookup"><span data-stu-id="fd6bc-112">GetSymAttributePreRemap Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader2-getsymattributepreremap-method.md)|<span data-ttu-id="fd6bc-113">Pobiera atrybut niestandardowy ustalane na podstawie jego nazwy.</span><span class="sxs-lookup"><span data-stu-id="fd6bc-113">Gets a custom attribute based upon its name.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="fd6bc-114">Wymagania</span><span class="sxs-lookup"><span data-stu-id="fd6bc-114">Requirements</span></span>  
 <span data-ttu-id="fd6bc-115">**Nagłówek:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="fd6bc-115">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fd6bc-116">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="fd6bc-116">See Also</span></span>  
 [<span data-ttu-id="fd6bc-117">Interfejsy magazynu symboli diagnostycznych</span><span class="sxs-lookup"><span data-stu-id="fd6bc-117">Diagnostics Symbol Store Interfaces</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/diagnostics-symbol-store-interfaces.md)  
 [<span data-ttu-id="fd6bc-118">ISymUnmanagedReader — interfejs</span><span class="sxs-lookup"><span data-stu-id="fd6bc-118">ISymUnmanagedReader Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-interface.md)
