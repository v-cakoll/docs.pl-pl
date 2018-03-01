---
title: "ISymUnmanagedMethod::GetRanges — Metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- ISymUnmanagedMethod.GetRanges
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedMethod::GetRanges
helpviewer_keywords:
- ISymUnmanagedMethod::GetRanges method [.NET Framework debugging]
- GetRanges method [.NET Framework debugging]
ms.assetid: a85283d8-379c-417a-9736-ddeeef9bcf50
topic_type:
- apiref
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 1e17b411e39e522006092d79380566484f8fab67
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="isymunmanagedmethodgetranges-method"></a><span data-ttu-id="19370-102">ISymUnmanagedMethod::GetRanges — Metoda</span><span class="sxs-lookup"><span data-stu-id="19370-102">ISymUnmanagedMethod::GetRanges Method</span></span>
<span data-ttu-id="19370-103">Podanej pozycji w dokumencie zwraca tablicę początkową i końcową pary przesunięcia, które odpowiadają zakresom język pośredni firmy Microsoft (MSIL), który obejmuje pozycję w ramach tej metody.</span><span class="sxs-lookup"><span data-stu-id="19370-103">Given a position in a document, returns an array of start and end offset pairs that correspond to the ranges of Microsoft intermediate language (MSIL) that the position covers within this method.</span></span> <span data-ttu-id="19370-104">Tablica jest tablicą liczb całkowitych i ma format [rozpoczęcia, zakończenia, start, zakończenie].</span><span class="sxs-lookup"><span data-stu-id="19370-104">The array is an array of integers and has the format [start, end, start, end].</span></span> <span data-ttu-id="19370-105">Określona liczba par zakres jest długość tablicy podzielona przez 2.</span><span class="sxs-lookup"><span data-stu-id="19370-105">The number of range pairs is the length of the array divided by 2.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="19370-106">Składnia</span><span class="sxs-lookup"><span data-stu-id="19370-106">Syntax</span></span>  
  
```  
HRESULT GetRanges(  
    [in]  ISymUnmanagedDocument* document,  
    [in]  ULONG32                line,  
    [in]  ULONG32                column,  
    [in]  ULONG32                cRanges,  
    [out] ULONG32                *pcRanges,  
    [out, size_is(cRanges),  
        length_is(*pcRanges)] ULONG32 ranges[]);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="19370-107">Parametry</span><span class="sxs-lookup"><span data-stu-id="19370-107">Parameters</span></span>  
 `document`  
 <span data-ttu-id="19370-108">[in] Dokument, dla którego wnioskuje się przesunięcie.</span><span class="sxs-lookup"><span data-stu-id="19370-108">[in] The document for which the offset is requested.</span></span>  
  
 `line`  
 <span data-ttu-id="19370-109">[in] Wiersz dokumentu odpowiadający zakresów.</span><span class="sxs-lookup"><span data-stu-id="19370-109">[in] The document line corresponding to the ranges.</span></span>  
  
 `column`  
 <span data-ttu-id="19370-110">[in] Kolumna dokumentu odpowiadający zakresów.</span><span class="sxs-lookup"><span data-stu-id="19370-110">[in] The document column corresponding to the ranges.</span></span>  
  
 `cRanges`  
 <span data-ttu-id="19370-111">[in] Rozmiar `ranges` tablicy.</span><span class="sxs-lookup"><span data-stu-id="19370-111">[in] The size of the `ranges` array.</span></span>  
  
 `pcRanges`  
 <span data-ttu-id="19370-112">[out] Wskaźnik do `ULONG32` odbierająca rozmiar buforu, muszą zawierać zakresów.</span><span class="sxs-lookup"><span data-stu-id="19370-112">[out] A pointer to a `ULONG32` that receives the size of the buffer required to contain the ranges.</span></span>  
  
 `ranges`  
 <span data-ttu-id="19370-113">[out] Wskaźnik do buforu, który odbiera zakresów.</span><span class="sxs-lookup"><span data-stu-id="19370-113">[out] A pointer to the buffer that receives the ranges.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="19370-114">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="19370-114">Return Value</span></span>  
 <span data-ttu-id="19370-115">Wartość S_OK, jeśli metoda zakończy się pomyślnie; w przeciwnym razie E_FAIL lub inny kod błędu.</span><span class="sxs-lookup"><span data-stu-id="19370-115">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="19370-116">Wymagania</span><span class="sxs-lookup"><span data-stu-id="19370-116">Requirements</span></span>  
 <span data-ttu-id="19370-117">**Nagłówek:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="19370-117">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="19370-118">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="19370-118">See Also</span></span>  
 [<span data-ttu-id="19370-119">ISymUnmanagedMethod, interfejs</span><span class="sxs-lookup"><span data-stu-id="19370-119">ISymUnmanagedMethod Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedmethod-interface.md)
