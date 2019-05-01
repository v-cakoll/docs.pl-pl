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
ms.openlocfilehash: 090183cad17aff6faf5e79639eadff086c1a26ce
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61797465"
---
# <a name="isymunmanagedwriterabort-method"></a><span data-ttu-id="68dfb-102">ISymUnmanagedWriter::Abort — Metoda</span><span class="sxs-lookup"><span data-stu-id="68dfb-102">ISymUnmanagedWriter::Abort Method</span></span>
<span data-ttu-id="68dfb-103">Zamyka moduł zapisujący symboli nie poświęcając symbole do magazynu symboli.</span><span class="sxs-lookup"><span data-stu-id="68dfb-103">Closes the symbol writer without committing the symbols to the symbol store.</span></span> <span data-ttu-id="68dfb-104">Po tym wywołaniu moduł zapisujący symbol staje się nieprawidłowy dalsze aktualizacje.</span><span class="sxs-lookup"><span data-stu-id="68dfb-104">After this call, the symbol writer becomes invalid for further updates.</span></span> <span data-ttu-id="68dfb-105">Aby zatwierdzić symboli i zamknąć Edytor symboli, należy użyć [ISymUnmanagedWriter::Close](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-close-method.md) metody zamiast tego.</span><span class="sxs-lookup"><span data-stu-id="68dfb-105">To commit the symbols and close the symbol writer, use the [ISymUnmanagedWriter::Close](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-close-method.md) method instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="68dfb-106">Składnia</span><span class="sxs-lookup"><span data-stu-id="68dfb-106">Syntax</span></span>  
  
```  
HRESULT Abort();  
```  
  
## <a name="return-value"></a><span data-ttu-id="68dfb-107">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="68dfb-107">Return Value</span></span>  
 <span data-ttu-id="68dfb-108">S_OK, jeśli metoda się powiedzie; w przeciwnym razie E_FAIL lub innego kodu błędu.</span><span class="sxs-lookup"><span data-stu-id="68dfb-108">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="68dfb-109">Wymagania</span><span class="sxs-lookup"><span data-stu-id="68dfb-109">Requirements</span></span>  
 <span data-ttu-id="68dfb-110">**Nagłówek:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="68dfb-110">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="68dfb-111">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="68dfb-111">See also</span></span>

- [<span data-ttu-id="68dfb-112">ISymUnmanagedWriter, interfejs</span><span class="sxs-lookup"><span data-stu-id="68dfb-112">ISymUnmanagedWriter Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-interface.md)
