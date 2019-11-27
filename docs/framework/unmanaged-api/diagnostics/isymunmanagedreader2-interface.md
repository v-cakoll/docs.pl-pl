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
ms.openlocfilehash: a07c75e14244fb5bdf72ff2b0d344ae27672ef89
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/23/2019
ms.locfileid: "74448268"
---
# <a name="isymunmanagedreader2-interface"></a><span data-ttu-id="0a733-102">ISymUnmanagedReader2 — Interfejs</span><span class="sxs-lookup"><span data-stu-id="0a733-102">ISymUnmanagedReader2 Interface</span></span>
<span data-ttu-id="0a733-103">Reprezentuje czytnik symboli, który zapewnia dostęp do dokumentów, metod i zmiennych w magazynie symboli.</span><span class="sxs-lookup"><span data-stu-id="0a733-103">Represents a symbol reader that provides access to documents, methods, and variables within a symbol store.</span></span> <span data-ttu-id="0a733-104">Ten interfejs rozszerza interfejs [ISymUnmanagedReader](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-interface.md) .</span><span class="sxs-lookup"><span data-stu-id="0a733-104">This interface extends the [ISymUnmanagedReader](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-interface.md) interface.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="0a733-105">Metody</span><span class="sxs-lookup"><span data-stu-id="0a733-105">Methods</span></span>  
  
|<span data-ttu-id="0a733-106">Metoda</span><span class="sxs-lookup"><span data-stu-id="0a733-106">Method</span></span>|<span data-ttu-id="0a733-107">Opis</span><span class="sxs-lookup"><span data-stu-id="0a733-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="0a733-108">GetMethodByVersionPreRemap, metoda</span><span class="sxs-lookup"><span data-stu-id="0a733-108">GetMethodByVersionPreRemap Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader2-getmethodbyversionpreremap-method.md)|<span data-ttu-id="0a733-109">Pobierz metodę czytnika symboli, używając tokenu metody oraz numeru wersji Edit-and-Continue.</span><span class="sxs-lookup"><span data-stu-id="0a733-109">Get a symbol reader method, given a method token and an edit-and-continue version number.</span></span>|  
|[<span data-ttu-id="0a733-110">GetMethodsInDocument, metoda</span><span class="sxs-lookup"><span data-stu-id="0a733-110">GetMethodsInDocument Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader2-getmethodsindocument-method.md)|<span data-ttu-id="0a733-111">Pobiera każdą metodę, która zawiera informacje o wierszu w podanym dokumencie.</span><span class="sxs-lookup"><span data-stu-id="0a733-111">Gets every method that has line information in the provided document.</span></span>|  
|[<span data-ttu-id="0a733-112">GetSymAttributePreRemap, metoda</span><span class="sxs-lookup"><span data-stu-id="0a733-112">GetSymAttributePreRemap Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader2-getsymattributepreremap-method.md)|<span data-ttu-id="0a733-113">Pobiera atrybut niestandardowy na podstawie jego nazwy.</span><span class="sxs-lookup"><span data-stu-id="0a733-113">Gets a custom attribute based upon its name.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="0a733-114">Wymagania</span><span class="sxs-lookup"><span data-stu-id="0a733-114">Requirements</span></span>  
 <span data-ttu-id="0a733-115">**Nagłówek:** CorSym. idl, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="0a733-115">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0a733-116">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="0a733-116">See also</span></span>

- [<span data-ttu-id="0a733-117">Interfejsy magazynu symboli diagnostycznych</span><span class="sxs-lookup"><span data-stu-id="0a733-117">Diagnostics Symbol Store Interfaces</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/diagnostics-symbol-store-interfaces.md)
- [<span data-ttu-id="0a733-118">ISymUnmanagedReader, interfejs</span><span class="sxs-lookup"><span data-stu-id="0a733-118">ISymUnmanagedReader Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-interface.md)
