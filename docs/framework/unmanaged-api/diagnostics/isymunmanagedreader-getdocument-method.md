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
ms.openlocfilehash: 45548fcd85e58086c2a43ac33e739c8ccb0e833f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33428084"
---
# <a name="isymunmanagedreadergetdocument-method"></a><span data-ttu-id="5781a-102">ISymUnmanagedReader::GetDocument — Metoda</span><span class="sxs-lookup"><span data-stu-id="5781a-102">ISymUnmanagedReader::GetDocument Method</span></span>
<span data-ttu-id="5781a-103">Umożliwia znalezienie dokumentu.</span><span class="sxs-lookup"><span data-stu-id="5781a-103">Finds a document.</span></span> <span data-ttu-id="5781a-104">Język dokumentu, dostawcy i typ są opcjonalne.</span><span class="sxs-lookup"><span data-stu-id="5781a-104">The document language, vendor, and type are optional.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5781a-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="5781a-105">Syntax</span></span>  
  
```  
HRESULT GetDocument (  
    [in]  WCHAR  *url,  
    [in]  GUID   language,  
    [in]  GUID   languageVendor,  
    [in]  GUID   documentType,  
    [out, retval] ISymUnmanagedDocument** pRetVal);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="5781a-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="5781a-106">Parameters</span></span>  
 `url`  
 <span data-ttu-id="5781a-107">[in] Adres URL, który identyfikuje dokumentu.</span><span class="sxs-lookup"><span data-stu-id="5781a-107">[in] The URL that identifies the document.</span></span>  
  
 `language`  
 <span data-ttu-id="5781a-108">[in] Z językiem dokumentu.</span><span class="sxs-lookup"><span data-stu-id="5781a-108">[in] The document language.</span></span> <span data-ttu-id="5781a-109">Ten parametr jest opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="5781a-109">This parameter is optional.</span></span>  
  
 `languageVendor`  
 <span data-ttu-id="5781a-110">[in] Tożsamość dostawcy z językiem dokumentu.</span><span class="sxs-lookup"><span data-stu-id="5781a-110">[in] The identity of the vendor for the document language.</span></span> <span data-ttu-id="5781a-111">Ten parametr jest opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="5781a-111">This parameter is optional.</span></span>  
  
 `documentType`  
 <span data-ttu-id="5781a-112">[in] Typ dokumentu.</span><span class="sxs-lookup"><span data-stu-id="5781a-112">[in] The type of the document.</span></span> <span data-ttu-id="5781a-113">Ten parametr jest opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="5781a-113">This parameter is optional.</span></span>  
  
 `pRetVal`  
 <span data-ttu-id="5781a-114">[out] Wskaźnik do interfejsu zwrócony.</span><span class="sxs-lookup"><span data-stu-id="5781a-114">[out] A pointer to the returned interface.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="5781a-115">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="5781a-115">Return Value</span></span>  
 <span data-ttu-id="5781a-116">Wartość S_OK, jeśli metoda zakończy się pomyślnie; w przeciwnym razie E_FAIL lub inny kod błędu.</span><span class="sxs-lookup"><span data-stu-id="5781a-116">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5781a-117">Wymagania</span><span class="sxs-lookup"><span data-stu-id="5781a-117">Requirements</span></span>  
 <span data-ttu-id="5781a-118">**Header:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="5781a-118">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5781a-119">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="5781a-119">See Also</span></span>  
 [<span data-ttu-id="5781a-120">ISymUnmanagedReader, interfejs</span><span class="sxs-lookup"><span data-stu-id="5781a-120">ISymUnmanagedReader Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-interface.md)
