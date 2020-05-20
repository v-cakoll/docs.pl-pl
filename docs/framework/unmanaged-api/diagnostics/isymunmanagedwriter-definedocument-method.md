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
ms.openlocfilehash: fdcfb0c4f9c21eb516f4196d0c8f682669468219
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/19/2020
ms.locfileid: "83615231"
---
# <a name="isymunmanagedwriterdefinedocument-method"></a><span data-ttu-id="bf91f-102">ISymUnmanagedWriter::DefineDocument — Metoda</span><span class="sxs-lookup"><span data-stu-id="bf91f-102">ISymUnmanagedWriter::DefineDocument Method</span></span>
<span data-ttu-id="bf91f-103">Definiuje dokument źródłowy.</span><span class="sxs-lookup"><span data-stu-id="bf91f-103">Defines a source document.</span></span> <span data-ttu-id="bf91f-104">Identyfikatory GUID są udostępniane dla znanych języków, dostawców i typów dokumentów.</span><span class="sxs-lookup"><span data-stu-id="bf91f-104">GUIDs are provided for known languages, vendors, and document types.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bf91f-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="bf91f-105">Syntax</span></span>  
  
```cpp  
HRESULT DefineDocument(  
    [in]  const WCHAR  *url,  
    [in]  const GUID   *language,  
    [in]  const GUID   *languageVendor,  
    [in]  const GUID   *documentType,  
    [out, retval] ISymUnmanagedDocumentWriter**  pRetVal);  
```  
  
## <a name="parameters"></a><span data-ttu-id="bf91f-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="bf91f-106">Parameters</span></span>  
 `url`  
 <span data-ttu-id="bf91f-107">podczas Wskaźnik do obiektu `WCHAR` , który definiuje adres URL (Uniform Resource Locator) identyfikujący dokument.</span><span class="sxs-lookup"><span data-stu-id="bf91f-107">[in] A pointer to a `WCHAR` that defines the uniform resource locator (URL) that identifies the document.</span></span>  
  
 `language`  
 <span data-ttu-id="bf91f-108">podczas Wskaźnik do identyfikatora GUID, który definiuje język dokumentu.</span><span class="sxs-lookup"><span data-stu-id="bf91f-108">[in] A pointer to a GUID that defines the document language.</span></span>  
  
 `languageVendor`  
 <span data-ttu-id="bf91f-109">podczas Wskaźnik do identyfikatora GUID, który definiuje tożsamość dostawcy dla języka dokumentu.</span><span class="sxs-lookup"><span data-stu-id="bf91f-109">[in] A pointer to a GUID that defines the identity of the vendor for the document language.</span></span>  
  
 `documentType`  
 <span data-ttu-id="bf91f-110">podczas Wskaźnik do identyfikatora GUID, który definiuje typ dokumentu.</span><span class="sxs-lookup"><span data-stu-id="bf91f-110">[in] A pointer to a GUID that defines the type of the document.</span></span>  
  
 `pRetVal`  
 <span data-ttu-id="bf91f-111">określoną Wskaźnik do zwracanego interfejsu [ISymUnmanagedWriter](isymunmanagedwriter-interface.md) .</span><span class="sxs-lookup"><span data-stu-id="bf91f-111">[out] A pointer to the returned [ISymUnmanagedWriter](isymunmanagedwriter-interface.md) interface.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="bf91f-112">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="bf91f-112">Return Value</span></span>  
 <span data-ttu-id="bf91f-113">S_OK, jeśli metoda się powiedzie; w przeciwnym razie E_FAIL lub inny kod błędu.</span><span class="sxs-lookup"><span data-stu-id="bf91f-113">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="bf91f-114">Wymagania</span><span class="sxs-lookup"><span data-stu-id="bf91f-114">Requirements</span></span>  
 <span data-ttu-id="bf91f-115">**Nagłówek:** CorSym. idl, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="bf91f-115">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bf91f-116">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="bf91f-116">See also</span></span>

- [<span data-ttu-id="bf91f-117">ISymUnmanagedWriter — Interfejs</span><span class="sxs-lookup"><span data-stu-id="bf91f-117">ISymUnmanagedWriter Interface</span></span>](isymunmanagedwriter-interface.md)
