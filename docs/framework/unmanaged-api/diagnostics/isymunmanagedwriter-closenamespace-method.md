---
title: ISymUnmanagedWriter::CloseNamespace — Metoda
ms.date: 03/30/2017
api_name:
- ISymUnmanagedWriter.CloseNamespace
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedWriter::CloseNamespace
helpviewer_keywords:
- ISymUnmanagedWriter::CloseNamespace method [.NET Framework debugging]
- CloseNamespace method [.NET Framework debugging]
ms.assetid: 7f74d9c5-1377-4958-b842-6306d611cbd5
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 3ed618847d398bb4dcccb8ecebabdc947390c874
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/10/2019
ms.locfileid: "67778177"
---
# <a name="isymunmanagedwriterclosenamespace-method"></a><span data-ttu-id="a09a5-102">ISymUnmanagedWriter::CloseNamespace — Metoda</span><span class="sxs-lookup"><span data-stu-id="a09a5-102">ISymUnmanagedWriter::CloseNamespace Method</span></span>
<span data-ttu-id="a09a5-103">Zamyka otwarty ostatnio przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="a09a5-103">Closes the most recently opened namespace.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a09a5-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="a09a5-104">Syntax</span></span>  
  
```cpp  
HRESULT CloseNamespace();  
```  
  
## <a name="return-value"></a><span data-ttu-id="a09a5-105">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="a09a5-105">Return Value</span></span>  
 <span data-ttu-id="a09a5-106">S_OK, jeśli metoda się powiedzie; w przeciwnym razie E_FAIL lub innego kodu błędu.</span><span class="sxs-lookup"><span data-stu-id="a09a5-106">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a09a5-107">Wymagania</span><span class="sxs-lookup"><span data-stu-id="a09a5-107">Requirements</span></span>  
 <span data-ttu-id="a09a5-108">**Nagłówek:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="a09a5-108">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a09a5-109">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="a09a5-109">See also</span></span>

- [<span data-ttu-id="a09a5-110">ISymUnmanagedWriter, interfejs</span><span class="sxs-lookup"><span data-stu-id="a09a5-110">ISymUnmanagedWriter Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-interface.md)
- [<span data-ttu-id="a09a5-111">OpenNamespace, metoda</span><span class="sxs-lookup"><span data-stu-id="a09a5-111">OpenNamespace Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-opennamespace-method.md)
