---
title: ISymUnmanagedWriter3::Commit — Metoda
ms.date: 03/30/2017
api_name:
- ISymUnmanagedWriter3.Commit
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedWriter3::Commit
helpviewer_keywords:
- Commit method, ISymUnmanagedWriter3 interface [.NET Framework debugging]
- ISymUnmanagedWriter3::Commit method [.NET Framework debugging]
ms.assetid: f6961922-46ec-4d2c-8369-85f880731f37
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 9e4e2cd49bdffd0a1293a5601cb44e4804e2b1ed
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="isymunmanagedwriter3commit-method"></a><span data-ttu-id="a3f81-102">ISymUnmanagedWriter3::Commit — Metoda</span><span class="sxs-lookup"><span data-stu-id="a3f81-102">ISymUnmanagedWriter3::Commit Method</span></span>
<span data-ttu-id="a3f81-103">Zatwierdza zmiany do tej pory zapisywane do strumienia.</span><span class="sxs-lookup"><span data-stu-id="a3f81-103">Commits the changes written so far to the stream.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a3f81-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="a3f81-104">Syntax</span></span>  
  
```  
HRESULT Commit();  
```  
  
## <a name="return-value"></a><span data-ttu-id="a3f81-105">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="a3f81-105">Return Value</span></span>  
 <span data-ttu-id="a3f81-106">Wartość S_OK, jeśli metoda zakończy się pomyślnie; w przeciwnym razie E_FAIL lub inny kod błędu.</span><span class="sxs-lookup"><span data-stu-id="a3f81-106">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a3f81-107">Wymagania</span><span class="sxs-lookup"><span data-stu-id="a3f81-107">Requirements</span></span>  
 <span data-ttu-id="a3f81-108">**Nagłówek:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="a3f81-108">**Header:** CorSym.idl , CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a3f81-109">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="a3f81-109">See Also</span></span>  
 [<span data-ttu-id="a3f81-110">ISymUnmanagedWriter3, interfejs</span><span class="sxs-lookup"><span data-stu-id="a3f81-110">ISymUnmanagedWriter3 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter3-interface.md)
