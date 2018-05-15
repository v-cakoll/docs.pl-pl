---
title: ISymUnmanagedWriter::OpenNamespace — Metoda
ms.date: 03/30/2017
api_name:
- ISymUnmanagedWriter.OpenNamespace
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedWriter::OpenNamespace
helpviewer_keywords:
- ISymUnmanagedWriter::OpenNamespace method [.NET Framework debugging]
- OpenNamespace method [.NET Framework debugging]
ms.assetid: 426f4e4f-e60d-4ad1-b546-a10e3c55c283
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 02f57fdbbc1ea9a391d9c58c7ab49af0ef02f001
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="isymunmanagedwriteropennamespace-method"></a><span data-ttu-id="bdd3b-102">ISymUnmanagedWriter::OpenNamespace — Metoda</span><span class="sxs-lookup"><span data-stu-id="bdd3b-102">ISymUnmanagedWriter::OpenNamespace Method</span></span>
<span data-ttu-id="bdd3b-103">Zostanie otwarty nowy obszar nazw.</span><span class="sxs-lookup"><span data-stu-id="bdd3b-103">Opens a new namespace.</span></span> <span data-ttu-id="bdd3b-104">Tę metodę należy wywołać przed zdefiniowaniem metod lub zmienne, które zajmują przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="bdd3b-104">Call this method before defining methods or variables that occupy a namespace.</span></span> <span data-ttu-id="bdd3b-105">Przestrzenie nazw mogą być zagnieżdżone.</span><span class="sxs-lookup"><span data-stu-id="bdd3b-105">Namespaces can be nested.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bdd3b-106">Składnia</span><span class="sxs-lookup"><span data-stu-id="bdd3b-106">Syntax</span></span>  
  
```  
HRESULT OpenNamespace(  
    [in] const WCHAR *name);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="bdd3b-107">Parametry</span><span class="sxs-lookup"><span data-stu-id="bdd3b-107">Parameters</span></span>  
 `name`  
 <span data-ttu-id="bdd3b-108">[in] Wskaźnik na nazwę nowej przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="bdd3b-108">[in] A pointer to the name of the new namespace.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="bdd3b-109">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="bdd3b-109">Return Value</span></span>  
 <span data-ttu-id="bdd3b-110">Wartość S_OK, jeśli metoda zakończy się pomyślnie; w przeciwnym razie E_FAIL lub inny kod błędu.</span><span class="sxs-lookup"><span data-stu-id="bdd3b-110">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="bdd3b-111">Wymagania</span><span class="sxs-lookup"><span data-stu-id="bdd3b-111">Requirements</span></span>  
 <span data-ttu-id="bdd3b-112">**Header:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="bdd3b-112">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bdd3b-113">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="bdd3b-113">See Also</span></span>  
 [<span data-ttu-id="bdd3b-114">ISymUnmanagedWriter, interfejs</span><span class="sxs-lookup"><span data-stu-id="bdd3b-114">ISymUnmanagedWriter Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-interface.md)  
 [<span data-ttu-id="bdd3b-115">CloseNamespace, metoda</span><span class="sxs-lookup"><span data-stu-id="bdd3b-115">CloseNamespace Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-closenamespace-method.md)
