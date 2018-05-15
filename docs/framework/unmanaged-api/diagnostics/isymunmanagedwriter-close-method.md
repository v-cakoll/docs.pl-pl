---
title: ISymUnmanagedWriter::Close — Metoda
ms.date: 03/30/2017
api_name:
- ISymUnmanagedWriter.Close
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedWriter::Close
helpviewer_keywords:
- Close method, ISymUnmanagedWriter interface [.NET Framework debugging]
- ISymUnmanagedWriter::Close method [.NET Framework debugging]
ms.assetid: 4cce59e1-80b9-4fc4-b3aa-126f1c5876bc
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 30747fa25528f5679264ebfb67addf401b7d01d9
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="isymunmanagedwriterclose-method"></a><span data-ttu-id="84b88-102">ISymUnmanagedWriter::Close — Metoda</span><span class="sxs-lookup"><span data-stu-id="84b88-102">ISymUnmanagedWriter::Close Method</span></span>
<span data-ttu-id="84b88-103">Zamyka twórcę symbol po zatwierdzania symbole w magazynie symboli.</span><span class="sxs-lookup"><span data-stu-id="84b88-103">Closes the symbol writer after committing the symbols to the symbol store.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="84b88-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="84b88-104">Syntax</span></span>  
  
```  
HRESULT Close();  
```  
  
## <a name="return-value"></a><span data-ttu-id="84b88-105">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="84b88-105">Return Value</span></span>  
 <span data-ttu-id="84b88-106">Wartość S_OK, jeśli metoda zakończy się pomyślnie; w przeciwnym razie E_FAIL lub inny kod błędu.</span><span class="sxs-lookup"><span data-stu-id="84b88-106">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="84b88-107">Uwagi</span><span class="sxs-lookup"><span data-stu-id="84b88-107">Remarks</span></span>  
 <span data-ttu-id="84b88-108">Po tym wywołaniu twórcę symbol staje się nieprawidłowy dla dalszego aktualizacji.</span><span class="sxs-lookup"><span data-stu-id="84b88-108">After this call, the symbol writer becomes invalid for further updates.</span></span> <span data-ttu-id="84b88-109">Aby zamknąć twórcę symbolu bez zatwierdzania symbole, użyj [ISymUnmanagedWriter::Abort](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-abort-method.md) metody zamiast tego.</span><span class="sxs-lookup"><span data-stu-id="84b88-109">To close the symbol writer without committing the symbols, use the [ISymUnmanagedWriter::Abort](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-abort-method.md) method instead.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="84b88-110">Wymagania</span><span class="sxs-lookup"><span data-stu-id="84b88-110">Requirements</span></span>  
 <span data-ttu-id="84b88-111">**Header:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="84b88-111">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="84b88-112">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="84b88-112">See Also</span></span>  
 [<span data-ttu-id="84b88-113">ISymUnmanagedWriter, interfejs</span><span class="sxs-lookup"><span data-stu-id="84b88-113">ISymUnmanagedWriter Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-interface.md)
