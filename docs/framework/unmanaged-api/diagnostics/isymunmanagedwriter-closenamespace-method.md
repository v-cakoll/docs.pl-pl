---
title: "ISymUnmanagedWriter::CloseNamespace — Metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
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
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 364c2a851371ea147a61a49826efe702140c5b2f
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="isymunmanagedwriterclosenamespace-method"></a><span data-ttu-id="6dd0a-102">ISymUnmanagedWriter::CloseNamespace — Metoda</span><span class="sxs-lookup"><span data-stu-id="6dd0a-102">ISymUnmanagedWriter::CloseNamespace Method</span></span>
<span data-ttu-id="6dd0a-103">Zamyka otwarty ostatnio przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="6dd0a-103">Closes the most recently opened namespace.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6dd0a-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="6dd0a-104">Syntax</span></span>  
  
```  
HRESULT CloseNamespace();  
```  
  
## <a name="return-value"></a><span data-ttu-id="6dd0a-105">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="6dd0a-105">Return Value</span></span>  
 <span data-ttu-id="6dd0a-106">Wartość S_OK, jeśli metoda zakończy się pomyślnie; w przeciwnym razie E_FAIL lub inny kod błędu.</span><span class="sxs-lookup"><span data-stu-id="6dd0a-106">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6dd0a-107">Wymagania</span><span class="sxs-lookup"><span data-stu-id="6dd0a-107">Requirements</span></span>  
 <span data-ttu-id="6dd0a-108">**Nagłówek:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="6dd0a-108">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6dd0a-109">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="6dd0a-109">See Also</span></span>  
 [<span data-ttu-id="6dd0a-110">ISymUnmanagedWriter, interfejs</span><span class="sxs-lookup"><span data-stu-id="6dd0a-110">ISymUnmanagedWriter Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-interface.md)  
 [<span data-ttu-id="6dd0a-111">OpenNamespace, metoda</span><span class="sxs-lookup"><span data-stu-id="6dd0a-111">OpenNamespace Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-opennamespace-method.md)
