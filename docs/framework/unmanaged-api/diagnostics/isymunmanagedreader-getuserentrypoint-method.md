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
ms.openlocfilehash: 0267ae8b57c837b097d496c8e119085d03417e36
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59211273"
---
# <a name="isymunmanagedreadergetuserentrypoint-method"></a><span data-ttu-id="db132-102">ISymUnmanagedReader::GetUserEntryPoint — Metoda</span><span class="sxs-lookup"><span data-stu-id="db132-102">ISymUnmanagedReader::GetUserEntryPoint Method</span></span>
<span data-ttu-id="db132-103">Zwraca metodę, która została określona jako punkt wejścia użytkownika dla modułu, jeśli istnieje.</span><span class="sxs-lookup"><span data-stu-id="db132-103">Returns the method that was specified as the user entry point for the module, if any.</span></span> <span data-ttu-id="db132-104">Na przykład ta metoda może być głównej metody użytkownika, a nie wycinków generowanych przez kompilator przed metodą głównego.</span><span class="sxs-lookup"><span data-stu-id="db132-104">For example, this method could be the user's main method rather than compiler-generated stubs before the main method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="db132-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="db132-105">Syntax</span></span>  
  
```  
HRESULT GetUserEntryPoint (  
    [out, retval]  mdMethodDef  *pToken);  
```  
  
## <a name="parameters"></a><span data-ttu-id="db132-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="db132-106">Parameters</span></span>  
 `pToken`  
 <span data-ttu-id="db132-107">[out] Wskaźnik do zmiennej, która odbiera punktu wejścia.</span><span class="sxs-lookup"><span data-stu-id="db132-107">[out] A pointer to a variable that receives the entry point.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="db132-108">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="db132-108">Return Value</span></span>  
 <span data-ttu-id="db132-109">S_OK, jeśli metoda się powiedzie; w przeciwnym razie E_FAIL lub innego kodu błędu.</span><span class="sxs-lookup"><span data-stu-id="db132-109">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="db132-110">Wymagania</span><span class="sxs-lookup"><span data-stu-id="db132-110">Requirements</span></span>  
 <span data-ttu-id="db132-111">**Nagłówek:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="db132-111">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="db132-112">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="db132-112">See also</span></span>

- [<span data-ttu-id="db132-113">ISymUnmanagedReader — Interfejs</span><span class="sxs-lookup"><span data-stu-id="db132-113">ISymUnmanagedReader Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-interface.md)
