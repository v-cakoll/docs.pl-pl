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
ms.openlocfilehash: 00baed93bd9ab48c92de83dac76931c3149afc2b
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33424641"
---
# <a name="isymunmanageddocumentgetsourcerange-method"></a><span data-ttu-id="44fca-102">ISymUnmanagedDocument::GetSourceRange — Metoda</span><span class="sxs-lookup"><span data-stu-id="44fca-102">ISymUnmanagedDocument::GetSourceRange Method</span></span>
<span data-ttu-id="44fca-103">Zwraca określony zakres osadzone źródło do danego buforu.</span><span class="sxs-lookup"><span data-stu-id="44fca-103">Returns the specified range of the embedded source into the given buffer.</span></span> <span data-ttu-id="44fca-104">Rozmiar buforu musi być wystarczająco duży, aby pomieścić źródła.</span><span class="sxs-lookup"><span data-stu-id="44fca-104">The buffer must be large enough to hold the source.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="44fca-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="44fca-105">Syntax</span></span>  
  
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
  
#### <a name="parameters"></a><span data-ttu-id="44fca-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="44fca-106">Parameters</span></span>  
 `startLine`  
 <span data-ttu-id="44fca-107">[in] Linia początkowa w bieżącym dokumencie.</span><span class="sxs-lookup"><span data-stu-id="44fca-107">[in] The starting line in the current document.</span></span>  
  
 `startColumn`  
 <span data-ttu-id="44fca-108">[in] Kolumna początkowa w bieżącym dokumencie.</span><span class="sxs-lookup"><span data-stu-id="44fca-108">[in] The starting column in the current document.</span></span>  
  
 `endLine`  
 <span data-ttu-id="44fca-109">[in] Końcowego wiersza w bieżącym dokumencie.</span><span class="sxs-lookup"><span data-stu-id="44fca-109">[in] The final line in the current document.</span></span>  
  
 `endColumn`  
 <span data-ttu-id="44fca-110">[in] Ostatniej kolumny w bieżącym dokumencie.</span><span class="sxs-lookup"><span data-stu-id="44fca-110">[in] The final column in the current document.</span></span>  
  
 `cSourceBytes`  
 <span data-ttu-id="44fca-111">[in] Rozmiar źródła, w bajtach.</span><span class="sxs-lookup"><span data-stu-id="44fca-111">[in] The size of the source, in bytes.</span></span>  
  
 `pcSourceBytes`  
 <span data-ttu-id="44fca-112">[out] Wskaźnik do zmiennej, która odbiera rozmiar źródła.</span><span class="sxs-lookup"><span data-stu-id="44fca-112">[out] A pointer to a variable that receives the source size.</span></span>  
  
 `source`  
 <span data-ttu-id="44fca-113">[out] Rozmiar i długość zakresu określonego dokumentu źródłowego w bajtach.</span><span class="sxs-lookup"><span data-stu-id="44fca-113">[out] The size and length of the specified range of the source document, in bytes.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="44fca-114">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="44fca-114">Return Value</span></span>  
 <span data-ttu-id="44fca-115">Wartość S_OK, jeśli metoda zakończy się powodzeniem.</span><span class="sxs-lookup"><span data-stu-id="44fca-115">S_OK if the method succeeds.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="44fca-116">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="44fca-116">See Also</span></span>  
 [<span data-ttu-id="44fca-117">ISymUnmanagedDocument, interfejs</span><span class="sxs-lookup"><span data-stu-id="44fca-117">ISymUnmanagedDocument Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanageddocument-interface.md)
