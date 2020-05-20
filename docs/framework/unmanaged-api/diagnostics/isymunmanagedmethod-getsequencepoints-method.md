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
ms.openlocfilehash: 451cfecde7e14fad9d3fed3367112e1fb59796e5
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/19/2020
ms.locfileid: "83615148"
---
# <a name="isymunmanagedmethodgetsequencepoints-method"></a><span data-ttu-id="bca3f-102">ISymUnmanagedMethod::GetSequencePoints — Metoda</span><span class="sxs-lookup"><span data-stu-id="bca3f-102">ISymUnmanagedMethod::GetSequencePoints Method</span></span>
<span data-ttu-id="bca3f-103">Pobiera wszystkie punkty sekwencji w tej metodzie.</span><span class="sxs-lookup"><span data-stu-id="bca3f-103">Gets all the sequence points within this method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bca3f-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="bca3f-104">Syntax</span></span>  
  
```cpp  
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
  
## <a name="parameters"></a><span data-ttu-id="bca3f-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="bca3f-105">Parameters</span></span>  
 `cPoints`  
 <span data-ttu-id="bca3f-106">podczas A, `ULONG32` który otrzymuje wielkość tablic,,,, `offsets` `documents` `lines` `columns` `endLines` i `endColumns` .</span><span class="sxs-lookup"><span data-stu-id="bca3f-106">[in] A `ULONG32` that receives the size of the `offsets`, `documents`, `lines`, `columns`, `endLines`, and `endColumns` arrays.</span></span>  
  
 `pcPoints`  
 <span data-ttu-id="bca3f-107">określoną Wskaźnik do obiektu `ULONG32` , który otrzymuje długość buforu wymaganego do zawierania punktów sekwencji.</span><span class="sxs-lookup"><span data-stu-id="bca3f-107">[out] A pointer to a `ULONG32` that receives the length of the buffer required to contain the sequence points.</span></span>  
  
 `offsets`  
 <span data-ttu-id="bca3f-108">podczas Tablica, w której mają być przechowywane przesunięcia języka pośredniego firmy Microsoft (MSIL) od początku metody dla punktów sekwencji.</span><span class="sxs-lookup"><span data-stu-id="bca3f-108">[in] An array in which to store the Microsoft intermediate language (MSIL) offsets from the beginning of the method for the sequence points.</span></span>  
  
 `documents`  
 <span data-ttu-id="bca3f-109">podczas Tablica, w której mają być przechowywane dokumenty, w których znajdują się punkty sekwencji.</span><span class="sxs-lookup"><span data-stu-id="bca3f-109">[in] An array in which to store the documents in which the sequence points are located.</span></span>  
  
 `lines`  
 <span data-ttu-id="bca3f-110">podczas Tablica, w której mają być przechowywane wiersze w dokumentach, w których znajdują się punkty sekwencji.</span><span class="sxs-lookup"><span data-stu-id="bca3f-110">[in] An array in which to store the lines in the documents at which the sequence points are located.</span></span>  
  
 `columns`  
 <span data-ttu-id="bca3f-111">podczas Tablica, w której mają być przechowywane kolumny w dokumentach, w których znajdują się punkty sekwencji.</span><span class="sxs-lookup"><span data-stu-id="bca3f-111">[in] An array in which to store the columns in the documents at which the sequence points are located.</span></span>  
  
 `endLines`  
 <span data-ttu-id="bca3f-112">podczas Tablica wierszy w dokumentach, w których kończy się punkty sekwencji.</span><span class="sxs-lookup"><span data-stu-id="bca3f-112">[in] The array of lines in the documents at which the sequence points end.</span></span>  
  
 `endColumns`  
 <span data-ttu-id="bca3f-113">podczas Tablica kolumn w dokumentach, w których kończy się punkty sekwencji.</span><span class="sxs-lookup"><span data-stu-id="bca3f-113">[in] The array of columns in the documents at which the sequence points end.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="bca3f-114">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="bca3f-114">Return Value</span></span>  
 <span data-ttu-id="bca3f-115">S_OK, jeśli metoda się powiedzie; w przeciwnym razie E_FAIL lub inny kod błędu.</span><span class="sxs-lookup"><span data-stu-id="bca3f-115">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="bca3f-116">Wymagania</span><span class="sxs-lookup"><span data-stu-id="bca3f-116">Requirements</span></span>  
 <span data-ttu-id="bca3f-117">**Nagłówek:** CorSym. idl, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="bca3f-117">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bca3f-118">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="bca3f-118">See also</span></span>

- [<span data-ttu-id="bca3f-119">ISymUnmanagedMethod — Interfejs</span><span class="sxs-lookup"><span data-stu-id="bca3f-119">ISymUnmanagedMethod Interface</span></span>](isymunmanagedmethod-interface.md)
