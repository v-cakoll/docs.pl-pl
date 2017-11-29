---
title: "ISymUnmanagedDocument::GetCheckSumAlgorithmId — Metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ISymUnmanagedDocument.GetCheckSumAlgorithmId
api_location: diasymreader.dll
api_type: COM
f1_keywords: ISymUnmanagedDocument::GetCheckSumAlgorithmId
helpviewer_keywords:
- ISymUnmanagedDocument::GetCheckSumAlgorithmId method [.NET Framework debugging]
- GetCheckSumAlgorithmId method [.NET Framework debugging]
ms.assetid: c7f941cd-e25b-4b85-b1ce-5f77c9208fa9
topic_type: apiref
caps.latest.revision: "7"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 268951d70fec1096fc9cafaeeb6da3b83bc0acf2
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="isymunmanageddocumentgetchecksumalgorithmid-method"></a><span data-ttu-id="43128-102">ISymUnmanagedDocument::GetCheckSumAlgorithmId — Metoda</span><span class="sxs-lookup"><span data-stu-id="43128-102">ISymUnmanagedDocument::GetCheckSumAlgorithmId Method</span></span>
<span data-ttu-id="43128-103">Pobiera identyfikator algorytmu sumy kontrolnej, lub zwraca identyfikator GUID z samych zer, jeśli nie istnieje żadne sumy kontrolnej.</span><span class="sxs-lookup"><span data-stu-id="43128-103">Gets the checksum algorithm identifier, or returns a GUID of all zeros if there is no checksum.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="43128-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="43128-104">Syntax</span></span>  
  
```  
HRESULT GetCheckSumAlgorithmId(  
    [out, retval] GUID*  pRetVal);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="43128-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="43128-105">Parameters</span></span>  
 `pRetVal`  
 <span data-ttu-id="43128-106">[out] Wskaźnik do zmiennej, która odbiera identyfikator algorytmu sumy kontrolnej.</span><span class="sxs-lookup"><span data-stu-id="43128-106">[out] A pointer to a variable that receives the checksum algorithm identifier.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="43128-107">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="43128-107">Return Value</span></span>  
 <span data-ttu-id="43128-108">Wartość S_OK, jeśli metoda zakończy się powodzeniem.</span><span class="sxs-lookup"><span data-stu-id="43128-108">S_OK if the method succeeds.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="43128-109">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="43128-109">See Also</span></span>  
 [<span data-ttu-id="43128-110">ISymUnmanagedDocument — interfejs</span><span class="sxs-lookup"><span data-stu-id="43128-110">ISymUnmanagedDocument Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanageddocument-interface.md)
