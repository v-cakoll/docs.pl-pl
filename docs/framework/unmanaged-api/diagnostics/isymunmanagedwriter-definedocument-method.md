---
title: ISymUnmanagedWriter::DefineDocument — Metoda
ms.date: 03/30/2017
api_name:
- ISymUnmanagedWriter.DefineDocument
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedWriter::DefineDocument
helpviewer_keywords:
- ISymUnmanagedWriter::DefineDocument method [.NET Framework debugging]
- DefineDocument method [.NET Framework debugging]
ms.assetid: c3bf15b0-3250-4bbe-b9b5-c5d695289b6f
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: d1c214918b4a41ac989a3804c9146c4a54c5909f
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54738212"
---
# <a name="isymunmanagedwriterdefinedocument-method"></a><span data-ttu-id="a4b8f-102">ISymUnmanagedWriter::DefineDocument — Metoda</span><span class="sxs-lookup"><span data-stu-id="a4b8f-102">ISymUnmanagedWriter::DefineDocument Method</span></span>
<span data-ttu-id="a4b8f-103">Definiuje dokumentu źródłowego.</span><span class="sxs-lookup"><span data-stu-id="a4b8f-103">Defines a source document.</span></span> <span data-ttu-id="a4b8f-104">Identyfikatory GUID są dostarczane dla znanych języków, dostawców i typy dokumentów.</span><span class="sxs-lookup"><span data-stu-id="a4b8f-104">GUIDs are provided for known languages, vendors, and document types.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a4b8f-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="a4b8f-105">Syntax</span></span>  
  
```  
HRESULT DefineDocument(  
    [in]  const WCHAR  *url,  
    [in]  const GUID   *language,  
    [in]  const GUID   *languageVendor,  
    [in]  const GUID   *documentType,  
    [out, retval] ISymUnmanagedDocumentWriter**  pRetVal);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="a4b8f-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="a4b8f-106">Parameters</span></span>  
 `url`  
 <span data-ttu-id="a4b8f-107">[in] Wskaźnik do `WCHAR` definiujący adres URL (adres URL) identyfikujący dokumentu.</span><span class="sxs-lookup"><span data-stu-id="a4b8f-107">[in] A pointer to a `WCHAR` that defines the uniform resource locator (URL) that identifies the document.</span></span>  
  
 `language`  
 <span data-ttu-id="a4b8f-108">[in] Wskaźnik do identyfikatora GUID, który definiuje języka dokumentu.</span><span class="sxs-lookup"><span data-stu-id="a4b8f-108">[in] A pointer to a GUID that defines the document language.</span></span>  
  
 `languageVendor`  
 <span data-ttu-id="a4b8f-109">[in] Wskaźnik na identyfikator GUID, który definiuje tożsamość przez dostawcę dla języka dokumentu.</span><span class="sxs-lookup"><span data-stu-id="a4b8f-109">[in] A pointer to a GUID that defines the identity of the vendor for the document language.</span></span>  
  
 `documentType`  
 <span data-ttu-id="a4b8f-110">[in] Wskaźnik na identyfikator GUID, który definiuje typ dokumentu.</span><span class="sxs-lookup"><span data-stu-id="a4b8f-110">[in] A pointer to a GUID that defines the type of the document.</span></span>  
  
 `pRetVal`  
 <span data-ttu-id="a4b8f-111">[out] Wskaźnik do zwracanego [isymunmanagedwriter —](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-interface.md) interfejsu.</span><span class="sxs-lookup"><span data-stu-id="a4b8f-111">[out] A pointer to the returned [ISymUnmanagedWriter](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-interface.md) interface.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="a4b8f-112">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="a4b8f-112">Return Value</span></span>  
 <span data-ttu-id="a4b8f-113">S_OK, jeśli metoda się powiedzie; w przeciwnym razie E_FAIL lub innego kodu błędu.</span><span class="sxs-lookup"><span data-stu-id="a4b8f-113">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a4b8f-114">Wymagania</span><span class="sxs-lookup"><span data-stu-id="a4b8f-114">Requirements</span></span>  
 <span data-ttu-id="a4b8f-115">**Nagłówek:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="a4b8f-115">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a4b8f-116">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="a4b8f-116">See also</span></span>
- [<span data-ttu-id="a4b8f-117">ISymUnmanagedWriter, interfejs</span><span class="sxs-lookup"><span data-stu-id="a4b8f-117">ISymUnmanagedWriter Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-interface.md)
