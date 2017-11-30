---
title: "ISymUnmanagedWriter3::Commit — Metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ISymUnmanagedWriter3.Commit
api_location: diasymreader.dll
api_type: COM
f1_keywords: ISymUnmanagedWriter3::Commit
helpviewer_keywords:
- Commit method, ISymUnmanagedWriter3 interface [.NET Framework debugging]
- ISymUnmanagedWriter3::Commit method [.NET Framework debugging]
ms.assetid: f6961922-46ec-4d2c-8369-85f880731f37
topic_type: apiref
caps.latest.revision: "7"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 3ff2baa8a5006e2a3a83ddbcf5ca79b78350794b
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="isymunmanagedwriter3commit-method"></a><span data-ttu-id="05be4-102">ISymUnmanagedWriter3::Commit — Metoda</span><span class="sxs-lookup"><span data-stu-id="05be4-102">ISymUnmanagedWriter3::Commit Method</span></span>
<span data-ttu-id="05be4-103">Zatwierdza zmiany do tej pory zapisywane do strumienia.</span><span class="sxs-lookup"><span data-stu-id="05be4-103">Commits the changes written so far to the stream.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="05be4-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="05be4-104">Syntax</span></span>  
  
```  
HRESULT Commit();  
```  
  
## <a name="return-value"></a><span data-ttu-id="05be4-105">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="05be4-105">Return Value</span></span>  
 <span data-ttu-id="05be4-106">Wartość S_OK, jeśli metoda zakończy się pomyślnie; w przeciwnym razie E_FAIL lub inny kod błędu.</span><span class="sxs-lookup"><span data-stu-id="05be4-106">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="05be4-107">Wymagania</span><span class="sxs-lookup"><span data-stu-id="05be4-107">Requirements</span></span>  
 <span data-ttu-id="05be4-108">**Nagłówek:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="05be4-108">**Header:** CorSym.idl , CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="05be4-109">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="05be4-109">See Also</span></span>  
 [<span data-ttu-id="05be4-110">ISymUnmanagedWriter3 — interfejs</span><span class="sxs-lookup"><span data-stu-id="05be4-110">ISymUnmanagedWriter3 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter3-interface.md)
