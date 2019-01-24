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
ms.openlocfilehash: b4c79cb3df37a9ed10e46567be63aad29fee37c4
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54550191"
---
# <a name="isymunmanagedwriterabort-method"></a><span data-ttu-id="56bbd-102">ISymUnmanagedWriter::Abort — Metoda</span><span class="sxs-lookup"><span data-stu-id="56bbd-102">ISymUnmanagedWriter::Abort Method</span></span>
<span data-ttu-id="56bbd-103">Zamyka moduł zapisujący symboli nie poświęcając symbole do magazynu symboli.</span><span class="sxs-lookup"><span data-stu-id="56bbd-103">Closes the symbol writer without committing the symbols to the symbol store.</span></span> <span data-ttu-id="56bbd-104">Po tym wywołaniu moduł zapisujący symbol staje się nieprawidłowy dalsze aktualizacje.</span><span class="sxs-lookup"><span data-stu-id="56bbd-104">After this call, the symbol writer becomes invalid for further updates.</span></span> <span data-ttu-id="56bbd-105">Aby zatwierdzić symboli i zamknąć Edytor symboli, należy użyć [ISymUnmanagedWriter::Close](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-close-method.md) metody zamiast tego.</span><span class="sxs-lookup"><span data-stu-id="56bbd-105">To commit the symbols and close the symbol writer, use the [ISymUnmanagedWriter::Close](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-close-method.md) method instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="56bbd-106">Składnia</span><span class="sxs-lookup"><span data-stu-id="56bbd-106">Syntax</span></span>  
  
```  
HRESULT Abort();  
```  
  
## <a name="return-value"></a><span data-ttu-id="56bbd-107">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="56bbd-107">Return Value</span></span>  
 <span data-ttu-id="56bbd-108">S_OK, jeśli metoda się powiedzie; w przeciwnym razie E_FAIL lub innego kodu błędu.</span><span class="sxs-lookup"><span data-stu-id="56bbd-108">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="56bbd-109">Wymagania</span><span class="sxs-lookup"><span data-stu-id="56bbd-109">Requirements</span></span>  
 <span data-ttu-id="56bbd-110">**Nagłówek:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="56bbd-110">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="56bbd-111">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="56bbd-111">See also</span></span>
- [<span data-ttu-id="56bbd-112">ISymUnmanagedWriter, interfejs</span><span class="sxs-lookup"><span data-stu-id="56bbd-112">ISymUnmanagedWriter Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-interface.md)
