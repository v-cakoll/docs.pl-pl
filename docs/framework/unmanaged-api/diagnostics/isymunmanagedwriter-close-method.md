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
ms.openlocfilehash: fd7131c55f9c06a8fcfc0cad859c18e410169c78
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/10/2019
ms.locfileid: "67778197"
---
# <a name="isymunmanagedwriterclose-method"></a><span data-ttu-id="8ea8b-102">ISymUnmanagedWriter::Close — Metoda</span><span class="sxs-lookup"><span data-stu-id="8ea8b-102">ISymUnmanagedWriter::Close Method</span></span>
<span data-ttu-id="8ea8b-103">Zamyka moduł zapisujący symbol po zatwierdzeniu symbole do magazynu symboli.</span><span class="sxs-lookup"><span data-stu-id="8ea8b-103">Closes the symbol writer after committing the symbols to the symbol store.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8ea8b-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="8ea8b-104">Syntax</span></span>  
  
```cpp  
HRESULT Close();  
```  
  
## <a name="return-value"></a><span data-ttu-id="8ea8b-105">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="8ea8b-105">Return Value</span></span>  
 <span data-ttu-id="8ea8b-106">S_OK, jeśli metoda się powiedzie; w przeciwnym razie E_FAIL lub innego kodu błędu.</span><span class="sxs-lookup"><span data-stu-id="8ea8b-106">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="8ea8b-107">Uwagi</span><span class="sxs-lookup"><span data-stu-id="8ea8b-107">Remarks</span></span>  
 <span data-ttu-id="8ea8b-108">Po tym wywołaniu moduł zapisujący symbol staje się nieprawidłowy dalsze aktualizacje.</span><span class="sxs-lookup"><span data-stu-id="8ea8b-108">After this call, the symbol writer becomes invalid for further updates.</span></span> <span data-ttu-id="8ea8b-109">Aby zamknąć Edytor symboli nie poświęcając symbole, należy użyć [ISymUnmanagedWriter::Abort](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-abort-method.md) metody zamiast tego.</span><span class="sxs-lookup"><span data-stu-id="8ea8b-109">To close the symbol writer without committing the symbols, use the [ISymUnmanagedWriter::Abort](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-abort-method.md) method instead.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8ea8b-110">Wymagania</span><span class="sxs-lookup"><span data-stu-id="8ea8b-110">Requirements</span></span>  
 <span data-ttu-id="8ea8b-111">**Nagłówek:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="8ea8b-111">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8ea8b-112">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="8ea8b-112">See also</span></span>

- [<span data-ttu-id="8ea8b-113">ISymUnmanagedWriter, interfejs</span><span class="sxs-lookup"><span data-stu-id="8ea8b-113">ISymUnmanagedWriter Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-interface.md)
