---
title: ISymUnmanagedReader::GetDocumentVersion — Metoda
ms.date: 03/30/2017
api_name:
- ISymUnmanagedReader.GetDocumentVersion
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedReader::GetDocumentVersion
helpviewer_keywords:
- GetDocumentVersion method [.NET Framework debugging]
- ISymUnmanagedReader::GetDocumentVersion method [.NET Framework debugging]
ms.assetid: a51f1f64-e084-44c5-830c-2222da5a6bbf
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 31b550c7b3cec999b0420fbdc06582a24f420abe
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33425987"
---
# <a name="isymunmanagedreadergetdocumentversion-method"></a><span data-ttu-id="80475-102">ISymUnmanagedReader::GetDocumentVersion — Metoda</span><span class="sxs-lookup"><span data-stu-id="80475-102">ISymUnmanagedReader::GetDocumentVersion Method</span></span>
<span data-ttu-id="80475-103">Pobiera określoną wersję określonego dokumentu.</span><span class="sxs-lookup"><span data-stu-id="80475-103">Gets the specified version of the specified document.</span></span> <span data-ttu-id="80475-104">Wersja dokumentu rozpoczyna się od 1 i jest zwiększany po każdej dokumentu jest aktualizowany przy użyciu [UpdateSymbolStore](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-updatesymbolstore-method.md) metody.</span><span class="sxs-lookup"><span data-stu-id="80475-104">The document version starts at 1 and is incremented each time the document is updated using the [UpdateSymbolStore](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-updatesymbolstore-method.md) method.</span></span> <span data-ttu-id="80475-105">Jeśli `pbCurrent` parametr jest `true`, jest to najnowsza wersja dokumentu.</span><span class="sxs-lookup"><span data-stu-id="80475-105">If the `pbCurrent` parameter is `true`, this is the latest version of the document.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="80475-106">Składnia</span><span class="sxs-lookup"><span data-stu-id="80475-106">Syntax</span></span>  
  
```  
HRESULT GetDocumentVersion (  
    [in]  ISymUnmanagedDocument *pDoc,  
    [out] int* version,  
    [out] BOOL* pbCurrent);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="80475-107">Parametry</span><span class="sxs-lookup"><span data-stu-id="80475-107">Parameters</span></span>  
 `pDoc`  
 <span data-ttu-id="80475-108">[in] Określony dokument.</span><span class="sxs-lookup"><span data-stu-id="80475-108">[in] The specified document.</span></span>  
  
 `version`  
 <span data-ttu-id="80475-109">[out] Wskaźnik do zmiennej, która odbiera wersji określonego dokumentu.</span><span class="sxs-lookup"><span data-stu-id="80475-109">[out] A pointer to a variable that receives the version of the specified document.</span></span>  
  
 `pbCurrent`  
 <span data-ttu-id="80475-110">[out] Wskaźnik do zmiennej, która odbiera `true` , jeśli jest to najnowsza wersja dokumentu lub `false` Jeśli nie jest najnowsza wersja.</span><span class="sxs-lookup"><span data-stu-id="80475-110">[out] A pointer to a variable that receives `true` if this is the latest version of the document, or `false` if it isn't the latest version.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="80475-111">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="80475-111">Return Value</span></span>  
 <span data-ttu-id="80475-112">Wartość S_OK, jeśli metoda zakończy się pomyślnie; w przeciwnym razie E_FAIL lub inny kod błędu.</span><span class="sxs-lookup"><span data-stu-id="80475-112">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="80475-113">Wymagania</span><span class="sxs-lookup"><span data-stu-id="80475-113">Requirements</span></span>  
 <span data-ttu-id="80475-114">**Header:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="80475-114">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="80475-115">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="80475-115">See Also</span></span>  
 [<span data-ttu-id="80475-116">ISymUnmanagedReader, interfejs</span><span class="sxs-lookup"><span data-stu-id="80475-116">ISymUnmanagedReader Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-interface.md)
