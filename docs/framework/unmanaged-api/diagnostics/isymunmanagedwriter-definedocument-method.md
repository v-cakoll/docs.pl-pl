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
ms.openlocfilehash: 02b270677131d0960db67b0ac8db38cba2b5e2df
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/23/2019
ms.locfileid: "74428053"
---
# <a name="isymunmanagedwriterdefinedocument-method"></a><span data-ttu-id="d0a02-102">ISymUnmanagedWriter::DefineDocument — Metoda</span><span class="sxs-lookup"><span data-stu-id="d0a02-102">ISymUnmanagedWriter::DefineDocument Method</span></span>
<span data-ttu-id="d0a02-103">Definiuje dokument źródłowy.</span><span class="sxs-lookup"><span data-stu-id="d0a02-103">Defines a source document.</span></span> <span data-ttu-id="d0a02-104">Identyfikatory GUID są udostępniane dla znanych języków, dostawców i typów dokumentów.</span><span class="sxs-lookup"><span data-stu-id="d0a02-104">GUIDs are provided for known languages, vendors, and document types.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d0a02-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="d0a02-105">Syntax</span></span>  
  
```cpp  
HRESULT DefineDocument(  
    [in]  const WCHAR  *url,  
    [in]  const GUID   *language,  
    [in]  const GUID   *languageVendor,  
    [in]  const GUID   *documentType,  
    [out, retval] ISymUnmanagedDocumentWriter**  pRetVal);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d0a02-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="d0a02-106">Parameters</span></span>  
 `url`  
 <span data-ttu-id="d0a02-107">podczas Wskaźnik do `WCHAR`, który definiuje adres URL (Uniform Resource Locator) identyfikujący dokument.</span><span class="sxs-lookup"><span data-stu-id="d0a02-107">[in] A pointer to a `WCHAR` that defines the uniform resource locator (URL) that identifies the document.</span></span>  
  
 `language`  
 <span data-ttu-id="d0a02-108">podczas Wskaźnik do identyfikatora GUID, który definiuje język dokumentu.</span><span class="sxs-lookup"><span data-stu-id="d0a02-108">[in] A pointer to a GUID that defines the document language.</span></span>  
  
 `languageVendor`  
 <span data-ttu-id="d0a02-109">podczas Wskaźnik do identyfikatora GUID, który definiuje tożsamość dostawcy dla języka dokumentu.</span><span class="sxs-lookup"><span data-stu-id="d0a02-109">[in] A pointer to a GUID that defines the identity of the vendor for the document language.</span></span>  
  
 `documentType`  
 <span data-ttu-id="d0a02-110">podczas Wskaźnik do identyfikatora GUID, który definiuje typ dokumentu.</span><span class="sxs-lookup"><span data-stu-id="d0a02-110">[in] A pointer to a GUID that defines the type of the document.</span></span>  
  
 `pRetVal`  
 <span data-ttu-id="d0a02-111">określoną Wskaźnik do zwracanego interfejsu [ISymUnmanagedWriter](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-interface.md) .</span><span class="sxs-lookup"><span data-stu-id="d0a02-111">[out] A pointer to the returned [ISymUnmanagedWriter](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-interface.md) interface.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="d0a02-112">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="d0a02-112">Return Value</span></span>  
 <span data-ttu-id="d0a02-113">S_OK, jeśli metoda się powiedzie; w przeciwnym razie E_FAIL lub inny kod błędu.</span><span class="sxs-lookup"><span data-stu-id="d0a02-113">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d0a02-114">Wymagania</span><span class="sxs-lookup"><span data-stu-id="d0a02-114">Requirements</span></span>  
 <span data-ttu-id="d0a02-115">**Nagłówek:** CorSym. idl, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="d0a02-115">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d0a02-116">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="d0a02-116">See also</span></span>

- [<span data-ttu-id="d0a02-117">ISymUnmanagedWriter, interfejs</span><span class="sxs-lookup"><span data-stu-id="d0a02-117">ISymUnmanagedWriter Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-interface.md)
