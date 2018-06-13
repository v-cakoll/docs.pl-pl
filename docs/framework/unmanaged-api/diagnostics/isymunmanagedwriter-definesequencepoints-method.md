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
ms.openlocfilehash: 1dc87b201638bab974c59722a69300977b14cf08
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33426939"
---
# <a name="isymunmanagedwriterdefinesequencepoints-method"></a><span data-ttu-id="afd03-102">ISymUnmanagedWriter::DefineSequencePoints — Metoda</span><span class="sxs-lookup"><span data-stu-id="afd03-102">ISymUnmanagedWriter::DefineSequencePoints Method</span></span>
<span data-ttu-id="afd03-103">Definiuje grupę punkty sekwencji w bieżącej metodzie.</span><span class="sxs-lookup"><span data-stu-id="afd03-103">Defines a group of sequence points within the current method.</span></span> <span data-ttu-id="afd03-104">Każdego wiersza początkowego i kolumna początkowa definiują rozpoczęcia instrukcji w metodzie.</span><span class="sxs-lookup"><span data-stu-id="afd03-104">Each starting line and starting column define the start of a statement within a method.</span></span> <span data-ttu-id="afd03-105">Każdy zakończenia wiersza i kończąc na kolumnie zdefiniuj końca instrukcji w metodzie.</span><span class="sxs-lookup"><span data-stu-id="afd03-105">Each ending line and ending column define the end of a statement within a method.</span></span> <span data-ttu-id="afd03-106">Tablice mają być sortowane w rosnącej kolejności przesunięcia.</span><span class="sxs-lookup"><span data-stu-id="afd03-106">The arrays should be sorted in increasing order of offsets.</span></span> <span data-ttu-id="afd03-107">Przesunięcie jest zawsze mierzona od początku metody, w bajtach.</span><span class="sxs-lookup"><span data-stu-id="afd03-107">The offset is always measured from the start of the method, in bytes.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="afd03-108">Składnia</span><span class="sxs-lookup"><span data-stu-id="afd03-108">Syntax</span></span>  
  
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
  
#### <a name="parameters"></a><span data-ttu-id="afd03-109">Parametry</span><span class="sxs-lookup"><span data-stu-id="afd03-109">Parameters</span></span>  
 `document`  
 <span data-ttu-id="afd03-110">[in] Obiekt dokumentu, dla której są zdefiniowane punkty sekwencji.</span><span class="sxs-lookup"><span data-stu-id="afd03-110">[in] The document object for which the sequence points are being defined.</span></span>  
  
 `spCount`  
 <span data-ttu-id="afd03-111">[in] A `ULONG32` czy wskazuje rozmiar poszczególnych `offsets`, `lines`, `columns`, `endLines`, i `endColumns` buforów.</span><span class="sxs-lookup"><span data-stu-id="afd03-111">[in] A `ULONG32` that that indicates the size of each of the `offsets`, `lines`, `columns`, `endLines`, and `endColumns` buffers.</span></span>  
  
 `offsets`  
 <span data-ttu-id="afd03-112">[in] Przesunięcie punkty sekwencji zmierzony od początku metody.</span><span class="sxs-lookup"><span data-stu-id="afd03-112">[in] The offset of the sequence points measured from the beginning of the method.</span></span>  
  
 `lines`  
 <span data-ttu-id="afd03-113">[in] Numery wiersza początkowego punkty sekwencji.</span><span class="sxs-lookup"><span data-stu-id="afd03-113">[in] The starting line numbers of the sequence points.</span></span>  
  
 `columns`  
 <span data-ttu-id="afd03-114">[in] Początkowy numery kolumn punkty sekwencji.</span><span class="sxs-lookup"><span data-stu-id="afd03-114">[in] The starting column numbers of the sequence points.</span></span>  
  
 `endLines`  
 <span data-ttu-id="afd03-115">[in] Końcowy numery wierszy punkty sekwencji.</span><span class="sxs-lookup"><span data-stu-id="afd03-115">[in] The ending line numbers of the sequence points.</span></span> <span data-ttu-id="afd03-116">Ten parametr jest opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="afd03-116">This parameter is optional.</span></span>  
  
 `endColumns`  
 <span data-ttu-id="afd03-117">[in] Końcowy numery kolumn punkty sekwencji.</span><span class="sxs-lookup"><span data-stu-id="afd03-117">[in] The ending column numbers of the sequence points.</span></span> <span data-ttu-id="afd03-118">Ten parametr jest opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="afd03-118">This parameter is optional.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="afd03-119">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="afd03-119">Return Value</span></span>  
 <span data-ttu-id="afd03-120">Wartość S_OK, jeśli metoda zakończy się pomyślnie; w przeciwnym razie E_FAIL lub inny kod błędu.</span><span class="sxs-lookup"><span data-stu-id="afd03-120">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="afd03-121">Wymagania</span><span class="sxs-lookup"><span data-stu-id="afd03-121">Requirements</span></span>  
 <span data-ttu-id="afd03-122">**Header:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="afd03-122">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="afd03-123">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="afd03-123">See Also</span></span>  
 [<span data-ttu-id="afd03-124">ISymUnmanagedWriter, interfejs</span><span class="sxs-lookup"><span data-stu-id="afd03-124">ISymUnmanagedWriter Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-interface.md)
