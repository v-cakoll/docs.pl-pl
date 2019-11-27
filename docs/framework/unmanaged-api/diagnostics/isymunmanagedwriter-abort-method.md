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
ms.openlocfilehash: 6074ec5248d27b1405d2367349904f6630df951b
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/23/2019
ms.locfileid: "74445996"
---
# <a name="isymunmanagedwriterabort-method"></a><span data-ttu-id="4983b-102">ISymUnmanagedWriter::Abort — Metoda</span><span class="sxs-lookup"><span data-stu-id="4983b-102">ISymUnmanagedWriter::Abort Method</span></span>
<span data-ttu-id="4983b-103">Zamyka moduł zapisujący symboli bez przekazywania symboli do magazynu symboli.</span><span class="sxs-lookup"><span data-stu-id="4983b-103">Closes the symbol writer without committing the symbols to the symbol store.</span></span> <span data-ttu-id="4983b-104">Po tym wywołaniu moduł zapisujący symboli jest nieprawidłowy dla dalszych aktualizacji.</span><span class="sxs-lookup"><span data-stu-id="4983b-104">After this call, the symbol writer becomes invalid for further updates.</span></span> <span data-ttu-id="4983b-105">Aby zatwierdzić symbole i zamknąć moduł zapisujący symboli, należy zamiast tego użyć metody [ISymUnmanagedWriter:: Close](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-close-method.md) .</span><span class="sxs-lookup"><span data-stu-id="4983b-105">To commit the symbols and close the symbol writer, use the [ISymUnmanagedWriter::Close](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-close-method.md) method instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4983b-106">Składnia</span><span class="sxs-lookup"><span data-stu-id="4983b-106">Syntax</span></span>  
  
```cpp  
HRESULT Abort();  
```  
  
## <a name="return-value"></a><span data-ttu-id="4983b-107">Wartość zwrócona</span><span class="sxs-lookup"><span data-stu-id="4983b-107">Return Value</span></span>  
 <span data-ttu-id="4983b-108">S_OK, jeśli metoda się powiedzie; w przeciwnym razie E_FAIL lub inny kod błędu.</span><span class="sxs-lookup"><span data-stu-id="4983b-108">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4983b-109">Wymagania</span><span class="sxs-lookup"><span data-stu-id="4983b-109">Requirements</span></span>  
 <span data-ttu-id="4983b-110">**Nagłówek:** CorSym. idl, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="4983b-110">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4983b-111">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="4983b-111">See also</span></span>

- [<span data-ttu-id="4983b-112">ISymUnmanagedWriter, interfejs</span><span class="sxs-lookup"><span data-stu-id="4983b-112">ISymUnmanagedWriter Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-interface.md)
