---
title: ISymUnmanagedDocument::GetURL — Metoda
ms.date: 03/30/2017
api_name:
- ISymUnmanagedDocument.GetURL
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedDocument::GetURL
helpviewer_keywords:
- GetURL method [.NET Framework debugging]
- ISymUnmanagedDocument::GetURL method [.NET Framework debugging]
ms.assetid: 60600178-c2b5-4cab-b3a5-f0f61acebaf1
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 5a447de2bb01e7bbf838ef5443e3ae7951bf8226
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="isymunmanageddocumentgeturl-method"></a><span data-ttu-id="339ae-102">ISymUnmanagedDocument::GetURL — Metoda</span><span class="sxs-lookup"><span data-stu-id="339ae-102">ISymUnmanagedDocument::GetURL Method</span></span>
<span data-ttu-id="339ae-103">Zwraca adres URL (adres URL) dla tego dokumentu.</span><span class="sxs-lookup"><span data-stu-id="339ae-103">Returns the uniform resource locator (URL) for this document.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="339ae-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="339ae-104">Syntax</span></span>  
  
```  
HRESULT GetURL(  
    [in]  ULONG32  cchUrl,  
    [out] ULONG32  *pcchUrl,  
    [out, size_is(cchUrl), length_is(*pcchUrl)] WCHAR szUrl[]);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="339ae-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="339ae-105">Parameters</span></span>  
 `cchUrl`  
 <span data-ttu-id="339ae-106">[in] Rozmiar w znaków z `szURL` buforu.</span><span class="sxs-lookup"><span data-stu-id="339ae-106">[in] The size, in characters, of the `szURL` buffer.</span></span>  
  
 `pcchUrl`  
 <span data-ttu-id="339ae-107">[out] Wskaźnik do zmiennej, która odbiera rozmiaru adresu URL, takie jak zakończenie wartości null.</span><span class="sxs-lookup"><span data-stu-id="339ae-107">[out] A pointer to a variable that receives the size of the URL, including the null termination.</span></span>  
  
 `szUrl`  
 <span data-ttu-id="339ae-108">[out] Bufor zawierający adres URL.</span><span class="sxs-lookup"><span data-stu-id="339ae-108">[out] The buffer containing the URL.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="339ae-109">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="339ae-109">Return Value</span></span>  
 <span data-ttu-id="339ae-110">Wartość S_OK, jeśli metoda zakończy się pomyślnie; w przeciwnym razie kod błędu.</span><span class="sxs-lookup"><span data-stu-id="339ae-110">S_OK if the method succeeds; otherwise, an error code.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="339ae-111">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="339ae-111">See Also</span></span>  
 [<span data-ttu-id="339ae-112">ISymUnmanagedDocument, interfejs</span><span class="sxs-lookup"><span data-stu-id="339ae-112">ISymUnmanagedDocument Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanageddocument-interface.md)
