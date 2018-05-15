---
title: ISymUnmanagedMethod::GetSequencePoints — Metoda
ms.date: 03/30/2017
api_name:
- ISymUnmanagedMethod.GetSequencePoints
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedMethod::GetSequencePoints
helpviewer_keywords:
- ISymUnmanagedMethod::GetSequencePoints method [.NET Framework debugging]
- GetSequencePoints method [.NET Framework debugging]
ms.assetid: f909ac48-3d8f-49fb-a369-e3d9959151cd
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: c9a35f35d7aea34c0ef08c30415fde75fe71e645
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="isymunmanagedmethodgetsequencepoints-method"></a><span data-ttu-id="d2d2b-102">ISymUnmanagedMethod::GetSequencePoints — Metoda</span><span class="sxs-lookup"><span data-stu-id="d2d2b-102">ISymUnmanagedMethod::GetSequencePoints Method</span></span>
<span data-ttu-id="d2d2b-103">Pobiera wszystkie punkty sekwencji w ramach tej metody.</span><span class="sxs-lookup"><span data-stu-id="d2d2b-103">Gets all the sequence points within this method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d2d2b-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="d2d2b-104">Syntax</span></span>  
  
```  
HRESULT GetSequencePoints(  
    [in]  ULONG32  cPoints,  
    [out] ULONG32  *pcPoints,  
    [in, size_is(cPoints)] ULONG32  offsets[],  
    [in, size_is(cPoints)] ISymUnmanagedDocument* documents[],  
    [in, size_is(cPoints)] ULONG32  lines[],  
    [in, size_is(cPoints)] ULONG32  columns[],  
    [in, size_is(cPoints)] ULONG32  endLines[],  
    [in, size_is(cPoints)] ULONG32  endColumns[]);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="d2d2b-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="d2d2b-105">Parameters</span></span>  
 `cPoints`  
 <span data-ttu-id="d2d2b-106">[in] A `ULONG32` odbierająca rozmiar `offsets`, `documents`, `lines`, `columns`, `endLines`, i `endColumns` tablic.</span><span class="sxs-lookup"><span data-stu-id="d2d2b-106">[in] A `ULONG32` that receives the size of the `offsets`, `documents`, `lines`, `columns`, `endLines`, and `endColumns` arrays.</span></span>  
  
 `pcPoints`  
 <span data-ttu-id="d2d2b-107">[out] Wskaźnik do `ULONG32` odbierająca długość buforu, muszą zawierać punkty sekwencji.</span><span class="sxs-lookup"><span data-stu-id="d2d2b-107">[out] A pointer to a `ULONG32` that receives the length of the buffer required to contain the sequence points.</span></span>  
  
 `offsets`  
 <span data-ttu-id="d2d2b-108">[in] Tablica do przechowywania Microsoft pośredniego language (MSIL) powoduje przesunięcie od początku metodę punkty sekwencji.</span><span class="sxs-lookup"><span data-stu-id="d2d2b-108">[in] An array in which to store the Microsoft intermediate language (MSIL) offsets from the beginning of the method for the sequence points.</span></span>  
  
 `documents`  
 <span data-ttu-id="d2d2b-109">[in] Tablica do przechowywania dokumentów, w których znajdują się punkty sekwencji.</span><span class="sxs-lookup"><span data-stu-id="d2d2b-109">[in] An array in which to store the documents in which the sequence points are located.</span></span>  
  
 `lines`  
 <span data-ttu-id="d2d2b-110">[in] Tablica do przechowywania dokumentów, w których znajdują się punkty sekwencji wierszy.</span><span class="sxs-lookup"><span data-stu-id="d2d2b-110">[in] An array in which to store the lines in the documents at which the sequence points are located.</span></span>  
  
 `columns`  
 <span data-ttu-id="d2d2b-111">[in] Tablica do przechowywania kolumny w dokumentach, w których znajdują się punkty sekwencji.</span><span class="sxs-lookup"><span data-stu-id="d2d2b-111">[in] An array in which to store the columns in the documents at which the sequence points are located.</span></span>  
  
 `endLines`  
 <span data-ttu-id="d2d2b-112">[in] Tablica wiersze w dokumentach, w których sekwencja punktów końcowych.</span><span class="sxs-lookup"><span data-stu-id="d2d2b-112">[in] The array of lines in the documents at which the sequence points end.</span></span>  
  
 `endColumns`  
 <span data-ttu-id="d2d2b-113">[in] Tablica kolumn w dokumentach, w których sekwencja punktów końcowych.</span><span class="sxs-lookup"><span data-stu-id="d2d2b-113">[in] The array of columns in the documents at which the sequence points end.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="d2d2b-114">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="d2d2b-114">Return Value</span></span>  
 <span data-ttu-id="d2d2b-115">Wartość S_OK, jeśli metoda zakończy się pomyślnie; w przeciwnym razie E_FAIL lub inny kod błędu.</span><span class="sxs-lookup"><span data-stu-id="d2d2b-115">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d2d2b-116">Wymagania</span><span class="sxs-lookup"><span data-stu-id="d2d2b-116">Requirements</span></span>  
 <span data-ttu-id="d2d2b-117">**Header:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="d2d2b-117">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d2d2b-118">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="d2d2b-118">See Also</span></span>  
 [<span data-ttu-id="d2d2b-119">ISymUnmanagedMethod, interfejs</span><span class="sxs-lookup"><span data-stu-id="d2d2b-119">ISymUnmanagedMethod Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedmethod-interface.md)
