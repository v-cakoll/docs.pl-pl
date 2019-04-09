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
ms.openlocfilehash: 4d3497d3167715d3e8a04f10a6687260949e4a36
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59104705"
---
# <a name="isymunmanagedwriterclose-method"></a><span data-ttu-id="2384b-102">ISymUnmanagedWriter::Close — Metoda</span><span class="sxs-lookup"><span data-stu-id="2384b-102">ISymUnmanagedWriter::Close Method</span></span>
<span data-ttu-id="2384b-103">Zamyka moduł zapisujący symbol po zatwierdzeniu symbole do magazynu symboli.</span><span class="sxs-lookup"><span data-stu-id="2384b-103">Closes the symbol writer after committing the symbols to the symbol store.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2384b-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="2384b-104">Syntax</span></span>  
  
```  
HRESULT Close();  
```  
  
## <a name="return-value"></a><span data-ttu-id="2384b-105">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="2384b-105">Return Value</span></span>  
 <span data-ttu-id="2384b-106">S_OK, jeśli metoda się powiedzie; w przeciwnym razie E_FAIL lub innego kodu błędu.</span><span class="sxs-lookup"><span data-stu-id="2384b-106">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="2384b-107">Uwagi</span><span class="sxs-lookup"><span data-stu-id="2384b-107">Remarks</span></span>  
 <span data-ttu-id="2384b-108">Po tym wywołaniu moduł zapisujący symbol staje się nieprawidłowy dalsze aktualizacje.</span><span class="sxs-lookup"><span data-stu-id="2384b-108">After this call, the symbol writer becomes invalid for further updates.</span></span> <span data-ttu-id="2384b-109">Aby zamknąć Edytor symboli nie poświęcając symbole, należy użyć [ISymUnmanagedWriter::Abort](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-abort-method.md) metody zamiast tego.</span><span class="sxs-lookup"><span data-stu-id="2384b-109">To close the symbol writer without committing the symbols, use the [ISymUnmanagedWriter::Abort](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-abort-method.md) method instead.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2384b-110">Wymagania</span><span class="sxs-lookup"><span data-stu-id="2384b-110">Requirements</span></span>  
 <span data-ttu-id="2384b-111">**Nagłówek:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="2384b-111">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2384b-112">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="2384b-112">See also</span></span>

- [<span data-ttu-id="2384b-113">ISymUnmanagedWriter — Interfejs</span><span class="sxs-lookup"><span data-stu-id="2384b-113">ISymUnmanagedWriter Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-interface.md)
