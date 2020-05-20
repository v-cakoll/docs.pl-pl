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
ms.openlocfilehash: a76435be591d9f73d5975c5315f6e744f8972fc7
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/19/2020
ms.locfileid: "83614620"
---
# <a name="isymunmanageddocumentgetchecksumalgorithmid-method"></a><span data-ttu-id="821c6-102">ISymUnmanagedDocument::GetCheckSumAlgorithmId — Metoda</span><span class="sxs-lookup"><span data-stu-id="821c6-102">ISymUnmanagedDocument::GetCheckSumAlgorithmId Method</span></span>
<span data-ttu-id="821c6-103">Pobiera identyfikator algorytmu sum kontrolnych lub zwraca identyfikator GUID wszystkich zer, jeśli nie ma sumy kontrolnej.</span><span class="sxs-lookup"><span data-stu-id="821c6-103">Gets the checksum algorithm identifier, or returns a GUID of all zeros if there is no checksum.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="821c6-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="821c6-104">Syntax</span></span>  
  
```cpp  
HRESULT GetCheckSumAlgorithmId(  
    [out, retval] GUID*  pRetVal);  
```  
  
## <a name="parameters"></a><span data-ttu-id="821c6-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="821c6-105">Parameters</span></span>  
 `pRetVal`  
 <span data-ttu-id="821c6-106">określoną Wskaźnik do zmiennej, która otrzymuje identyfikator algorytmu sum kontrolnych.</span><span class="sxs-lookup"><span data-stu-id="821c6-106">[out] A pointer to a variable that receives the checksum algorithm identifier.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="821c6-107">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="821c6-107">Return Value</span></span>  
 <span data-ttu-id="821c6-108">S_OK, jeśli metoda zakończy się pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="821c6-108">S_OK if the method succeeds.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="821c6-109">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="821c6-109">See also</span></span>

- [<span data-ttu-id="821c6-110">ISymUnmanagedDocument, interfejs</span><span class="sxs-lookup"><span data-stu-id="821c6-110">ISymUnmanagedDocument Interface</span></span>](isymunmanageddocument-interface.md)
