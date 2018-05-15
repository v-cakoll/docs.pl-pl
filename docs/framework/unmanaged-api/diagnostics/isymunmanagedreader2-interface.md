---
title: ISymUnmanagedReader2 — Interfejs
ms.date: 03/30/2017
api_name:
- ISymUnmanagedReader2
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedReader2
helpviewer_keywords:
- ISymUnmanagedReader2 interface [.NET Framework debugging]
ms.assetid: a01a881b-82a3-4b3e-a3a9-9dc305c2e5f7
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 1dfc67ecf1eeb9ea5a19c98a8c378e73021da6c8
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="isymunmanagedreader2-interface"></a><span data-ttu-id="fcc06-102">ISymUnmanagedReader2 — Interfejs</span><span class="sxs-lookup"><span data-stu-id="fcc06-102">ISymUnmanagedReader2 Interface</span></span>
<span data-ttu-id="fcc06-103">Reprezentuje czytnika symboli, która zapewnia dostęp do dokumentów, metod i zmiennych w magazynie symboli.</span><span class="sxs-lookup"><span data-stu-id="fcc06-103">Represents a symbol reader that provides access to documents, methods, and variables within a symbol store.</span></span> <span data-ttu-id="fcc06-104">Ten interfejs stanowi rozszerzenie [ISymUnmanagedReader](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-interface.md) interfejsu.</span><span class="sxs-lookup"><span data-stu-id="fcc06-104">This interface extends the [ISymUnmanagedReader](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-interface.md) interface.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="fcc06-105">Metody</span><span class="sxs-lookup"><span data-stu-id="fcc06-105">Methods</span></span>  
  
|<span data-ttu-id="fcc06-106">Metoda</span><span class="sxs-lookup"><span data-stu-id="fcc06-106">Method</span></span>|<span data-ttu-id="fcc06-107">Opis</span><span class="sxs-lookup"><span data-stu-id="fcc06-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="fcc06-108">GetMethodByVersionPreRemap, metoda</span><span class="sxs-lookup"><span data-stu-id="fcc06-108">GetMethodByVersionPreRemap Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader2-getmethodbyversionpreremap-method.md)|<span data-ttu-id="fcc06-109">Pobierz metodę czytnika symboli podany token metody i numer wersji edit-and-continue.</span><span class="sxs-lookup"><span data-stu-id="fcc06-109">Get a symbol reader method, given a method token and an edit-and-continue version number.</span></span>|  
|[<span data-ttu-id="fcc06-110">GetMethodsInDocument, metoda</span><span class="sxs-lookup"><span data-stu-id="fcc06-110">GetMethodsInDocument Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader2-getmethodsindocument-method.md)|<span data-ttu-id="fcc06-111">Pobiera co metodę, która zawiera informacje dotyczące wiersza udostępnionego dokumentu.</span><span class="sxs-lookup"><span data-stu-id="fcc06-111">Gets every method that has line information in the provided document.</span></span>|  
|[<span data-ttu-id="fcc06-112">GetSymAttributePreRemap, metoda</span><span class="sxs-lookup"><span data-stu-id="fcc06-112">GetSymAttributePreRemap Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader2-getsymattributepreremap-method.md)|<span data-ttu-id="fcc06-113">Pobiera atrybut niestandardowy ustalane na podstawie jego nazwy.</span><span class="sxs-lookup"><span data-stu-id="fcc06-113">Gets a custom attribute based upon its name.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="fcc06-114">Wymagania</span><span class="sxs-lookup"><span data-stu-id="fcc06-114">Requirements</span></span>  
 <span data-ttu-id="fcc06-115">**Header:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="fcc06-115">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fcc06-116">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="fcc06-116">See Also</span></span>  
 [<span data-ttu-id="fcc06-117">Interfejsy magazynu symboli diagnostycznych</span><span class="sxs-lookup"><span data-stu-id="fcc06-117">Diagnostics Symbol Store Interfaces</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/diagnostics-symbol-store-interfaces.md)  
 [<span data-ttu-id="fcc06-118">ISymUnmanagedReader, interfejs</span><span class="sxs-lookup"><span data-stu-id="fcc06-118">ISymUnmanagedReader Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-interface.md)
