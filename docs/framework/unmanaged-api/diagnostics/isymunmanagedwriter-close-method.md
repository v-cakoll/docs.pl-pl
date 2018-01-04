---
title: "ISymUnmanagedWriter::Close — Metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ISymUnmanagedWriter.Close
api_location: diasymreader.dll
api_type: COM
f1_keywords: ISymUnmanagedWriter::Close
helpviewer_keywords:
- Close method, ISymUnmanagedWriter interface [.NET Framework debugging]
- ISymUnmanagedWriter::Close method [.NET Framework debugging]
ms.assetid: 4cce59e1-80b9-4fc4-b3aa-126f1c5876bc
topic_type: apiref
caps.latest.revision: "10"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 70f710802862c3237cbd67693f8366946926891e
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="isymunmanagedwriterclose-method"></a><span data-ttu-id="e5cf7-102">ISymUnmanagedWriter::Close — Metoda</span><span class="sxs-lookup"><span data-stu-id="e5cf7-102">ISymUnmanagedWriter::Close Method</span></span>
<span data-ttu-id="e5cf7-103">Zamyka twórcę symbol po zatwierdzania symbole w magazynie symboli.</span><span class="sxs-lookup"><span data-stu-id="e5cf7-103">Closes the symbol writer after committing the symbols to the symbol store.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e5cf7-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="e5cf7-104">Syntax</span></span>  
  
```  
HRESULT Close();  
```  
  
## <a name="return-value"></a><span data-ttu-id="e5cf7-105">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="e5cf7-105">Return Value</span></span>  
 <span data-ttu-id="e5cf7-106">Wartość S_OK, jeśli metoda zakończy się pomyślnie; w przeciwnym razie E_FAIL lub inny kod błędu.</span><span class="sxs-lookup"><span data-stu-id="e5cf7-106">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="e5cf7-107">Uwagi</span><span class="sxs-lookup"><span data-stu-id="e5cf7-107">Remarks</span></span>  
 <span data-ttu-id="e5cf7-108">Po tym wywołaniu twórcę symbol staje się nieprawidłowy dla dalszego aktualizacji.</span><span class="sxs-lookup"><span data-stu-id="e5cf7-108">After this call, the symbol writer becomes invalid for further updates.</span></span> <span data-ttu-id="e5cf7-109">Aby zamknąć twórcę symbolu bez zatwierdzania symbole, użyj [ISymUnmanagedWriter::Abort](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-abort-method.md) metody zamiast tego.</span><span class="sxs-lookup"><span data-stu-id="e5cf7-109">To close the symbol writer without committing the symbols, use the [ISymUnmanagedWriter::Abort](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-abort-method.md) method instead.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e5cf7-110">Wymagania</span><span class="sxs-lookup"><span data-stu-id="e5cf7-110">Requirements</span></span>  
 <span data-ttu-id="e5cf7-111">**Nagłówek:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="e5cf7-111">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e5cf7-112">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="e5cf7-112">See Also</span></span>  
 [<span data-ttu-id="e5cf7-113">ISymUnmanagedWriter, interfejs</span><span class="sxs-lookup"><span data-stu-id="e5cf7-113">ISymUnmanagedWriter Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-interface.md)
