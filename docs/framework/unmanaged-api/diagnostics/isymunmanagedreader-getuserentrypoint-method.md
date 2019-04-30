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
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61670043"
---
# <a name="isymunmanagedreadergetuserentrypoint-method"></a><span data-ttu-id="97448-102">ISymUnmanagedReader::GetUserEntryPoint — Metoda</span><span class="sxs-lookup"><span data-stu-id="97448-102">ISymUnmanagedReader::GetUserEntryPoint Method</span></span>
<span data-ttu-id="97448-103">Zwraca metodę, która została określona jako punkt wejścia użytkownika dla modułu, jeśli istnieje.</span><span class="sxs-lookup"><span data-stu-id="97448-103">Returns the method that was specified as the user entry point for the module, if any.</span></span> <span data-ttu-id="97448-104">Na przykład ta metoda może być głównej metody użytkownika, a nie wycinków generowanych przez kompilator przed metodą głównego.</span><span class="sxs-lookup"><span data-stu-id="97448-104">For example, this method could be the user's main method rather than compiler-generated stubs before the main method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="97448-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="97448-105">Syntax</span></span>  
  
```  
HRESULT GetUserEntryPoint (  
    [out, retval]  mdMethodDef  *pToken);  
```  
  
## <a name="parameters"></a><span data-ttu-id="97448-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="97448-106">Parameters</span></span>  
 `pToken`  
 <span data-ttu-id="97448-107">[out] Wskaźnik do zmiennej, która odbiera punktu wejścia.</span><span class="sxs-lookup"><span data-stu-id="97448-107">[out] A pointer to a variable that receives the entry point.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="97448-108">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="97448-108">Return Value</span></span>  
 <span data-ttu-id="97448-109">S_OK, jeśli metoda się powiedzie; w przeciwnym razie E_FAIL lub innego kodu błędu.</span><span class="sxs-lookup"><span data-stu-id="97448-109">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="97448-110">Wymagania</span><span class="sxs-lookup"><span data-stu-id="97448-110">Requirements</span></span>  
 <span data-ttu-id="97448-111">**Nagłówek:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="97448-111">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="97448-112">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="97448-112">See also</span></span>

- [<span data-ttu-id="97448-113">ISymUnmanagedReader, interfejs</span><span class="sxs-lookup"><span data-stu-id="97448-113">ISymUnmanagedReader Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-interface.md)
