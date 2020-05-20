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
ms.openlocfilehash: 0a7ecd475a8031fedb2c8474593b45045fcc6fb9
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/19/2020
ms.locfileid: "83610135"
---
# <a name="isymunmanagedwriterclose-method"></a><span data-ttu-id="137ef-102">ISymUnmanagedWriter::Close — Metoda</span><span class="sxs-lookup"><span data-stu-id="137ef-102">ISymUnmanagedWriter::Close Method</span></span>
<span data-ttu-id="137ef-103">Zamyka moduł zapisujący symboli po zatwierdzeniu symboli do magazynu symboli.</span><span class="sxs-lookup"><span data-stu-id="137ef-103">Closes the symbol writer after committing the symbols to the symbol store.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="137ef-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="137ef-104">Syntax</span></span>  
  
```cpp  
HRESULT Close();  
```  
  
## <a name="return-value"></a><span data-ttu-id="137ef-105">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="137ef-105">Return Value</span></span>  
 <span data-ttu-id="137ef-106">S_OK, jeśli metoda się powiedzie; w przeciwnym razie E_FAIL lub inny kod błędu.</span><span class="sxs-lookup"><span data-stu-id="137ef-106">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="137ef-107">Uwagi</span><span class="sxs-lookup"><span data-stu-id="137ef-107">Remarks</span></span>  
 <span data-ttu-id="137ef-108">Po tym wywołaniu moduł zapisujący symboli jest nieprawidłowy dla dalszych aktualizacji.</span><span class="sxs-lookup"><span data-stu-id="137ef-108">After this call, the symbol writer becomes invalid for further updates.</span></span> <span data-ttu-id="137ef-109">Aby zamknąć moduł zapisujący symboli bez przekazywania symboli, zamiast tego użyj metody [ISymUnmanagedWriter:: Abort](isymunmanagedwriter-abort-method.md) .</span><span class="sxs-lookup"><span data-stu-id="137ef-109">To close the symbol writer without committing the symbols, use the [ISymUnmanagedWriter::Abort](isymunmanagedwriter-abort-method.md) method instead.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="137ef-110">Wymagania</span><span class="sxs-lookup"><span data-stu-id="137ef-110">Requirements</span></span>  
 <span data-ttu-id="137ef-111">**Nagłówek:** CorSym. idl, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="137ef-111">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="137ef-112">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="137ef-112">See also</span></span>

- [<span data-ttu-id="137ef-113">ISymUnmanagedWriter — Interfejs</span><span class="sxs-lookup"><span data-stu-id="137ef-113">ISymUnmanagedWriter Interface</span></span>](isymunmanagedwriter-interface.md)
