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
ms.openlocfilehash: 7b4c334d82320066bf9459907660fe6b7e2acefd
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="isymunmanagedreadergetuserentrypoint-method"></a><span data-ttu-id="4667c-102">ISymUnmanagedReader::GetUserEntryPoint — Metoda</span><span class="sxs-lookup"><span data-stu-id="4667c-102">ISymUnmanagedReader::GetUserEntryPoint Method</span></span>
<span data-ttu-id="4667c-103">Zwraca metodę, która została określona jako punktu wejścia użytkownika dla modułu, jeśli istnieje.</span><span class="sxs-lookup"><span data-stu-id="4667c-103">Returns the method that was specified as the user entry point for the module, if any.</span></span> <span data-ttu-id="4667c-104">Tej metody można na przykład metoda główna użytkownika, a nie generowane przez kompilator klas zastępczych przed wywołaniem metody głównej.</span><span class="sxs-lookup"><span data-stu-id="4667c-104">For example, this method could be the user's main method rather than compiler-generated stubs before the main method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4667c-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="4667c-105">Syntax</span></span>  
  
```  
HRESULT GetUserEntryPoint (  
    [out, retval]  mdMethodDef  *pToken);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="4667c-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="4667c-106">Parameters</span></span>  
 `pToken`  
 <span data-ttu-id="4667c-107">[out] Wskaźnik do zmiennej, która odbiera punktu wejścia.</span><span class="sxs-lookup"><span data-stu-id="4667c-107">[out] A pointer to a variable that receives the entry point.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="4667c-108">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="4667c-108">Return Value</span></span>  
 <span data-ttu-id="4667c-109">Wartość S_OK, jeśli metoda zakończy się pomyślnie; w przeciwnym razie E_FAIL lub inny kod błędu.</span><span class="sxs-lookup"><span data-stu-id="4667c-109">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4667c-110">Wymagania</span><span class="sxs-lookup"><span data-stu-id="4667c-110">Requirements</span></span>  
 <span data-ttu-id="4667c-111">**Header:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="4667c-111">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4667c-112">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="4667c-112">See Also</span></span>  
 [<span data-ttu-id="4667c-113">ISymUnmanagedReader, interfejs</span><span class="sxs-lookup"><span data-stu-id="4667c-113">ISymUnmanagedReader Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-interface.md)
