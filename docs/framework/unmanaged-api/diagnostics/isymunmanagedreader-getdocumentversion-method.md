---
title: "ISymUnmanagedReader::GetDocumentVersion — Metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ISymUnmanagedReader.GetDocumentVersion
api_location: diasymreader.dll
api_type: COM
f1_keywords: ISymUnmanagedReader::GetDocumentVersion
helpviewer_keywords:
- GetDocumentVersion method [.NET Framework debugging]
- ISymUnmanagedReader::GetDocumentVersion method [.NET Framework debugging]
ms.assetid: a51f1f64-e084-44c5-830c-2222da5a6bbf
topic_type: apiref
caps.latest.revision: "9"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 377457fa852e1a4ae140f72d2dd83731490b81d9
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="isymunmanagedreadergetdocumentversion-method"></a><span data-ttu-id="9da50-102">ISymUnmanagedReader::GetDocumentVersion — Metoda</span><span class="sxs-lookup"><span data-stu-id="9da50-102">ISymUnmanagedReader::GetDocumentVersion Method</span></span>
<span data-ttu-id="9da50-103">Pobiera określoną wersję określonego dokumentu.</span><span class="sxs-lookup"><span data-stu-id="9da50-103">Gets the specified version of the specified document.</span></span> <span data-ttu-id="9da50-104">Wersja dokumentu rozpoczyna się od 1 i jest zwiększany po każdej dokumentu jest aktualizowany przy użyciu [UpdateSymbolStore](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-updatesymbolstore-method.md) metody.</span><span class="sxs-lookup"><span data-stu-id="9da50-104">The document version starts at 1 and is incremented each time the document is updated using the [UpdateSymbolStore](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-updatesymbolstore-method.md) method.</span></span> <span data-ttu-id="9da50-105">Jeśli `pbCurrent` parametr jest `true`, jest to najnowsza wersja dokumentu.</span><span class="sxs-lookup"><span data-stu-id="9da50-105">If the `pbCurrent` parameter is `true`, this is the latest version of the document.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9da50-106">Składnia</span><span class="sxs-lookup"><span data-stu-id="9da50-106">Syntax</span></span>  
  
```  
HRESULT GetDocumentVersion (  
    [in]  ISymUnmanagedDocument *pDoc,  
    [out] int* version,  
    [out] BOOL* pbCurrent);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="9da50-107">Parametry</span><span class="sxs-lookup"><span data-stu-id="9da50-107">Parameters</span></span>  
 `pDoc`  
 <span data-ttu-id="9da50-108">[in] Określony dokument.</span><span class="sxs-lookup"><span data-stu-id="9da50-108">[in] The specified document.</span></span>  
  
 `version`  
 <span data-ttu-id="9da50-109">[out] Wskaźnik do zmiennej, która odbiera wersji określonego dokumentu.</span><span class="sxs-lookup"><span data-stu-id="9da50-109">[out] A pointer to a variable that receives the version of the specified document.</span></span>  
  
 `pbCurrent`  
 <span data-ttu-id="9da50-110">[out] Wskaźnik do zmiennej, która odbiera `true` , jeśli jest to najnowsza wersja dokumentu lub `false` Jeśli nie jest najnowsza wersja.</span><span class="sxs-lookup"><span data-stu-id="9da50-110">[out] A pointer to a variable that receives `true` if this is the latest version of the document, or `false` if it isn't the latest version.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="9da50-111">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="9da50-111">Return Value</span></span>  
 <span data-ttu-id="9da50-112">Wartość S_OK, jeśli metoda zakończy się pomyślnie; w przeciwnym razie E_FAIL lub inny kod błędu.</span><span class="sxs-lookup"><span data-stu-id="9da50-112">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9da50-113">Wymagania</span><span class="sxs-lookup"><span data-stu-id="9da50-113">Requirements</span></span>  
 <span data-ttu-id="9da50-114">**Nagłówek:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="9da50-114">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9da50-115">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="9da50-115">See Also</span></span>  
 [<span data-ttu-id="9da50-116">ISymUnmanagedReader — interfejs</span><span class="sxs-lookup"><span data-stu-id="9da50-116">ISymUnmanagedReader Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-interface.md)
