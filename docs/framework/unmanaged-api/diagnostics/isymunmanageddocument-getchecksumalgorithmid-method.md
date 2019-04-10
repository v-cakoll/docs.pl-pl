---
title: ISymUnmanagedDocument::GetCheckSumAlgorithmId — Metoda
ms.date: 03/30/2017
api_name:
- ISymUnmanagedDocument.GetCheckSumAlgorithmId
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedDocument::GetCheckSumAlgorithmId
helpviewer_keywords:
- ISymUnmanagedDocument::GetCheckSumAlgorithmId method [.NET Framework debugging]
- GetCheckSumAlgorithmId method [.NET Framework debugging]
ms.assetid: c7f941cd-e25b-4b85-b1ce-5f77c9208fa9
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: f2df98728eec28ffca05b2e246575fc5c882a078
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59229644"
---
# <a name="isymunmanageddocumentgetchecksumalgorithmid-method"></a><span data-ttu-id="939fd-102">ISymUnmanagedDocument::GetCheckSumAlgorithmId — Metoda</span><span class="sxs-lookup"><span data-stu-id="939fd-102">ISymUnmanagedDocument::GetCheckSumAlgorithmId Method</span></span>
<span data-ttu-id="939fd-103">Pobiera identyfikator algorytmu sumy kontrolnej lub zwraca identyfikator GUID same zera, jeśli nie określono żadnych sumy kontrolnej.</span><span class="sxs-lookup"><span data-stu-id="939fd-103">Gets the checksum algorithm identifier, or returns a GUID of all zeros if there is no checksum.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="939fd-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="939fd-104">Syntax</span></span>  
  
```  
HRESULT GetCheckSumAlgorithmId(  
    [out, retval] GUID*  pRetVal);  
```  
  
## <a name="parameters"></a><span data-ttu-id="939fd-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="939fd-105">Parameters</span></span>  
 `pRetVal`  
 <span data-ttu-id="939fd-106">[out] Wskaźnik do zmiennej, która odbiera identyfikator algorytmu sumy kontrolnej.</span><span class="sxs-lookup"><span data-stu-id="939fd-106">[out] A pointer to a variable that receives the checksum algorithm identifier.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="939fd-107">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="939fd-107">Return Value</span></span>  
 <span data-ttu-id="939fd-108">S_OK, jeśli metoda zakończy się powodzeniem.</span><span class="sxs-lookup"><span data-stu-id="939fd-108">S_OK if the method succeeds.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="939fd-109">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="939fd-109">See also</span></span>

- [<span data-ttu-id="939fd-110">ISymUnmanagedDocument — Interfejs</span><span class="sxs-lookup"><span data-stu-id="939fd-110">ISymUnmanagedDocument Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanageddocument-interface.md)
