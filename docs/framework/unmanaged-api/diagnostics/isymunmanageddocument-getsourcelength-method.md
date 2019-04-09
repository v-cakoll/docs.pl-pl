---
title: ISymUnmanagedDocument::GetSourceLength — Metoda
ms.date: 03/30/2017
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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 2717a279abf7fb1b704a769d54654d97949cc0a2
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59136906"
---
# <a name="isymunmanageddocumentgetsourcelength-method"></a><span data-ttu-id="f6c62-102">ISymUnmanagedDocument::GetSourceLength — Metoda</span><span class="sxs-lookup"><span data-stu-id="f6c62-102">ISymUnmanagedDocument::GetSourceLength Method</span></span>
<span data-ttu-id="f6c62-103">Pobiera długość w bajtach osadzonego źródła.</span><span class="sxs-lookup"><span data-stu-id="f6c62-103">Gets the length, in bytes, of the embedded source.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f6c62-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="f6c62-104">Syntax</span></span>  
  
```  
HRESULT GetSourceLength(  
    [out, retval]  ULONG32*  pRetVal);  
```  
  
## <a name="parameters"></a><span data-ttu-id="f6c62-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="f6c62-105">Parameters</span></span>  
 `pRetVal`  
 <span data-ttu-id="f6c62-106">[out] Wskaźnik do zmiennej, która wskazuje długość w bajtach, osadzonego źródła.</span><span class="sxs-lookup"><span data-stu-id="f6c62-106">[out] A pointer to a variable that indicates the length, in bytes, of the embedded source.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="f6c62-107">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="f6c62-107">Return Value</span></span>  
 <span data-ttu-id="f6c62-108">S_OK, jeśli metoda zakończy się powodzeniem.</span><span class="sxs-lookup"><span data-stu-id="f6c62-108">S_OK if the method succeeds.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f6c62-109">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="f6c62-109">See also</span></span>

- [<span data-ttu-id="f6c62-110">ISymUnmanagedDocument — Interfejs</span><span class="sxs-lookup"><span data-stu-id="f6c62-110">ISymUnmanagedDocument Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanageddocument-interface.md)
