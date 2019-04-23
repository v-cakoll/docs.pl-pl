---
title: ISymUnmanagedDocument::GetSourceRange — Metoda
ms.date: 03/30/2017
api_name:
- ISymUnmanagedDocument.GetSourceRange
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedDocument::GetSourceRange
helpviewer_keywords:
- ISymUnmanagedDocument::GetSourceRange method [.NET Framework debugging]
- GetSourceRange method [.NET Framework debugging]
ms.assetid: 20fefee7-1040-41ba-93dc-bd42f68b90c2
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 59420cfd29c3228aece9fc5ae02b950db6099ea0
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59218475"
---
# <a name="isymunmanageddocumentgetsourcerange-method"></a><span data-ttu-id="9961f-102">ISymUnmanagedDocument::GetSourceRange — Metoda</span><span class="sxs-lookup"><span data-stu-id="9961f-102">ISymUnmanagedDocument::GetSourceRange Method</span></span>
<span data-ttu-id="9961f-103">Zwraca określony zakres osadzonego źródła do podanego buforu.</span><span class="sxs-lookup"><span data-stu-id="9961f-103">Returns the specified range of the embedded source into the given buffer.</span></span> <span data-ttu-id="9961f-104">Rozmiar buforu musi być wystarczająco duży, aby pomieścić źródła.</span><span class="sxs-lookup"><span data-stu-id="9961f-104">The buffer must be large enough to hold the source.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9961f-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="9961f-105">Syntax</span></span>  
  
```  
HRESULT GetSourceRange(  
    [in]  ULONG32  startLine,  
    [in]  ULONG32  startColumn,  
    [in]  ULONG32  endLine,  
    [in]  ULONG32  endColumn,  
    [in]  ULONG32  cSourceBytes,  
    [out] ULONG32  *pcSourceBytes,  
    [out, size_is(cSourceBytes),  
        length_is(*pcSourceBytes)] BYTE source[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="9961f-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="9961f-106">Parameters</span></span>  
 `startLine`  
 <span data-ttu-id="9961f-107">[in] Linia początkowa w bieżącym dokumencie.</span><span class="sxs-lookup"><span data-stu-id="9961f-107">[in] The starting line in the current document.</span></span>  
  
 `startColumn`  
 <span data-ttu-id="9961f-108">[in] Kolumna początkowa w bieżącym dokumencie.</span><span class="sxs-lookup"><span data-stu-id="9961f-108">[in] The starting column in the current document.</span></span>  
  
 `endLine`  
 <span data-ttu-id="9961f-109">[in] Ostatni wiersz w bieżącym dokumencie.</span><span class="sxs-lookup"><span data-stu-id="9961f-109">[in] The final line in the current document.</span></span>  
  
 `endColumn`  
 <span data-ttu-id="9961f-110">[in] Ostatniej kolumny w bieżącym dokumencie.</span><span class="sxs-lookup"><span data-stu-id="9961f-110">[in] The final column in the current document.</span></span>  
  
 `cSourceBytes`  
 <span data-ttu-id="9961f-111">[in] Rozmiar źródła, w bajtach.</span><span class="sxs-lookup"><span data-stu-id="9961f-111">[in] The size of the source, in bytes.</span></span>  
  
 `pcSourceBytes`  
 <span data-ttu-id="9961f-112">[out] Wskaźnik do zmiennej, która odbiera rozmiar źródła.</span><span class="sxs-lookup"><span data-stu-id="9961f-112">[out] A pointer to a variable that receives the source size.</span></span>  
  
 `source`  
 <span data-ttu-id="9961f-113">[out] Rozmiar i długość zakresu określonego dokumentu źródłowego, w bajtach.</span><span class="sxs-lookup"><span data-stu-id="9961f-113">[out] The size and length of the specified range of the source document, in bytes.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="9961f-114">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="9961f-114">Return Value</span></span>  
 <span data-ttu-id="9961f-115">S_OK, jeśli metoda zakończy się powodzeniem.</span><span class="sxs-lookup"><span data-stu-id="9961f-115">S_OK if the method succeeds.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9961f-116">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="9961f-116">See also</span></span>

- [<span data-ttu-id="9961f-117">ISymUnmanagedDocument, interfejs</span><span class="sxs-lookup"><span data-stu-id="9961f-117">ISymUnmanagedDocument Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanageddocument-interface.md)
