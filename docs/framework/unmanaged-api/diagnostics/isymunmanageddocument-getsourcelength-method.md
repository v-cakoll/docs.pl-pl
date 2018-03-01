---
title: "ISymUnmanagedDocument::GetSourceLength — Metoda"
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
- ISymUnmanagedDocument.GetSourceLength
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedDocument::GetSourceLength
helpviewer_keywords:
- GetSourceLength method [.NET Framework debugging]
- ISymUnmanagedDocument::GetSourceLength method [.NET Framework debugging]
ms.assetid: e087dbbb-f4fb-4fbe-8292-e4f1a14d0df2
topic_type:
- apiref
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 61d9bd99a08f428993f38fb5b6889c9659607782
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="isymunmanageddocumentgetsourcelength-method"></a><span data-ttu-id="742b9-102">ISymUnmanagedDocument::GetSourceLength — Metoda</span><span class="sxs-lookup"><span data-stu-id="742b9-102">ISymUnmanagedDocument::GetSourceLength Method</span></span>
<span data-ttu-id="742b9-103">Pobiera długość w bajtach osadzonego źródła.</span><span class="sxs-lookup"><span data-stu-id="742b9-103">Gets the length, in bytes, of the embedded source.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="742b9-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="742b9-104">Syntax</span></span>  
  
```  
HRESULT GetSourceLength(  
    [out, retval]  ULONG32*  pRetVal);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="742b9-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="742b9-105">Parameters</span></span>  
 `pRetVal`  
 <span data-ttu-id="742b9-106">[out] Wskaźnik do zmiennej, która wskazuje długość w bajtach osadzone źródło.</span><span class="sxs-lookup"><span data-stu-id="742b9-106">[out] A pointer to a variable that indicates the length, in bytes, of the embedded source.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="742b9-107">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="742b9-107">Return Value</span></span>  
 <span data-ttu-id="742b9-108">Wartość S_OK, jeśli metoda zakończy się powodzeniem.</span><span class="sxs-lookup"><span data-stu-id="742b9-108">S_OK if the method succeeds.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="742b9-109">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="742b9-109">See Also</span></span>  
 [<span data-ttu-id="742b9-110">ISymUnmanagedDocument, interfejs</span><span class="sxs-lookup"><span data-stu-id="742b9-110">ISymUnmanagedDocument Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanageddocument-interface.md)
