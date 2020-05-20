---
title: ISymUnmanagedDocument::HasEmbeddedSource — Metoda
ms.date: 03/30/2017
api_name:
- ISymUnmanagedDocument.HasEmbeddedSource
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedDocument::HasEmbeddedSource
helpviewer_keywords:
- HasEmbeddedSource method [.NET Framework debugging]
- ISymUnmanagedDocument::HasEmbeddedSource method [.NET Framework debugging]
ms.assetid: 385fc4d3-365c-4645-b7b0-6c4c5344b79f
topic_type:
- apiref
ms.openlocfilehash: d654f6d57bd784063fc7f87dd9767bdc27ad2776
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/19/2020
ms.locfileid: "83615582"
---
# <a name="isymunmanageddocumenthasembeddedsource-method"></a><span data-ttu-id="32035-102">ISymUnmanagedDocument::HasEmbeddedSource — Metoda</span><span class="sxs-lookup"><span data-stu-id="32035-102">ISymUnmanagedDocument::HasEmbeddedSource Method</span></span>
<span data-ttu-id="32035-103">Zwraca `true` czy dokument ma osadzone źródło w symbolach debugowania; w przeciwnym razie zwraca `false` .</span><span class="sxs-lookup"><span data-stu-id="32035-103">Returns `true` if the document has source embedded in the debugging symbols; otherwise, returns `false`.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="32035-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="32035-104">Syntax</span></span>  
  
```cpp  
HRESULT HasEmbeddedSource(  
   [out, retval]  BOOL  *pRetVal);  
```  
  
## <a name="parameters"></a><span data-ttu-id="32035-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="32035-105">Parameters</span></span>  
 `pRetVal`  
 <span data-ttu-id="32035-106">określoną Wskaźnik do zmiennej, która wskazuje, czy dokument ma osadzone źródło w symbolach debugowania.</span><span class="sxs-lookup"><span data-stu-id="32035-106">[out] A pointer to a variable that indicates whether the document has source embedded in the debugging symbols.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="32035-107">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="32035-107">Return Value</span></span>  
 <span data-ttu-id="32035-108">S_OK, jeśli metoda zakończy się pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="32035-108">S_OK if the method succeeds.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="32035-109">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="32035-109">See also</span></span>

- [<span data-ttu-id="32035-110">ISymUnmanagedDocument, interfejs</span><span class="sxs-lookup"><span data-stu-id="32035-110">ISymUnmanagedDocument Interface</span></span>](isymunmanageddocument-interface.md)
