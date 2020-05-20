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
ms.openlocfilehash: 950fb3b9c51ae2c9470b5aadd31c877d7aa6b6f6
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/19/2020
ms.locfileid: "83615062"
---
# <a name="isymunmanagedreadergetdocument-method"></a><span data-ttu-id="157e4-102">ISymUnmanagedReader::GetDocument — Metoda</span><span class="sxs-lookup"><span data-stu-id="157e4-102">ISymUnmanagedReader::GetDocument Method</span></span>
<span data-ttu-id="157e4-103">Znajduje dokument.</span><span class="sxs-lookup"><span data-stu-id="157e4-103">Finds a document.</span></span> <span data-ttu-id="157e4-104">Język dokumentu, dostawca i typ są opcjonalne.</span><span class="sxs-lookup"><span data-stu-id="157e4-104">The document language, vendor, and type are optional.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="157e4-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="157e4-105">Syntax</span></span>  
  
```cpp  
HRESULT GetDocument (  
    [in]  WCHAR  *url,  
    [in]  GUID   language,  
    [in]  GUID   languageVendor,  
    [in]  GUID   documentType,  
    [out, retval] ISymUnmanagedDocument** pRetVal);  
```  
  
## <a name="parameters"></a><span data-ttu-id="157e4-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="157e4-106">Parameters</span></span>  
 `url`  
 <span data-ttu-id="157e4-107">podczas Adres URL identyfikujący dokument.</span><span class="sxs-lookup"><span data-stu-id="157e4-107">[in] The URL that identifies the document.</span></span>  
  
 `language`  
 <span data-ttu-id="157e4-108">podczas Język dokumentu.</span><span class="sxs-lookup"><span data-stu-id="157e4-108">[in] The document language.</span></span> <span data-ttu-id="157e4-109">Ten parametr jest opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="157e4-109">This parameter is optional.</span></span>  
  
 `languageVendor`  
 <span data-ttu-id="157e4-110">podczas Tożsamość dostawcy dla języka dokumentu.</span><span class="sxs-lookup"><span data-stu-id="157e4-110">[in] The identity of the vendor for the document language.</span></span> <span data-ttu-id="157e4-111">Ten parametr jest opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="157e4-111">This parameter is optional.</span></span>  
  
 `documentType`  
 <span data-ttu-id="157e4-112">podczas Typ dokumentu.</span><span class="sxs-lookup"><span data-stu-id="157e4-112">[in] The type of the document.</span></span> <span data-ttu-id="157e4-113">Ten parametr jest opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="157e4-113">This parameter is optional.</span></span>  
  
 `pRetVal`  
 <span data-ttu-id="157e4-114">określoną Wskaźnik do zwracanego interfejsu.</span><span class="sxs-lookup"><span data-stu-id="157e4-114">[out] A pointer to the returned interface.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="157e4-115">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="157e4-115">Return Value</span></span>  
 <span data-ttu-id="157e4-116">S_OK, jeśli metoda się powiedzie; w przeciwnym razie E_FAIL lub inny kod błędu.</span><span class="sxs-lookup"><span data-stu-id="157e4-116">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="157e4-117">Wymagania</span><span class="sxs-lookup"><span data-stu-id="157e4-117">Requirements</span></span>  
 <span data-ttu-id="157e4-118">**Nagłówek:** CorSym. idl, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="157e4-118">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="157e4-119">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="157e4-119">See also</span></span>

- [<span data-ttu-id="157e4-120">ISymUnmanagedReader — Interfejs</span><span class="sxs-lookup"><span data-stu-id="157e4-120">ISymUnmanagedReader Interface</span></span>](isymunmanagedreader-interface.md)
