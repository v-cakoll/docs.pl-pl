---
title: ISymUnmanagedWriter::DefineSequencePoints — Metoda
ms.date: 03/30/2017
api_name:
- ISymUnmanagedWriter.DefineSequencePoints
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedWriter::DefineSequencePoints
helpviewer_keywords:
- DefineSequencePoints method [.NET Framework debugging]
- ISymUnmanagedWriter::DefineSequencePoints method [.NET Framework debugging]
ms.assetid: 64202baf-be6b-40ba-8162-8cc6c0c9b8e1
topic_type:
- apiref
ms.openlocfilehash: 8889c412f414f38d1d18d33ec297e82fd052280d
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/19/2020
ms.locfileid: "83614802"
---
# <a name="isymunmanagedwriterdefinesequencepoints-method"></a><span data-ttu-id="5fe6c-102">ISymUnmanagedWriter::DefineSequencePoints — Metoda</span><span class="sxs-lookup"><span data-stu-id="5fe6c-102">ISymUnmanagedWriter::DefineSequencePoints Method</span></span>
<span data-ttu-id="5fe6c-103">Definiuje grupę punktów sekwencji w bieżącej metodzie.</span><span class="sxs-lookup"><span data-stu-id="5fe6c-103">Defines a group of sequence points within the current method.</span></span> <span data-ttu-id="5fe6c-104">Każda linia początkowa i początkowa kolumna definiują początek instrukcji w ramach metody.</span><span class="sxs-lookup"><span data-stu-id="5fe6c-104">Each starting line and starting column define the start of a statement within a method.</span></span> <span data-ttu-id="5fe6c-105">Każdy wiersz końcowy i kolumna końcowa definiują koniec instrukcji w ramach metody.</span><span class="sxs-lookup"><span data-stu-id="5fe6c-105">Each ending line and ending column define the end of a statement within a method.</span></span> <span data-ttu-id="5fe6c-106">Tablice powinny być sortowane w kolejności rosnącej.</span><span class="sxs-lookup"><span data-stu-id="5fe6c-106">The arrays should be sorted in increasing order of offsets.</span></span> <span data-ttu-id="5fe6c-107">Przesunięcie jest zawsze mierzone od początku metody, w bajtach.</span><span class="sxs-lookup"><span data-stu-id="5fe6c-107">The offset is always measured from the start of the method, in bytes.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5fe6c-108">Składnia</span><span class="sxs-lookup"><span data-stu-id="5fe6c-108">Syntax</span></span>  
  
```cpp  
HRESULT DefineSequencePoints(  
    [in] ISymUnmanagedDocumentWriter*  document,  
    [in] ULONG32 spCount,  
    [in, size_is(spCount)] ULONG32     offsets[],  
    [in, size_is(spCount)] ULONG32     lines[],  
    [in, size_is(spCount)] ULONG32     columns[],  
    [in, size_is(spCount)] ULONG32     endLines[],  
    [in, size_is(spCount)] ULONG32     endColumns[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="5fe6c-109">Parametry</span><span class="sxs-lookup"><span data-stu-id="5fe6c-109">Parameters</span></span>  
 `document`  
 <span data-ttu-id="5fe6c-110">podczas Obiekt dokumentu, dla którego są definiowane punkty sekwencji.</span><span class="sxs-lookup"><span data-stu-id="5fe6c-110">[in] The document object for which the sequence points are being defined.</span></span>  
  
 `spCount`  
 <span data-ttu-id="5fe6c-111">podczas A, `ULONG32` który wskazuje rozmiar każdego z `offsets` `lines` buforów,, `columns` , `endLines` i `endColumns` .</span><span class="sxs-lookup"><span data-stu-id="5fe6c-111">[in] A `ULONG32` that indicates the size of each of the `offsets`, `lines`, `columns`, `endLines`, and `endColumns` buffers.</span></span>  
  
 `offsets`  
 <span data-ttu-id="5fe6c-112">podczas Przesunięcie punktów sekwencji mierzone od początku metody.</span><span class="sxs-lookup"><span data-stu-id="5fe6c-112">[in] The offset of the sequence points measured from the beginning of the method.</span></span>  
  
 `lines`  
 <span data-ttu-id="5fe6c-113">podczas Numery wierszy początkowych punktów sekwencji.</span><span class="sxs-lookup"><span data-stu-id="5fe6c-113">[in] The starting line numbers of the sequence points.</span></span>  
  
 `columns`  
 <span data-ttu-id="5fe6c-114">podczas Numery kolumn początkowych punktów sekwencji.</span><span class="sxs-lookup"><span data-stu-id="5fe6c-114">[in] The starting column numbers of the sequence points.</span></span>  
  
 `endLines`  
 <span data-ttu-id="5fe6c-115">podczas Numery wierszy zakończenia punktów sekwencji.</span><span class="sxs-lookup"><span data-stu-id="5fe6c-115">[in] The ending line numbers of the sequence points.</span></span> <span data-ttu-id="5fe6c-116">Ten parametr jest opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="5fe6c-116">This parameter is optional.</span></span>  
  
 `endColumns`  
 <span data-ttu-id="5fe6c-117">podczas Numery kolumn końcowych punktów sekwencji.</span><span class="sxs-lookup"><span data-stu-id="5fe6c-117">[in] The ending column numbers of the sequence points.</span></span> <span data-ttu-id="5fe6c-118">Ten parametr jest opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="5fe6c-118">This parameter is optional.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="5fe6c-119">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="5fe6c-119">Return Value</span></span>  
 <span data-ttu-id="5fe6c-120">S_OK, jeśli metoda się powiedzie; w przeciwnym razie E_FAIL lub inny kod błędu.</span><span class="sxs-lookup"><span data-stu-id="5fe6c-120">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5fe6c-121">Wymagania</span><span class="sxs-lookup"><span data-stu-id="5fe6c-121">Requirements</span></span>  
 <span data-ttu-id="5fe6c-122">**Nagłówek:** CorSym. idl, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="5fe6c-122">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5fe6c-123">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="5fe6c-123">See also</span></span>

- [<span data-ttu-id="5fe6c-124">ISymUnmanagedWriter — Interfejs</span><span class="sxs-lookup"><span data-stu-id="5fe6c-124">ISymUnmanagedWriter Interface</span></span>](isymunmanagedwriter-interface.md)
