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
ms.openlocfilehash: 4331728a4766d81b723c439747e5e1181815394f
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/19/2020
ms.locfileid: "83614672"
---
# <a name="isymunmanagedwriter3commit-method"></a><span data-ttu-id="e1c65-102">ISymUnmanagedWriter3::Commit — Metoda</span><span class="sxs-lookup"><span data-stu-id="e1c65-102">ISymUnmanagedWriter3::Commit Method</span></span>
<span data-ttu-id="e1c65-103">Zatwierdza zmiany zapisywane do strumienia.</span><span class="sxs-lookup"><span data-stu-id="e1c65-103">Commits the changes written so far to the stream.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e1c65-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="e1c65-104">Syntax</span></span>  
  
```cpp  
HRESULT Commit();  
```  
  
## <a name="return-value"></a><span data-ttu-id="e1c65-105">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="e1c65-105">Return Value</span></span>  
 <span data-ttu-id="e1c65-106">S_OK, jeśli metoda się powiedzie; w przeciwnym razie E_FAIL lub inny kod błędu.</span><span class="sxs-lookup"><span data-stu-id="e1c65-106">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e1c65-107">Wymagania</span><span class="sxs-lookup"><span data-stu-id="e1c65-107">Requirements</span></span>  
 <span data-ttu-id="e1c65-108">**Nagłówek:** CorSym. idl, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="e1c65-108">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e1c65-109">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="e1c65-109">See also</span></span>

- [<span data-ttu-id="e1c65-110">ISymUnmanagedWriter3 — Interfejs</span><span class="sxs-lookup"><span data-stu-id="e1c65-110">ISymUnmanagedWriter3 Interface</span></span>](isymunmanagedwriter3-interface.md)
