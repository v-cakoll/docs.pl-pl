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
ms.openlocfilehash: f6b1e253fb7bf1a97f44e1eb05676fc356af9837
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59123711"
---
# <a name="isymunmanagedmethodgetsequencepoints-method"></a><span data-ttu-id="decfb-102">ISymUnmanagedMethod::GetSequencePoints — Metoda</span><span class="sxs-lookup"><span data-stu-id="decfb-102">ISymUnmanagedMethod::GetSequencePoints Method</span></span>
<span data-ttu-id="decfb-103">Pobiera wszystkie punkty sekwencji w ramach tej metody.</span><span class="sxs-lookup"><span data-stu-id="decfb-103">Gets all the sequence points within this method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="decfb-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="decfb-104">Syntax</span></span>  
  
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
  
## <a name="parameters"></a><span data-ttu-id="decfb-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="decfb-105">Parameters</span></span>  
 `cPoints`  
 <span data-ttu-id="decfb-106">[in] A `ULONG32` wielkości, która otrzymuje `offsets`, `documents`, `lines`, `columns`, `endLines`, i `endColumns` tablic.</span><span class="sxs-lookup"><span data-stu-id="decfb-106">[in] A `ULONG32` that receives the size of the `offsets`, `documents`, `lines`, `columns`, `endLines`, and `endColumns` arrays.</span></span>  
  
 `pcPoints`  
 <span data-ttu-id="decfb-107">[out] Wskaźnik do `ULONG32` odbierająca długość buforu, muszą zawierać punktów sekwencji.</span><span class="sxs-lookup"><span data-stu-id="decfb-107">[out] A pointer to a `ULONG32` that receives the length of the buffer required to contain the sequence points.</span></span>  
  
 `offsets`  
 <span data-ttu-id="decfb-108">[in] Tablica, w którym będą przechowywane przez firmę Microsoft intermediate language (MSIL) powoduje przesunięcie od początku metody punktów sekwencji.</span><span class="sxs-lookup"><span data-stu-id="decfb-108">[in] An array in which to store the Microsoft intermediate language (MSIL) offsets from the beginning of the method for the sequence points.</span></span>  
  
 `documents`  
 <span data-ttu-id="decfb-109">[in] Tablica do przechowywania dokumentów, w których znajdują się punkty sekwencji.</span><span class="sxs-lookup"><span data-stu-id="decfb-109">[in] An array in which to store the documents in which the sequence points are located.</span></span>  
  
 `lines`  
 <span data-ttu-id="decfb-110">[in] Tablica do przechowywania wierszy w dokumentach, w których znajdują się punkty sekwencji.</span><span class="sxs-lookup"><span data-stu-id="decfb-110">[in] An array in which to store the lines in the documents at which the sequence points are located.</span></span>  
  
 `columns`  
 <span data-ttu-id="decfb-111">[in] Tablica, w którym będą przechowywane w kolumnach w dokumentach, w których znajdują się punkty sekwencji.</span><span class="sxs-lookup"><span data-stu-id="decfb-111">[in] An array in which to store the columns in the documents at which the sequence points are located.</span></span>  
  
 `endLines`  
 <span data-ttu-id="decfb-112">[in] Tablica wiersze w dokumentach, w których sekwencji punktów końcowych.</span><span class="sxs-lookup"><span data-stu-id="decfb-112">[in] The array of lines in the documents at which the sequence points end.</span></span>  
  
 `endColumns`  
 <span data-ttu-id="decfb-113">[in] Tablica kolumn w dokumentach, w których sekwencji punktów końcowych.</span><span class="sxs-lookup"><span data-stu-id="decfb-113">[in] The array of columns in the documents at which the sequence points end.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="decfb-114">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="decfb-114">Return Value</span></span>  
 <span data-ttu-id="decfb-115">S_OK, jeśli metoda się powiedzie; w przeciwnym razie E_FAIL lub innego kodu błędu.</span><span class="sxs-lookup"><span data-stu-id="decfb-115">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="decfb-116">Wymagania</span><span class="sxs-lookup"><span data-stu-id="decfb-116">Requirements</span></span>  
 <span data-ttu-id="decfb-117">**Nagłówek:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="decfb-117">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="decfb-118">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="decfb-118">See also</span></span>

- [<span data-ttu-id="decfb-119">ISymUnmanagedMethod — Interfejs</span><span class="sxs-lookup"><span data-stu-id="decfb-119">ISymUnmanagedMethod Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedmethod-interface.md)
