---
title: ISymUnmanagedDispose::Destroy — Metoda
ms.date: 03/30/2017
api_name:
- ISymUnmanagedDispose.Destroy
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedDispose::Destroy
helpviewer_keywords:
- ISymUnmanagedDispose::Destroy method [.NET Framework debugging]
- Destroy method [.NET Framework debugging]
ms.assetid: a854ab9f-d2ba-470e-867f-808c1e7bd07a
topic_type:
- apiref
ms.openlocfilehash: 5bd94cb851d4bb044d4ce03b97d6342a2c9652e4
ms.sourcegitcommit: 7b1497c1927cb449cefd313bc5126ae37df30746
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/16/2020
ms.locfileid: "83441321"
---
# <a name="isymunmanageddisposedestroy-method"></a><span data-ttu-id="94c00-102">ISymUnmanagedDispose::Destroy — Metoda</span><span class="sxs-lookup"><span data-stu-id="94c00-102">ISymUnmanagedDispose::Destroy Method</span></span>
<span data-ttu-id="94c00-103">Powoduje, że obiekt źródłowy zwolni wszystkie odwołania wewnętrzne i zwróci niepowodzenie dla każdego kolejnego wywołania metody.</span><span class="sxs-lookup"><span data-stu-id="94c00-103">Causes the underlying object to release all internal references and return failure on any subsequent method calls.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="94c00-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="94c00-104">Syntax</span></span>  
  
```cpp  
HRESULT Destroy();  
```  
  
## <a name="return-value"></a><span data-ttu-id="94c00-105">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="94c00-105">Return Value</span></span>  
 <span data-ttu-id="94c00-106">S_OK, jeśli metoda się powiedzie; w przeciwnym razie E_FAIL lub inny kod błędu.</span><span class="sxs-lookup"><span data-stu-id="94c00-106">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="94c00-107">Wymagania</span><span class="sxs-lookup"><span data-stu-id="94c00-107">Requirements</span></span>  
 <span data-ttu-id="94c00-108">**Nagłówek:** CorSym. idl, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="94c00-108">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="94c00-109">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="94c00-109">See also</span></span>

- [<span data-ttu-id="94c00-110">ISymUnmanagedDispose — Interfejs</span><span class="sxs-lookup"><span data-stu-id="94c00-110">ISymUnmanagedDispose Interface</span></span>](isymunmanageddispose-interface.md)
