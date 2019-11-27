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
ms.openlocfilehash: 2bc673d2e331cd32d5317cb20f9418eb3a3b144a
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/23/2019
ms.locfileid: "74431069"
---
# <a name="isymunmanageddocumentgetchecksumalgorithmid-method"></a><span data-ttu-id="72c8f-102">ISymUnmanagedDocument::GetCheckSumAlgorithmId — Metoda</span><span class="sxs-lookup"><span data-stu-id="72c8f-102">ISymUnmanagedDocument::GetCheckSumAlgorithmId Method</span></span>
<span data-ttu-id="72c8f-103">Pobiera identyfikator algorytmu sum kontrolnych lub zwraca identyfikator GUID wszystkich zer, jeśli nie ma sumy kontrolnej.</span><span class="sxs-lookup"><span data-stu-id="72c8f-103">Gets the checksum algorithm identifier, or returns a GUID of all zeros if there is no checksum.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="72c8f-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="72c8f-104">Syntax</span></span>  
  
```cpp  
HRESULT GetCheckSumAlgorithmId(  
    [out, retval] GUID*  pRetVal);  
```  
  
## <a name="parameters"></a><span data-ttu-id="72c8f-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="72c8f-105">Parameters</span></span>  
 `pRetVal`  
 <span data-ttu-id="72c8f-106">określoną Wskaźnik do zmiennej, która otrzymuje identyfikator algorytmu sum kontrolnych.</span><span class="sxs-lookup"><span data-stu-id="72c8f-106">[out] A pointer to a variable that receives the checksum algorithm identifier.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="72c8f-107">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="72c8f-107">Return Value</span></span>  
 <span data-ttu-id="72c8f-108">S_OK, jeśli metoda zakończy się pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="72c8f-108">S_OK if the method succeeds.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="72c8f-109">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="72c8f-109">See also</span></span>

- [<span data-ttu-id="72c8f-110">ISymUnmanagedDocument, interfejs</span><span class="sxs-lookup"><span data-stu-id="72c8f-110">ISymUnmanagedDocument Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanageddocument-interface.md)
