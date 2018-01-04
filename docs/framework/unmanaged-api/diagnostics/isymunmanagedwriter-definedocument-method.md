---
title: "ISymUnmanagedWriter::DefineDocument — Metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ISymUnmanagedWriter.DefineDocument
api_location: diasymreader.dll
api_type: COM
f1_keywords: ISymUnmanagedWriter::DefineDocument
helpviewer_keywords:
- ISymUnmanagedWriter::DefineDocument method [.NET Framework debugging]
- DefineDocument method [.NET Framework debugging]
ms.assetid: c3bf15b0-3250-4bbe-b9b5-c5d695289b6f
topic_type: apiref
caps.latest.revision: "9"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 522cc3a63101ec7ebe47e8e23878b9d1b12bca1e
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="isymunmanagedwriterdefinedocument-method"></a><span data-ttu-id="1471e-102">ISymUnmanagedWriter::DefineDocument — Metoda</span><span class="sxs-lookup"><span data-stu-id="1471e-102">ISymUnmanagedWriter::DefineDocument Method</span></span>
<span data-ttu-id="1471e-103">Definiuje dokumentu źródłowego.</span><span class="sxs-lookup"><span data-stu-id="1471e-103">Defines a source document.</span></span> <span data-ttu-id="1471e-104">Identyfikatory GUID są dostępne dla języków znanych dostawców i typów dokumentów.</span><span class="sxs-lookup"><span data-stu-id="1471e-104">GUIDs are provided for known languages, vendors, and document types.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1471e-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="1471e-105">Syntax</span></span>  
  
```  
HRESULT DefineDocument(  
    [in]  const WCHAR  *url,  
    [in]  const GUID   *language,  
    [in]  const GUID   *languageVendor,  
    [in]  const GUID   *documentType,  
    [out, retval] ISymUnmanagedDocumentWriter**  pRetVal);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="1471e-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="1471e-106">Parameters</span></span>  
 `url`  
 <span data-ttu-id="1471e-107">[in] Wskaźnik do `WCHAR` definiuje adres URL (adres URL) określający dokumentu.</span><span class="sxs-lookup"><span data-stu-id="1471e-107">[in] A pointer to a `WCHAR` that defines the uniform resource locator (URL) that identifies the document.</span></span>  
  
 `language`  
 <span data-ttu-id="1471e-108">[in] Wskaźnik do identyfikatora GUID, który definiuje z językiem dokumentu.</span><span class="sxs-lookup"><span data-stu-id="1471e-108">[in] A pointer to a GUID that defines the document language.</span></span>  
  
 `languageVendor`  
 <span data-ttu-id="1471e-109">[in] Wskaźnik identyfikator GUID, który określa tożsamość dostawcy z językiem dokumentu.</span><span class="sxs-lookup"><span data-stu-id="1471e-109">[in] A pointer to a GUID that defines the identity of the vendor for the document language.</span></span>  
  
 `documentType`  
 <span data-ttu-id="1471e-110">[in] Wskaźnik do identyfikatora GUID, który definiuje typ dokumentu.</span><span class="sxs-lookup"><span data-stu-id="1471e-110">[in] A pointer to a GUID that defines the type of the document.</span></span>  
  
 `pRetVal`  
 <span data-ttu-id="1471e-111">[out] Wskaźnik do zwróconego [ISymUnmanagedWriter](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-interface.md) interfejsu.</span><span class="sxs-lookup"><span data-stu-id="1471e-111">[out] A pointer to the returned [ISymUnmanagedWriter](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-interface.md) interface.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="1471e-112">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="1471e-112">Return Value</span></span>  
 <span data-ttu-id="1471e-113">Wartość S_OK, jeśli metoda zakończy się pomyślnie; w przeciwnym razie E_FAIL lub inny kod błędu.</span><span class="sxs-lookup"><span data-stu-id="1471e-113">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1471e-114">Wymagania</span><span class="sxs-lookup"><span data-stu-id="1471e-114">Requirements</span></span>  
 <span data-ttu-id="1471e-115">**Nagłówek:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="1471e-115">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1471e-116">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="1471e-116">See Also</span></span>  
 [<span data-ttu-id="1471e-117">ISymUnmanagedWriter, interfejs</span><span class="sxs-lookup"><span data-stu-id="1471e-117">ISymUnmanagedWriter Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-interface.md)
