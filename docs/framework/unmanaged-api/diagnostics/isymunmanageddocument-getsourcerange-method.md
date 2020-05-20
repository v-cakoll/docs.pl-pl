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
ms.openlocfilehash: 841379702e24428a8092cfd1d2cbd3c5b4e17ba4
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/19/2020
ms.locfileid: "83615608"
---
# <a name="isymunmanageddocumentgetsourcerange-method"></a><span data-ttu-id="4df69-102">ISymUnmanagedDocument::GetSourceRange — Metoda</span><span class="sxs-lookup"><span data-stu-id="4df69-102">ISymUnmanagedDocument::GetSourceRange Method</span></span>
<span data-ttu-id="4df69-103">Zwraca określony zakres osadzonego źródła do podanego buforu.</span><span class="sxs-lookup"><span data-stu-id="4df69-103">Returns the specified range of the embedded source into the given buffer.</span></span> <span data-ttu-id="4df69-104">Bufor musi być wystarczająco duży, aby pomieścić źródło.</span><span class="sxs-lookup"><span data-stu-id="4df69-104">The buffer must be large enough to hold the source.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4df69-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="4df69-105">Syntax</span></span>  
  
```cpp  
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
  
## <a name="parameters"></a><span data-ttu-id="4df69-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="4df69-106">Parameters</span></span>  
 `startLine`  
 <span data-ttu-id="4df69-107">podczas Wiersz początkowy w bieżącym dokumencie.</span><span class="sxs-lookup"><span data-stu-id="4df69-107">[in] The starting line in the current document.</span></span>  
  
 `startColumn`  
 <span data-ttu-id="4df69-108">podczas Kolumna początkowa w bieżącym dokumencie.</span><span class="sxs-lookup"><span data-stu-id="4df69-108">[in] The starting column in the current document.</span></span>  
  
 `endLine`  
 <span data-ttu-id="4df69-109">podczas Ostatni wiersz w bieżącym dokumencie.</span><span class="sxs-lookup"><span data-stu-id="4df69-109">[in] The final line in the current document.</span></span>  
  
 `endColumn`  
 <span data-ttu-id="4df69-110">podczas Końcowa kolumna w bieżącym dokumencie.</span><span class="sxs-lookup"><span data-stu-id="4df69-110">[in] The final column in the current document.</span></span>  
  
 `cSourceBytes`  
 <span data-ttu-id="4df69-111">podczas Rozmiar źródła w bajtach.</span><span class="sxs-lookup"><span data-stu-id="4df69-111">[in] The size of the source, in bytes.</span></span>  
  
 `pcSourceBytes`  
 <span data-ttu-id="4df69-112">określoną Wskaźnik do zmiennej, która otrzymuje rozmiar źródła.</span><span class="sxs-lookup"><span data-stu-id="4df69-112">[out] A pointer to a variable that receives the source size.</span></span>  
  
 `source`  
 <span data-ttu-id="4df69-113">określoną Rozmiar i długość określonego zakresu dokumentu źródłowego w bajtach.</span><span class="sxs-lookup"><span data-stu-id="4df69-113">[out] The size and length of the specified range of the source document, in bytes.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="4df69-114">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="4df69-114">Return Value</span></span>  
 <span data-ttu-id="4df69-115">S_OK, jeśli metoda zakończy się pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="4df69-115">S_OK if the method succeeds.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4df69-116">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="4df69-116">See also</span></span>

- [<span data-ttu-id="4df69-117">ISymUnmanagedDocument, interfejs</span><span class="sxs-lookup"><span data-stu-id="4df69-117">ISymUnmanagedDocument Interface</span></span>](isymunmanageddocument-interface.md)
