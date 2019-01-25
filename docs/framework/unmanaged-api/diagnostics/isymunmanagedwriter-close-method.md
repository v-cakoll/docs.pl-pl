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
ms.openlocfilehash: 780c19acd3d6980c0fb3e31d01e569a61fd04d6d
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54647312"
---
# <a name="isymunmanagedwriterclose-method"></a><span data-ttu-id="1afd5-102">ISymUnmanagedWriter::Close — Metoda</span><span class="sxs-lookup"><span data-stu-id="1afd5-102">ISymUnmanagedWriter::Close Method</span></span>
<span data-ttu-id="1afd5-103">Zamyka moduł zapisujący symbol po zatwierdzeniu symbole do magazynu symboli.</span><span class="sxs-lookup"><span data-stu-id="1afd5-103">Closes the symbol writer after committing the symbols to the symbol store.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1afd5-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="1afd5-104">Syntax</span></span>  
  
```  
HRESULT Close();  
```  
  
## <a name="return-value"></a><span data-ttu-id="1afd5-105">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="1afd5-105">Return Value</span></span>  
 <span data-ttu-id="1afd5-106">S_OK, jeśli metoda się powiedzie; w przeciwnym razie E_FAIL lub innego kodu błędu.</span><span class="sxs-lookup"><span data-stu-id="1afd5-106">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="1afd5-107">Uwagi</span><span class="sxs-lookup"><span data-stu-id="1afd5-107">Remarks</span></span>  
 <span data-ttu-id="1afd5-108">Po tym wywołaniu moduł zapisujący symbol staje się nieprawidłowy dalsze aktualizacje.</span><span class="sxs-lookup"><span data-stu-id="1afd5-108">After this call, the symbol writer becomes invalid for further updates.</span></span> <span data-ttu-id="1afd5-109">Aby zamknąć Edytor symboli nie poświęcając symbole, należy użyć [ISymUnmanagedWriter::Abort](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-abort-method.md) metody zamiast tego.</span><span class="sxs-lookup"><span data-stu-id="1afd5-109">To close the symbol writer without committing the symbols, use the [ISymUnmanagedWriter::Abort](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-abort-method.md) method instead.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1afd5-110">Wymagania</span><span class="sxs-lookup"><span data-stu-id="1afd5-110">Requirements</span></span>  
 <span data-ttu-id="1afd5-111">**Nagłówek:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="1afd5-111">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1afd5-112">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="1afd5-112">See also</span></span>
- [<span data-ttu-id="1afd5-113">ISymUnmanagedWriter, interfejs</span><span class="sxs-lookup"><span data-stu-id="1afd5-113">ISymUnmanagedWriter Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-interface.md)
