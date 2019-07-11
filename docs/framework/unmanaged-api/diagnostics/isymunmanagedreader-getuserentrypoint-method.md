---
title: ISymUnmanagedReader::GetUserEntryPoint — Metoda
ms.date: 03/30/2017
api_name:
- ISymUnmanagedReader.GetUserEntryPoint
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedReader::GetUserEntryPoint
helpviewer_keywords:
- GetUserEntryPoint method [.NET Framework debugging]
- ISymUnmanagedReader::GetUserEntryPoint method [.NET Framework debugging]
ms.assetid: 3fd3a34c-d176-46e9-9996-fb1646cff9b0
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 995c7edf99c917b8bcdc1d51dcc0bf50868e4f35
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/10/2019
ms.locfileid: "67777057"
---
# <a name="isymunmanagedreadergetuserentrypoint-method"></a><span data-ttu-id="cd99b-102">ISymUnmanagedReader::GetUserEntryPoint — Metoda</span><span class="sxs-lookup"><span data-stu-id="cd99b-102">ISymUnmanagedReader::GetUserEntryPoint Method</span></span>
<span data-ttu-id="cd99b-103">Zwraca metodę, która została określona jako punkt wejścia użytkownika dla modułu, jeśli istnieje.</span><span class="sxs-lookup"><span data-stu-id="cd99b-103">Returns the method that was specified as the user entry point for the module, if any.</span></span> <span data-ttu-id="cd99b-104">Na przykład ta metoda może być głównej metody użytkownika, a nie wycinków generowanych przez kompilator przed metodą głównego.</span><span class="sxs-lookup"><span data-stu-id="cd99b-104">For example, this method could be the user's main method rather than compiler-generated stubs before the main method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cd99b-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="cd99b-105">Syntax</span></span>  
  
```cpp  
HRESULT GetUserEntryPoint (  
    [out, retval]  mdMethodDef  *pToken);  
```  
  
## <a name="parameters"></a><span data-ttu-id="cd99b-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="cd99b-106">Parameters</span></span>  
 `pToken`  
 <span data-ttu-id="cd99b-107">[out] Wskaźnik do zmiennej, która odbiera punktu wejścia.</span><span class="sxs-lookup"><span data-stu-id="cd99b-107">[out] A pointer to a variable that receives the entry point.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="cd99b-108">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="cd99b-108">Return Value</span></span>  
 <span data-ttu-id="cd99b-109">S_OK, jeśli metoda się powiedzie; w przeciwnym razie E_FAIL lub innego kodu błędu.</span><span class="sxs-lookup"><span data-stu-id="cd99b-109">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="cd99b-110">Wymagania</span><span class="sxs-lookup"><span data-stu-id="cd99b-110">Requirements</span></span>  
 <span data-ttu-id="cd99b-111">**Nagłówek:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="cd99b-111">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cd99b-112">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="cd99b-112">See also</span></span>

- [<span data-ttu-id="cd99b-113">ISymUnmanagedReader, interfejs</span><span class="sxs-lookup"><span data-stu-id="cd99b-113">ISymUnmanagedReader Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-interface.md)
