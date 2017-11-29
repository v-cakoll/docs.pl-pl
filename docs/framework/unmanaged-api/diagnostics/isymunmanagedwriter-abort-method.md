---
title: "ISymUnmanagedWriter::Abort — Metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ISymUnmanagedWriter.Abort
api_location: diasymreader.dll
api_type: COM
f1_keywords: ISymUnmanagedWriter::Abort
helpviewer_keywords:
- ISymUnmanagedWriter::Abort method [.NET Framework debugging]
- Abort method, ISymUnmanagedWriter interface [.NET Framework debugging]
ms.assetid: 416b220f-38d4-48e0-bb49-d2faa7366702
topic_type: apiref
caps.latest.revision: "8"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 29dd11972e8db80f36820bba1eb679070d02146e
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="isymunmanagedwriterabort-method"></a><span data-ttu-id="5c3ab-102">ISymUnmanagedWriter::Abort — Metoda</span><span class="sxs-lookup"><span data-stu-id="5c3ab-102">ISymUnmanagedWriter::Abort Method</span></span>
<span data-ttu-id="5c3ab-103">Zamyka twórcę symbolu bez zatwierdzania symbole w magazynie symboli.</span><span class="sxs-lookup"><span data-stu-id="5c3ab-103">Closes the symbol writer without committing the symbols to the symbol store.</span></span> <span data-ttu-id="5c3ab-104">Po tym wywołaniu twórcę symbol staje się nieprawidłowy dla dalszego aktualizacji.</span><span class="sxs-lookup"><span data-stu-id="5c3ab-104">After this call, the symbol writer becomes invalid for further updates.</span></span> <span data-ttu-id="5c3ab-105">Aby zatwierdzić symbole i Zamknij moduł zapisujący symbolu, użyj [ISymUnmanagedWriter::Close](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-close-method.md) metody zamiast tego.</span><span class="sxs-lookup"><span data-stu-id="5c3ab-105">To commit the symbols and close the symbol writer, use the [ISymUnmanagedWriter::Close](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-close-method.md) method instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5c3ab-106">Składnia</span><span class="sxs-lookup"><span data-stu-id="5c3ab-106">Syntax</span></span>  
  
```  
HRESULT Abort();  
```  
  
## <a name="return-value"></a><span data-ttu-id="5c3ab-107">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="5c3ab-107">Return Value</span></span>  
 <span data-ttu-id="5c3ab-108">Wartość S_OK, jeśli metoda zakończy się pomyślnie; w przeciwnym razie E_FAIL lub inny kod błędu.</span><span class="sxs-lookup"><span data-stu-id="5c3ab-108">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5c3ab-109">Wymagania</span><span class="sxs-lookup"><span data-stu-id="5c3ab-109">Requirements</span></span>  
 <span data-ttu-id="5c3ab-110">**Nagłówek:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="5c3ab-110">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5c3ab-111">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="5c3ab-111">See Also</span></span>  
 [<span data-ttu-id="5c3ab-112">ISymUnmanagedWriter — interfejs</span><span class="sxs-lookup"><span data-stu-id="5c3ab-112">ISymUnmanagedWriter Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-interface.md)
