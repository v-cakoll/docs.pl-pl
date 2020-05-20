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
ms.openlocfilehash: 3685707f1983ffec413e9cea2df5034ac53f643a
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/19/2020
ms.locfileid: "83615595"
---
# <a name="isymunmanageddocumentgeturl-method"></a><span data-ttu-id="a12fb-102">ISymUnmanagedDocument::GetURL — Metoda</span><span class="sxs-lookup"><span data-stu-id="a12fb-102">ISymUnmanagedDocument::GetURL Method</span></span>
<span data-ttu-id="a12fb-103">Zwraca adres URL (Uniform Resource Locator) dla tego dokumentu.</span><span class="sxs-lookup"><span data-stu-id="a12fb-103">Returns the uniform resource locator (URL) for this document.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a12fb-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="a12fb-104">Syntax</span></span>  
  
```cpp  
HRESULT GetURL(  
    [in]  ULONG32  cchUrl,  
    [out] ULONG32  *pcchUrl,  
    [out, size_is(cchUrl), length_is(*pcchUrl)] WCHAR szUrl[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="a12fb-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="a12fb-105">Parameters</span></span>  
 `cchUrl`  
 <span data-ttu-id="a12fb-106">podczas Rozmiar (w znakach) `szURL` buforu.</span><span class="sxs-lookup"><span data-stu-id="a12fb-106">[in] The size, in characters, of the `szURL` buffer.</span></span>  
  
 `pcchUrl`  
 <span data-ttu-id="a12fb-107">określoną Wskaźnik do zmiennej, która otrzymuje rozmiar adresu URL, łącznie z zakończeniem o wartości null.</span><span class="sxs-lookup"><span data-stu-id="a12fb-107">[out] A pointer to a variable that receives the size of the URL, including the null termination.</span></span>  
  
 `szUrl`  
 <span data-ttu-id="a12fb-108">określoną Bufor zawierający adres URL.</span><span class="sxs-lookup"><span data-stu-id="a12fb-108">[out] The buffer containing the URL.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="a12fb-109">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="a12fb-109">Return Value</span></span>  
 <span data-ttu-id="a12fb-110">S_OK, jeśli metoda się powiedzie; w przeciwnym razie kod błędu.</span><span class="sxs-lookup"><span data-stu-id="a12fb-110">S_OK if the method succeeds; otherwise, an error code.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a12fb-111">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="a12fb-111">See also</span></span>

- [<span data-ttu-id="a12fb-112">ISymUnmanagedDocument, interfejs</span><span class="sxs-lookup"><span data-stu-id="a12fb-112">ISymUnmanagedDocument Interface</span></span>](isymunmanageddocument-interface.md)
