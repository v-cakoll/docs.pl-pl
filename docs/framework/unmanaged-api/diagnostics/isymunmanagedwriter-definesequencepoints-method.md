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
ms.openlocfilehash: 63ba108bc234e566450bb019afc63acb4e75ad1f
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/23/2019
ms.locfileid: "74427985"
---
# <a name="isymunmanagedwriterdefinesequencepoints-method"></a><span data-ttu-id="e831a-102">ISymUnmanagedWriter::DefineSequencePoints — Metoda</span><span class="sxs-lookup"><span data-stu-id="e831a-102">ISymUnmanagedWriter::DefineSequencePoints Method</span></span>
<span data-ttu-id="e831a-103">Definiuje grupę punktów sekwencji w bieżącej metodzie.</span><span class="sxs-lookup"><span data-stu-id="e831a-103">Defines a group of sequence points within the current method.</span></span> <span data-ttu-id="e831a-104">Każda linia początkowa i początkowa kolumna definiują początek instrukcji w ramach metody.</span><span class="sxs-lookup"><span data-stu-id="e831a-104">Each starting line and starting column define the start of a statement within a method.</span></span> <span data-ttu-id="e831a-105">Każdy wiersz końcowy i kolumna końcowa definiują koniec instrukcji w ramach metody.</span><span class="sxs-lookup"><span data-stu-id="e831a-105">Each ending line and ending column define the end of a statement within a method.</span></span> <span data-ttu-id="e831a-106">Tablice powinny być sortowane w kolejności rosnącej.</span><span class="sxs-lookup"><span data-stu-id="e831a-106">The arrays should be sorted in increasing order of offsets.</span></span> <span data-ttu-id="e831a-107">Przesunięcie jest zawsze mierzone od początku metody, w bajtach.</span><span class="sxs-lookup"><span data-stu-id="e831a-107">The offset is always measured from the start of the method, in bytes.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e831a-108">Składnia</span><span class="sxs-lookup"><span data-stu-id="e831a-108">Syntax</span></span>  
  
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
  
## <a name="parameters"></a><span data-ttu-id="e831a-109">Parametry</span><span class="sxs-lookup"><span data-stu-id="e831a-109">Parameters</span></span>  
 `document`  
 <span data-ttu-id="e831a-110">podczas Obiekt dokumentu, dla którego są definiowane punkty sekwencji.</span><span class="sxs-lookup"><span data-stu-id="e831a-110">[in] The document object for which the sequence points are being defined.</span></span>  
  
 `spCount`  
 <span data-ttu-id="e831a-111">podczas `ULONG32`, który wskazuje rozmiar każdego z `offsets`, `lines`, `columns`, `endLines`i `endColumns` buforów.</span><span class="sxs-lookup"><span data-stu-id="e831a-111">[in] A `ULONG32` that indicates the size of each of the `offsets`, `lines`, `columns`, `endLines`, and `endColumns` buffers.</span></span>  
  
 `offsets`  
 <span data-ttu-id="e831a-112">podczas Przesunięcie punktów sekwencji mierzone od początku metody.</span><span class="sxs-lookup"><span data-stu-id="e831a-112">[in] The offset of the sequence points measured from the beginning of the method.</span></span>  
  
 `lines`  
 <span data-ttu-id="e831a-113">podczas Numery wierszy początkowych punktów sekwencji.</span><span class="sxs-lookup"><span data-stu-id="e831a-113">[in] The starting line numbers of the sequence points.</span></span>  
  
 `columns`  
 <span data-ttu-id="e831a-114">podczas Numery kolumn początkowych punktów sekwencji.</span><span class="sxs-lookup"><span data-stu-id="e831a-114">[in] The starting column numbers of the sequence points.</span></span>  
  
 `endLines`  
 <span data-ttu-id="e831a-115">podczas Numery wierszy zakończenia punktów sekwencji.</span><span class="sxs-lookup"><span data-stu-id="e831a-115">[in] The ending line numbers of the sequence points.</span></span> <span data-ttu-id="e831a-116">Ten parametr jest opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="e831a-116">This parameter is optional.</span></span>  
  
 `endColumns`  
 <span data-ttu-id="e831a-117">podczas Numery kolumn końcowych punktów sekwencji.</span><span class="sxs-lookup"><span data-stu-id="e831a-117">[in] The ending column numbers of the sequence points.</span></span> <span data-ttu-id="e831a-118">Ten parametr jest opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="e831a-118">This parameter is optional.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="e831a-119">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="e831a-119">Return Value</span></span>  
 <span data-ttu-id="e831a-120">S_OK, jeśli metoda się powiedzie; w przeciwnym razie E_FAIL lub inny kod błędu.</span><span class="sxs-lookup"><span data-stu-id="e831a-120">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e831a-121">Wymagania</span><span class="sxs-lookup"><span data-stu-id="e831a-121">Requirements</span></span>  
 <span data-ttu-id="e831a-122">**Nagłówek:** CorSym. idl, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="e831a-122">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e831a-123">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="e831a-123">See also</span></span>

- [<span data-ttu-id="e831a-124">ISymUnmanagedWriter, interfejs</span><span class="sxs-lookup"><span data-stu-id="e831a-124">ISymUnmanagedWriter Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-interface.md)
