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
ms.openlocfilehash: a08695c4e5df6aaa63bedecf68b741302e5ddd8e
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54524948"
---
# <a name="isymunmanagedreader2-interface"></a><span data-ttu-id="9e456-102">ISymUnmanagedReader2 — Interfejs</span><span class="sxs-lookup"><span data-stu-id="9e456-102">ISymUnmanagedReader2 Interface</span></span>
<span data-ttu-id="9e456-103">Reprezentuje czytnik symbolu, który zapewnia dostęp do dokumentów, metod i zmiennych w magazynie symboli.</span><span class="sxs-lookup"><span data-stu-id="9e456-103">Represents a symbol reader that provides access to documents, methods, and variables within a symbol store.</span></span> <span data-ttu-id="9e456-104">Ten interfejs rozszerza [isymunmanagedreader —](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-interface.md) interfejsu.</span><span class="sxs-lookup"><span data-stu-id="9e456-104">This interface extends the [ISymUnmanagedReader](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-interface.md) interface.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="9e456-105">Metody</span><span class="sxs-lookup"><span data-stu-id="9e456-105">Methods</span></span>  
  
|<span data-ttu-id="9e456-106">Metoda</span><span class="sxs-lookup"><span data-stu-id="9e456-106">Method</span></span>|<span data-ttu-id="9e456-107">Opis</span><span class="sxs-lookup"><span data-stu-id="9e456-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="9e456-108">GetMethodByVersionPreRemap, metoda</span><span class="sxs-lookup"><span data-stu-id="9e456-108">GetMethodByVersionPreRemap Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader2-getmethodbyversionpreremap-method.md)|<span data-ttu-id="9e456-109">Uzyskaj metodę czytnika symboli podany token metody i numeru wersji edit-and-continue.</span><span class="sxs-lookup"><span data-stu-id="9e456-109">Get a symbol reader method, given a method token and an edit-and-continue version number.</span></span>|  
|[<span data-ttu-id="9e456-110">GetMethodsInDocument, metoda</span><span class="sxs-lookup"><span data-stu-id="9e456-110">GetMethodsInDocument Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader2-getmethodsindocument-method.md)|<span data-ttu-id="9e456-111">Pobiera każdej metody, która ma informacje wiersza w podany dokument.</span><span class="sxs-lookup"><span data-stu-id="9e456-111">Gets every method that has line information in the provided document.</span></span>|  
|[<span data-ttu-id="9e456-112">GetSymAttributePreRemap, metoda</span><span class="sxs-lookup"><span data-stu-id="9e456-112">GetSymAttributePreRemap Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader2-getsymattributepreremap-method.md)|<span data-ttu-id="9e456-113">Pobiera atrybut niestandardowy na podstawie jego nazwy.</span><span class="sxs-lookup"><span data-stu-id="9e456-113">Gets a custom attribute based upon its name.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="9e456-114">Wymagania</span><span class="sxs-lookup"><span data-stu-id="9e456-114">Requirements</span></span>  
 <span data-ttu-id="9e456-115">**Nagłówek:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="9e456-115">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9e456-116">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="9e456-116">See also</span></span>
- [<span data-ttu-id="9e456-117">Interfejsy magazynu symboli diagnostycznych</span><span class="sxs-lookup"><span data-stu-id="9e456-117">Diagnostics Symbol Store Interfaces</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/diagnostics-symbol-store-interfaces.md)
- [<span data-ttu-id="9e456-118">ISymUnmanagedReader, interfejs</span><span class="sxs-lookup"><span data-stu-id="9e456-118">ISymUnmanagedReader Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-interface.md)
