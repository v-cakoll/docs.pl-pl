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
ms.openlocfilehash: cf6a08b17819e3d3cdaa62b0e209fc2064de4a4a
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54688704"
---
# <a name="isymunmanagedreadergetdocumentversion-method"></a><span data-ttu-id="ebb2a-102">ISymUnmanagedReader::GetDocumentVersion — Metoda</span><span class="sxs-lookup"><span data-stu-id="ebb2a-102">ISymUnmanagedReader::GetDocumentVersion Method</span></span>
<span data-ttu-id="ebb2a-103">Pobiera określoną wersję określonego dokumentu.</span><span class="sxs-lookup"><span data-stu-id="ebb2a-103">Gets the specified version of the specified document.</span></span> <span data-ttu-id="ebb2a-104">Wersja dokumentu rozpoczyna się od 1 i jest zwiększana za każdym razem, dokument jest aktualizowany za pomocą [updatesymbolstore —](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-updatesymbolstore-method.md) metody.</span><span class="sxs-lookup"><span data-stu-id="ebb2a-104">The document version starts at 1 and is incremented each time the document is updated using the [UpdateSymbolStore](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-updatesymbolstore-method.md) method.</span></span> <span data-ttu-id="ebb2a-105">Jeśli `pbCurrent` parametr jest `true`, to jest najnowsza wersja dokumentu.</span><span class="sxs-lookup"><span data-stu-id="ebb2a-105">If the `pbCurrent` parameter is `true`, this is the latest version of the document.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ebb2a-106">Składnia</span><span class="sxs-lookup"><span data-stu-id="ebb2a-106">Syntax</span></span>  
  
```  
HRESULT GetDocumentVersion (  
    [in]  ISymUnmanagedDocument *pDoc,  
    [out] int* version,  
    [out] BOOL* pbCurrent);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="ebb2a-107">Parametry</span><span class="sxs-lookup"><span data-stu-id="ebb2a-107">Parameters</span></span>  
 `pDoc`  
 <span data-ttu-id="ebb2a-108">[in] Określony dokument.</span><span class="sxs-lookup"><span data-stu-id="ebb2a-108">[in] The specified document.</span></span>  
  
 `version`  
 <span data-ttu-id="ebb2a-109">[out] Wskaźnik do zmiennej, która odbiera wersję określonego dokumentu.</span><span class="sxs-lookup"><span data-stu-id="ebb2a-109">[out] A pointer to a variable that receives the version of the specified document.</span></span>  
  
 `pbCurrent`  
 <span data-ttu-id="ebb2a-110">[out] Wskaźnik do zmiennej, która odbiera `true` Jeśli to jest najnowsza wersja dokumentu, lub `false` Jeśli nie jest najnowsza wersja.</span><span class="sxs-lookup"><span data-stu-id="ebb2a-110">[out] A pointer to a variable that receives `true` if this is the latest version of the document, or `false` if it isn't the latest version.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="ebb2a-111">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="ebb2a-111">Return Value</span></span>  
 <span data-ttu-id="ebb2a-112">S_OK, jeśli metoda się powiedzie; w przeciwnym razie E_FAIL lub innego kodu błędu.</span><span class="sxs-lookup"><span data-stu-id="ebb2a-112">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ebb2a-113">Wymagania</span><span class="sxs-lookup"><span data-stu-id="ebb2a-113">Requirements</span></span>  
 <span data-ttu-id="ebb2a-114">**Nagłówek:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="ebb2a-114">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ebb2a-115">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="ebb2a-115">See also</span></span>
- [<span data-ttu-id="ebb2a-116">ISymUnmanagedReader, interfejs</span><span class="sxs-lookup"><span data-stu-id="ebb2a-116">ISymUnmanagedReader Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-interface.md)
