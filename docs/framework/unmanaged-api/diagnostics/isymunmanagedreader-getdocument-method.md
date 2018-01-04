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
ms.workload: dotnet
ms.openlocfilehash: 00ded0e7e88cacbcedb66e1cef27e4f5eaaf4d29
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="isymunmanagedreadergetdocument-method"></a><span data-ttu-id="67fb5-102">ISymUnmanagedReader::GetDocument — Metoda</span><span class="sxs-lookup"><span data-stu-id="67fb5-102">ISymUnmanagedReader::GetDocument Method</span></span>
<span data-ttu-id="67fb5-103">Umożliwia znalezienie dokumentu.</span><span class="sxs-lookup"><span data-stu-id="67fb5-103">Finds a document.</span></span> <span data-ttu-id="67fb5-104">Język dokumentu, dostawcy i typ są opcjonalne.</span><span class="sxs-lookup"><span data-stu-id="67fb5-104">The document language, vendor, and type are optional.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="67fb5-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="67fb5-105">Syntax</span></span>  
  
```  
HRESULT GetDocument (  
    [in]  WCHAR  *url,  
    [in]  GUID   language,  
    [in]  GUID   languageVendor,  
    [in]  GUID   documentType,  
    [out, retval] ISymUnmanagedDocument** pRetVal);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="67fb5-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="67fb5-106">Parameters</span></span>  
 `url`  
 <span data-ttu-id="67fb5-107">[in] Adres URL, który identyfikuje dokumentu.</span><span class="sxs-lookup"><span data-stu-id="67fb5-107">[in] The URL that identifies the document.</span></span>  
  
 `language`  
 <span data-ttu-id="67fb5-108">[in] Z językiem dokumentu.</span><span class="sxs-lookup"><span data-stu-id="67fb5-108">[in] The document language.</span></span> <span data-ttu-id="67fb5-109">Ten parametr jest opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="67fb5-109">This parameter is optional.</span></span>  
  
 `languageVendor`  
 <span data-ttu-id="67fb5-110">[in] Tożsamość dostawcy z językiem dokumentu.</span><span class="sxs-lookup"><span data-stu-id="67fb5-110">[in] The identity of the vendor for the document language.</span></span> <span data-ttu-id="67fb5-111">Ten parametr jest opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="67fb5-111">This parameter is optional.</span></span>  
  
 `documentType`  
 <span data-ttu-id="67fb5-112">[in] Typ dokumentu.</span><span class="sxs-lookup"><span data-stu-id="67fb5-112">[in] The type of the document.</span></span> <span data-ttu-id="67fb5-113">Ten parametr jest opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="67fb5-113">This parameter is optional.</span></span>  
  
 `pRetVal`  
 <span data-ttu-id="67fb5-114">[out] Wskaźnik do interfejsu zwrócony.</span><span class="sxs-lookup"><span data-stu-id="67fb5-114">[out] A pointer to the returned interface.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="67fb5-115">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="67fb5-115">Return Value</span></span>  
 <span data-ttu-id="67fb5-116">Wartość S_OK, jeśli metoda zakończy się pomyślnie; w przeciwnym razie E_FAIL lub inny kod błędu.</span><span class="sxs-lookup"><span data-stu-id="67fb5-116">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="67fb5-117">Wymagania</span><span class="sxs-lookup"><span data-stu-id="67fb5-117">Requirements</span></span>  
 <span data-ttu-id="67fb5-118">**Nagłówek:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="67fb5-118">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="67fb5-119">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="67fb5-119">See Also</span></span>  
 [<span data-ttu-id="67fb5-120">ISymUnmanagedReader, interfejs</span><span class="sxs-lookup"><span data-stu-id="67fb5-120">ISymUnmanagedReader Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-interface.md)
