---
title: "ISymUnmanagedReader::GetDocument — Metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ISymUnmanagedReader.GetDocument
api_location: diasymreader.dll
api_type: COM
f1_keywords: ISymUnmanagedReader::GetDocument
helpviewer_keywords:
- ISymUnmanagedReader::GetDocument method [.NET Framework debugging]
- GetDocument method [.NET Framework debugging]
ms.assetid: bb203853-6a6d-4027-b9e9-603a7f28b9d3
topic_type: apiref
caps.latest.revision: "7"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 7fcc18b1441093a3e3a1a0e813ccfb4ba3ad507b
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="isymunmanagedreadergetdocument-method"></a><span data-ttu-id="4157c-102">ISymUnmanagedReader::GetDocument — Metoda</span><span class="sxs-lookup"><span data-stu-id="4157c-102">ISymUnmanagedReader::GetDocument Method</span></span>
<span data-ttu-id="4157c-103">Umożliwia znalezienie dokumentu.</span><span class="sxs-lookup"><span data-stu-id="4157c-103">Finds a document.</span></span> <span data-ttu-id="4157c-104">Język dokumentu, dostawcy i typ są opcjonalne.</span><span class="sxs-lookup"><span data-stu-id="4157c-104">The document language, vendor, and type are optional.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4157c-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="4157c-105">Syntax</span></span>  
  
```  
HRESULT GetDocument (  
    [in]  WCHAR  *url,  
    [in]  GUID   language,  
    [in]  GUID   languageVendor,  
    [in]  GUID   documentType,  
    [out, retval] ISymUnmanagedDocument** pRetVal);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="4157c-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="4157c-106">Parameters</span></span>  
 `url`  
 <span data-ttu-id="4157c-107">[in] Adres URL, który identyfikuje dokumentu.</span><span class="sxs-lookup"><span data-stu-id="4157c-107">[in] The URL that identifies the document.</span></span>  
  
 `language`  
 <span data-ttu-id="4157c-108">[in] Z językiem dokumentu.</span><span class="sxs-lookup"><span data-stu-id="4157c-108">[in] The document language.</span></span> <span data-ttu-id="4157c-109">Ten parametr jest opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="4157c-109">This parameter is optional.</span></span>  
  
 `languageVendor`  
 <span data-ttu-id="4157c-110">[in] Tożsamość dostawcy z językiem dokumentu.</span><span class="sxs-lookup"><span data-stu-id="4157c-110">[in] The identity of the vendor for the document language.</span></span> <span data-ttu-id="4157c-111">Ten parametr jest opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="4157c-111">This parameter is optional.</span></span>  
  
 `documentType`  
 <span data-ttu-id="4157c-112">[in] Typ dokumentu.</span><span class="sxs-lookup"><span data-stu-id="4157c-112">[in] The type of the document.</span></span> <span data-ttu-id="4157c-113">Ten parametr jest opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="4157c-113">This parameter is optional.</span></span>  
  
 `pRetVal`  
 <span data-ttu-id="4157c-114">[out] Wskaźnik do interfejsu zwrócony.</span><span class="sxs-lookup"><span data-stu-id="4157c-114">[out] A pointer to the returned interface.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="4157c-115">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="4157c-115">Return Value</span></span>  
 <span data-ttu-id="4157c-116">Wartość S_OK, jeśli metoda zakończy się pomyślnie; w przeciwnym razie E_FAIL lub inny kod błędu.</span><span class="sxs-lookup"><span data-stu-id="4157c-116">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4157c-117">Wymagania</span><span class="sxs-lookup"><span data-stu-id="4157c-117">Requirements</span></span>  
 <span data-ttu-id="4157c-118">**Nagłówek:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="4157c-118">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4157c-119">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="4157c-119">See Also</span></span>  
 [<span data-ttu-id="4157c-120">ISymUnmanagedReader — interfejs</span><span class="sxs-lookup"><span data-stu-id="4157c-120">ISymUnmanagedReader Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-interface.md)
