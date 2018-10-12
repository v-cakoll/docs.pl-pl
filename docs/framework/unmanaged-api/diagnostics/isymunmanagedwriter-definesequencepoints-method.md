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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 5825f0425947f109ed834879684357fef7b70959
ms.sourcegitcommit: 15d99019aea4a5c3c91ddc9ba23692284a7f61f3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/12/2018
ms.locfileid: "49123777"
---
# <a name="isymunmanagedwriterdefinesequencepoints-method"></a><span data-ttu-id="9e6b6-102">ISymUnmanagedWriter::DefineSequencePoints — Metoda</span><span class="sxs-lookup"><span data-stu-id="9e6b6-102">ISymUnmanagedWriter::DefineSequencePoints Method</span></span>
<span data-ttu-id="9e6b6-103">Definiuje grupę punktów sekwencji w bieżącej metodzie.</span><span class="sxs-lookup"><span data-stu-id="9e6b6-103">Defines a group of sequence points within the current method.</span></span> <span data-ttu-id="9e6b6-104">Każda linia początkowa i kolumnę początkową definiują rozpoczęcia instrukcji wewnątrz metody.</span><span class="sxs-lookup"><span data-stu-id="9e6b6-104">Each starting line and starting column define the start of a statement within a method.</span></span> <span data-ttu-id="9e6b6-105">Zakończenie każdego wiersza i zakończenie kolumnę zdefiniuj końca instrukcji wewnątrz metody.</span><span class="sxs-lookup"><span data-stu-id="9e6b6-105">Each ending line and ending column define the end of a statement within a method.</span></span> <span data-ttu-id="9e6b6-106">Tablice powinny być sortowane rosnąco przesunięcia.</span><span class="sxs-lookup"><span data-stu-id="9e6b6-106">The arrays should be sorted in increasing order of offsets.</span></span> <span data-ttu-id="9e6b6-107">Przesunięcie zawsze jest mierzony od początku metody, w bajtach.</span><span class="sxs-lookup"><span data-stu-id="9e6b6-107">The offset is always measured from the start of the method, in bytes.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9e6b6-108">Składnia</span><span class="sxs-lookup"><span data-stu-id="9e6b6-108">Syntax</span></span>  
  
```  
HRESULT DefineSequencePoints(  
    [in] ISymUnmanagedDocumentWriter*  document,  
    [in] ULONG32 spCount,  
    [in, size_is(spCount)] ULONG32     offsets[],  
    [in, size_is(spCount)] ULONG32     lines[],  
    [in, size_is(spCount)] ULONG32     columns[],  
    [in, size_is(spCount)] ULONG32     endLines[],  
    [in, size_is(spCount)] ULONG32     endColumns[]);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="9e6b6-109">Parametry</span><span class="sxs-lookup"><span data-stu-id="9e6b6-109">Parameters</span></span>  
 `document`  
 <span data-ttu-id="9e6b6-110">[in] Obiekt dokumentu, dla której są zdefiniowane punktów sekwencji.</span><span class="sxs-lookup"><span data-stu-id="9e6b6-110">[in] The document object for which the sequence points are being defined.</span></span>  
  
 `spCount`  
 <span data-ttu-id="9e6b6-111">[in] A `ULONG32` oznacza to rozmiar wszystkich `offsets`, `lines`, `columns`, `endLines`, i `endColumns` buforów.</span><span class="sxs-lookup"><span data-stu-id="9e6b6-111">[in] A `ULONG32` that indicates the size of each of the `offsets`, `lines`, `columns`, `endLines`, and `endColumns` buffers.</span></span>  
  
 `offsets`  
 <span data-ttu-id="9e6b6-112">[in] Przesunięcie punktów sekwencji jest mierzony od początku metody.</span><span class="sxs-lookup"><span data-stu-id="9e6b6-112">[in] The offset of the sequence points measured from the beginning of the method.</span></span>  
  
 `lines`  
 <span data-ttu-id="9e6b6-113">[in] Linia początkowa liczby punktów sekwencji.</span><span class="sxs-lookup"><span data-stu-id="9e6b6-113">[in] The starting line numbers of the sequence points.</span></span>  
  
 `columns`  
 <span data-ttu-id="9e6b6-114">[in] Począwszy od liczby kolumn punktów sekwencji.</span><span class="sxs-lookup"><span data-stu-id="9e6b6-114">[in] The starting column numbers of the sequence points.</span></span>  
  
 `endLines`  
 <span data-ttu-id="9e6b6-115">[in] Końcowy numery wierszy punktów sekwencji.</span><span class="sxs-lookup"><span data-stu-id="9e6b6-115">[in] The ending line numbers of the sequence points.</span></span> <span data-ttu-id="9e6b6-116">Ten parametr jest opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="9e6b6-116">This parameter is optional.</span></span>  
  
 `endColumns`  
 <span data-ttu-id="9e6b6-117">[in] Końcowej kolumny liczby punktów sekwencji.</span><span class="sxs-lookup"><span data-stu-id="9e6b6-117">[in] The ending column numbers of the sequence points.</span></span> <span data-ttu-id="9e6b6-118">Ten parametr jest opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="9e6b6-118">This parameter is optional.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="9e6b6-119">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="9e6b6-119">Return Value</span></span>  
 <span data-ttu-id="9e6b6-120">S_OK, jeśli metoda się powiedzie; w przeciwnym razie E_FAIL lub innego kodu błędu.</span><span class="sxs-lookup"><span data-stu-id="9e6b6-120">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9e6b6-121">Wymagania</span><span class="sxs-lookup"><span data-stu-id="9e6b6-121">Requirements</span></span>  
 <span data-ttu-id="9e6b6-122">**Header:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="9e6b6-122">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9e6b6-123">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="9e6b6-123">See Also</span></span>  
 [<span data-ttu-id="9e6b6-124">ISymUnmanagedWriter, interfejs</span><span class="sxs-lookup"><span data-stu-id="9e6b6-124">ISymUnmanagedWriter Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-interface.md)
