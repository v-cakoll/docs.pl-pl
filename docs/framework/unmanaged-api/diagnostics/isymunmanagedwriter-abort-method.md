---
title: ISymUnmanagedWriter::Abort — Metoda
ms.date: 03/30/2017
api_name:
- ISymUnmanagedWriter.Abort
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedWriter::Abort
helpviewer_keywords:
- ISymUnmanagedWriter::Abort method [.NET Framework debugging]
- Abort method, ISymUnmanagedWriter interface [.NET Framework debugging]
ms.assetid: 416b220f-38d4-48e0-bb49-d2faa7366702
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: eb6a3e65b1f1d59cde3bff99e491bcf09816c8ad
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33428061"
---
# <a name="isymunmanagedwriterabort-method"></a><span data-ttu-id="da15c-102">ISymUnmanagedWriter::Abort — Metoda</span><span class="sxs-lookup"><span data-stu-id="da15c-102">ISymUnmanagedWriter::Abort Method</span></span>
<span data-ttu-id="da15c-103">Zamyka twórcę symbolu bez zatwierdzania symbole w magazynie symboli.</span><span class="sxs-lookup"><span data-stu-id="da15c-103">Closes the symbol writer without committing the symbols to the symbol store.</span></span> <span data-ttu-id="da15c-104">Po tym wywołaniu twórcę symbol staje się nieprawidłowy dla dalszego aktualizacji.</span><span class="sxs-lookup"><span data-stu-id="da15c-104">After this call, the symbol writer becomes invalid for further updates.</span></span> <span data-ttu-id="da15c-105">Aby zatwierdzić symbole i Zamknij moduł zapisujący symbolu, użyj [ISymUnmanagedWriter::Close](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-close-method.md) metody zamiast tego.</span><span class="sxs-lookup"><span data-stu-id="da15c-105">To commit the symbols and close the symbol writer, use the [ISymUnmanagedWriter::Close](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-close-method.md) method instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="da15c-106">Składnia</span><span class="sxs-lookup"><span data-stu-id="da15c-106">Syntax</span></span>  
  
```  
HRESULT Abort();  
```  
  
## <a name="return-value"></a><span data-ttu-id="da15c-107">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="da15c-107">Return Value</span></span>  
 <span data-ttu-id="da15c-108">Wartość S_OK, jeśli metoda zakończy się pomyślnie; w przeciwnym razie E_FAIL lub inny kod błędu.</span><span class="sxs-lookup"><span data-stu-id="da15c-108">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="da15c-109">Wymagania</span><span class="sxs-lookup"><span data-stu-id="da15c-109">Requirements</span></span>  
 <span data-ttu-id="da15c-110">**Header:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="da15c-110">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="da15c-111">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="da15c-111">See Also</span></span>  
 [<span data-ttu-id="da15c-112">ISymUnmanagedWriter, interfejs</span><span class="sxs-lookup"><span data-stu-id="da15c-112">ISymUnmanagedWriter Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-interface.md)
