---
title: "ISymUnmanagedReader::GetMethodFromDocumentPosition — Metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ISymUnmanagedReader.GetMethodFromDocumentPosition
api_location: diasymreader.dll
api_type: COM
f1_keywords: ISymUnmanagedReader::GetMethodFromDocumentPosition
helpviewer_keywords:
- GetMethodFromDocumentPosition method [.NET Framework debugging]
- ISymUnmanagedReader::GetMethodFromDocumentPosition method [.NET Framework debugging]
ms.assetid: 55773dbc-9053-46e3-8a3c-86caa9d91fb4
topic_type: apiref
caps.latest.revision: "9"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 4fa9bfa324254a48d43c4c3df5ecebb91b3f0ae1
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="isymunmanagedreadergetmethodfromdocumentposition-method"></a><span data-ttu-id="1f9cf-102">ISymUnmanagedReader::GetMethodFromDocumentPosition — Metoda</span><span class="sxs-lookup"><span data-stu-id="1f9cf-102">ISymUnmanagedReader::GetMethodFromDocumentPosition Method</span></span>
<span data-ttu-id="1f9cf-103">Zwraca metodę, która zawiera punkt przerwania w danej pozycji w dokumencie.</span><span class="sxs-lookup"><span data-stu-id="1f9cf-103">Returns the method that contains the breakpoint at the given position in a document.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1f9cf-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="1f9cf-104">Syntax</span></span>  
  
```  
HRESULT GetMethodFromDocumentPosition (  
    [in]  ISymUnmanagedDocument*  document,  
    [in]  ULONG32  line,  
    [in]  ULONG32  column,  
    [out, retval] ISymUnmanagedMethod**  pRetVal);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="1f9cf-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="1f9cf-105">Parameters</span></span>  
 `document`  
 <span data-ttu-id="1f9cf-106">[in] Określony dokument.</span><span class="sxs-lookup"><span data-stu-id="1f9cf-106">[in] The specified document.</span></span>  
  
 `line`  
 <span data-ttu-id="1f9cf-107">[in] Wiersz określonego dokumentu.</span><span class="sxs-lookup"><span data-stu-id="1f9cf-107">[in] The line of the specified document.</span></span>  
  
 `column`  
 <span data-ttu-id="1f9cf-108">[in] Kolumna określonego dokumentu.</span><span class="sxs-lookup"><span data-stu-id="1f9cf-108">[in] The column of the specified document.</span></span>  
  
 `pRetVal`  
 <span data-ttu-id="1f9cf-109">[out] Wskaźnik do adresu [ISymUnmanagedMethod — interfejs](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedmethod-interface.md) obiekt, który reprezentuje metodę zawierającego punkt przerwania.</span><span class="sxs-lookup"><span data-stu-id="1f9cf-109">[out] A pointer to the address of a [ISymUnmanagedMethod Interface](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedmethod-interface.md) object that represents the method containing the breakpoint.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="1f9cf-110">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="1f9cf-110">Return Value</span></span>  
 <span data-ttu-id="1f9cf-111">Wartość S_OK, jeśli metoda zakończy się pomyślnie; w przeciwnym razie E_FAIL lub inny kod błędu.</span><span class="sxs-lookup"><span data-stu-id="1f9cf-111">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1f9cf-112">Wymagania</span><span class="sxs-lookup"><span data-stu-id="1f9cf-112">Requirements</span></span>  
 <span data-ttu-id="1f9cf-113">**Nagłówek:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="1f9cf-113">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1f9cf-114">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="1f9cf-114">See Also</span></span>  
 [<span data-ttu-id="1f9cf-115">ISymUnmanagedReader, interfejs</span><span class="sxs-lookup"><span data-stu-id="1f9cf-115">ISymUnmanagedReader Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-interface.md)
