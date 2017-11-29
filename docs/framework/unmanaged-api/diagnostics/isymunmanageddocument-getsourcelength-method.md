---
title: "ISymUnmanagedDocument::GetSourceLength — Metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ISymUnmanagedDocument.GetSourceLength
api_location: diasymreader.dll
api_type: COM
f1_keywords: ISymUnmanagedDocument::GetSourceLength
helpviewer_keywords:
- GetSourceLength method [.NET Framework debugging]
- ISymUnmanagedDocument::GetSourceLength method [.NET Framework debugging]
ms.assetid: e087dbbb-f4fb-4fbe-8292-e4f1a14d0df2
topic_type: apiref
caps.latest.revision: "7"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: b4bf318303b1d787df100051a5c2d3fdd0ac5918
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="isymunmanageddocumentgetsourcelength-method"></a><span data-ttu-id="dc90d-102">ISymUnmanagedDocument::GetSourceLength — Metoda</span><span class="sxs-lookup"><span data-stu-id="dc90d-102">ISymUnmanagedDocument::GetSourceLength Method</span></span>
<span data-ttu-id="dc90d-103">Pobiera długość w bajtach osadzonego źródła.</span><span class="sxs-lookup"><span data-stu-id="dc90d-103">Gets the length, in bytes, of the embedded source.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="dc90d-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="dc90d-104">Syntax</span></span>  
  
```  
HRESULT GetSourceLength(  
    [out, retval]  ULONG32*  pRetVal);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="dc90d-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="dc90d-105">Parameters</span></span>  
 `pRetVal`  
 <span data-ttu-id="dc90d-106">[out] Wskaźnik do zmiennej, która wskazuje długość w bajtach osadzone źródło.</span><span class="sxs-lookup"><span data-stu-id="dc90d-106">[out] A pointer to a variable that indicates the length, in bytes, of the embedded source.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="dc90d-107">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="dc90d-107">Return Value</span></span>  
 <span data-ttu-id="dc90d-108">Wartość S_OK, jeśli metoda zakończy się powodzeniem.</span><span class="sxs-lookup"><span data-stu-id="dc90d-108">S_OK if the method succeeds.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dc90d-109">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="dc90d-109">See Also</span></span>  
 [<span data-ttu-id="dc90d-110">ISymUnmanagedDocument — interfejs</span><span class="sxs-lookup"><span data-stu-id="dc90d-110">ISymUnmanagedDocument Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanageddocument-interface.md)
