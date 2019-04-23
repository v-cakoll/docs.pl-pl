---
title: ISymUnmanagedReader::GetDocument — Metoda
ms.date: 03/30/2017
api_name:
- ISymUnmanagedReader.GetDocument
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedReader::GetDocument
helpviewer_keywords:
- ISymUnmanagedReader::GetDocument method [.NET Framework debugging]
- GetDocument method [.NET Framework debugging]
ms.assetid: bb203853-6a6d-4027-b9e9-603a7f28b9d3
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 2a173c23ea33532f05e30d072677715e15d04018
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59093687"
---
# <a name="isymunmanagedreadergetdocument-method"></a><span data-ttu-id="1fe1b-102">ISymUnmanagedReader::GetDocument — Metoda</span><span class="sxs-lookup"><span data-stu-id="1fe1b-102">ISymUnmanagedReader::GetDocument Method</span></span>
<span data-ttu-id="1fe1b-103">Umożliwia znalezienie dokumentu.</span><span class="sxs-lookup"><span data-stu-id="1fe1b-103">Finds a document.</span></span> <span data-ttu-id="1fe1b-104">Język dokumentu, dostawcy i typ są opcjonalne.</span><span class="sxs-lookup"><span data-stu-id="1fe1b-104">The document language, vendor, and type are optional.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1fe1b-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="1fe1b-105">Syntax</span></span>  
  
```  
HRESULT GetDocument (  
    [in]  WCHAR  *url,  
    [in]  GUID   language,  
    [in]  GUID   languageVendor,  
    [in]  GUID   documentType,  
    [out, retval] ISymUnmanagedDocument** pRetVal);  
```  
  
## <a name="parameters"></a><span data-ttu-id="1fe1b-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="1fe1b-106">Parameters</span></span>  
 `url`  
 <span data-ttu-id="1fe1b-107">[in] Adres URL, który identyfikuje dokumentu.</span><span class="sxs-lookup"><span data-stu-id="1fe1b-107">[in] The URL that identifies the document.</span></span>  
  
 `language`  
 <span data-ttu-id="1fe1b-108">[in] Język dokumentu.</span><span class="sxs-lookup"><span data-stu-id="1fe1b-108">[in] The document language.</span></span> <span data-ttu-id="1fe1b-109">Ten parametr jest opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="1fe1b-109">This parameter is optional.</span></span>  
  
 `languageVendor`  
 <span data-ttu-id="1fe1b-110">[in] Tożsamość dostawcy języka dokumentu.</span><span class="sxs-lookup"><span data-stu-id="1fe1b-110">[in] The identity of the vendor for the document language.</span></span> <span data-ttu-id="1fe1b-111">Ten parametr jest opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="1fe1b-111">This parameter is optional.</span></span>  
  
 `documentType`  
 <span data-ttu-id="1fe1b-112">[in] Typ dokumentu.</span><span class="sxs-lookup"><span data-stu-id="1fe1b-112">[in] The type of the document.</span></span> <span data-ttu-id="1fe1b-113">Ten parametr jest opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="1fe1b-113">This parameter is optional.</span></span>  
  
 `pRetVal`  
 <span data-ttu-id="1fe1b-114">[out] Wskaźnik do interfejsu zwrócone.</span><span class="sxs-lookup"><span data-stu-id="1fe1b-114">[out] A pointer to the returned interface.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="1fe1b-115">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="1fe1b-115">Return Value</span></span>  
 <span data-ttu-id="1fe1b-116">S_OK, jeśli metoda się powiedzie; w przeciwnym razie E_FAIL lub innego kodu błędu.</span><span class="sxs-lookup"><span data-stu-id="1fe1b-116">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1fe1b-117">Wymagania</span><span class="sxs-lookup"><span data-stu-id="1fe1b-117">Requirements</span></span>  
 <span data-ttu-id="1fe1b-118">**Nagłówek:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="1fe1b-118">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1fe1b-119">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="1fe1b-119">See also</span></span>

- [<span data-ttu-id="1fe1b-120">ISymUnmanagedReader, interfejs</span><span class="sxs-lookup"><span data-stu-id="1fe1b-120">ISymUnmanagedReader Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-interface.md)
