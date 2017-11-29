---
title: "ISymUnmanagedReader::GetUserEntryPoint — Metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ISymUnmanagedReader.GetUserEntryPoint
api_location: diasymreader.dll
api_type: COM
f1_keywords: ISymUnmanagedReader::GetUserEntryPoint
helpviewer_keywords:
- GetUserEntryPoint method [.NET Framework debugging]
- ISymUnmanagedReader::GetUserEntryPoint method [.NET Framework debugging]
ms.assetid: 3fd3a34c-d176-46e9-9996-fb1646cff9b0
topic_type: apiref
caps.latest.revision: "7"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 08a89ba20b48c3d7faa3f3d27d4c57c55b33c355
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="isymunmanagedreadergetuserentrypoint-method"></a><span data-ttu-id="4f0ba-102">ISymUnmanagedReader::GetUserEntryPoint — Metoda</span><span class="sxs-lookup"><span data-stu-id="4f0ba-102">ISymUnmanagedReader::GetUserEntryPoint Method</span></span>
<span data-ttu-id="4f0ba-103">Zwraca metodę, która została określona jako punktu wejścia użytkownika dla modułu, jeśli istnieje.</span><span class="sxs-lookup"><span data-stu-id="4f0ba-103">Returns the method that was specified as the user entry point for the module, if any.</span></span> <span data-ttu-id="4f0ba-104">Tej metody można na przykład metoda główna użytkownika, a nie generowane przez kompilator klas zastępczych przed wywołaniem metody głównej.</span><span class="sxs-lookup"><span data-stu-id="4f0ba-104">For example, this method could be the user's main method rather than compiler-generated stubs before the main method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4f0ba-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="4f0ba-105">Syntax</span></span>  
  
```  
HRESULT GetUserEntryPoint (  
    [out, retval]  mdMethodDef  *pToken);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="4f0ba-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="4f0ba-106">Parameters</span></span>  
 `pToken`  
 <span data-ttu-id="4f0ba-107">[out] Wskaźnik do zmiennej, która odbiera punktu wejścia.</span><span class="sxs-lookup"><span data-stu-id="4f0ba-107">[out] A pointer to a variable that receives the entry point.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="4f0ba-108">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="4f0ba-108">Return Value</span></span>  
 <span data-ttu-id="4f0ba-109">Wartość S_OK, jeśli metoda zakończy się pomyślnie; w przeciwnym razie E_FAIL lub inny kod błędu.</span><span class="sxs-lookup"><span data-stu-id="4f0ba-109">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4f0ba-110">Wymagania</span><span class="sxs-lookup"><span data-stu-id="4f0ba-110">Requirements</span></span>  
 <span data-ttu-id="4f0ba-111">**Nagłówek:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="4f0ba-111">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4f0ba-112">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="4f0ba-112">See Also</span></span>  
 [<span data-ttu-id="4f0ba-113">ISymUnmanagedReader — interfejs</span><span class="sxs-lookup"><span data-stu-id="4f0ba-113">ISymUnmanagedReader Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-interface.md)
