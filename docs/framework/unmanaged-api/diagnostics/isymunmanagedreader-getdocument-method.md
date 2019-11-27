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
ms.openlocfilehash: 1fcb885b6e19457065c2ca9971f068b42f97147d
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/23/2019
ms.locfileid: "74448346"
---
# <a name="isymunmanagedreadergetdocument-method"></a><span data-ttu-id="5624c-102">ISymUnmanagedReader::GetDocument — Metoda</span><span class="sxs-lookup"><span data-stu-id="5624c-102">ISymUnmanagedReader::GetDocument Method</span></span>
<span data-ttu-id="5624c-103">Znajduje dokument.</span><span class="sxs-lookup"><span data-stu-id="5624c-103">Finds a document.</span></span> <span data-ttu-id="5624c-104">Język dokumentu, dostawca i typ są opcjonalne.</span><span class="sxs-lookup"><span data-stu-id="5624c-104">The document language, vendor, and type are optional.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5624c-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="5624c-105">Syntax</span></span>  
  
```cpp  
HRESULT GetDocument (  
    [in]  WCHAR  *url,  
    [in]  GUID   language,  
    [in]  GUID   languageVendor,  
    [in]  GUID   documentType,  
    [out, retval] ISymUnmanagedDocument** pRetVal);  
```  
  
## <a name="parameters"></a><span data-ttu-id="5624c-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="5624c-106">Parameters</span></span>  
 `url`  
 <span data-ttu-id="5624c-107">podczas Adres URL identyfikujący dokument.</span><span class="sxs-lookup"><span data-stu-id="5624c-107">[in] The URL that identifies the document.</span></span>  
  
 `language`  
 <span data-ttu-id="5624c-108">podczas Język dokumentu.</span><span class="sxs-lookup"><span data-stu-id="5624c-108">[in] The document language.</span></span> <span data-ttu-id="5624c-109">Ten parametr jest opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="5624c-109">This parameter is optional.</span></span>  
  
 `languageVendor`  
 <span data-ttu-id="5624c-110">podczas Tożsamość dostawcy dla języka dokumentu.</span><span class="sxs-lookup"><span data-stu-id="5624c-110">[in] The identity of the vendor for the document language.</span></span> <span data-ttu-id="5624c-111">Ten parametr jest opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="5624c-111">This parameter is optional.</span></span>  
  
 `documentType`  
 <span data-ttu-id="5624c-112">podczas Typ dokumentu.</span><span class="sxs-lookup"><span data-stu-id="5624c-112">[in] The type of the document.</span></span> <span data-ttu-id="5624c-113">Ten parametr jest opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="5624c-113">This parameter is optional.</span></span>  
  
 `pRetVal`  
 <span data-ttu-id="5624c-114">określoną Wskaźnik do zwracanego interfejsu.</span><span class="sxs-lookup"><span data-stu-id="5624c-114">[out] A pointer to the returned interface.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="5624c-115">Wartość zwrócona</span><span class="sxs-lookup"><span data-stu-id="5624c-115">Return Value</span></span>  
 <span data-ttu-id="5624c-116">S_OK, jeśli metoda się powiedzie; w przeciwnym razie E_FAIL lub inny kod błędu.</span><span class="sxs-lookup"><span data-stu-id="5624c-116">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5624c-117">Wymagania</span><span class="sxs-lookup"><span data-stu-id="5624c-117">Requirements</span></span>  
 <span data-ttu-id="5624c-118">**Nagłówek:** CorSym. idl, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="5624c-118">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5624c-119">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="5624c-119">See also</span></span>

- [<span data-ttu-id="5624c-120">ISymUnmanagedReader, interfejs</span><span class="sxs-lookup"><span data-stu-id="5624c-120">ISymUnmanagedReader Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-interface.md)
