---
title: ISymUnmanagedWriter::SetMethodSourceRange — Metoda
ms.date: 03/30/2017
api_name:
- ISymUnmanagedWriter.SetMethodSourceRange
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedWriter::SetMethodSourceRange
helpviewer_keywords:
- SetMethodSourceRange method [.NET Framework debugging]
- ISymUnmanagedWriter::SetMethodSourceRange method [.NET Framework debugging]
ms.assetid: c698b86e-ace7-4b21-9549-f52d6a034959
topic_type:
- apiref
ms.openlocfilehash: 85e65f6a3ec13c2acc31b8f87dbe4b4476ffc2a5
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/23/2019
ms.locfileid: "74427866"
---
# <a name="isymunmanagedwritersetmethodsourcerange-method"></a><span data-ttu-id="6973e-102">ISymUnmanagedWriter::SetMethodSourceRange — Metoda</span><span class="sxs-lookup"><span data-stu-id="6973e-102">ISymUnmanagedWriter::SetMethodSourceRange Method</span></span>
<span data-ttu-id="6973e-103">Określa wartość rzeczywistą początkową i końcową metody w pliku źródłowym.</span><span class="sxs-lookup"><span data-stu-id="6973e-103">Specifies the true start and end of a method within a source file.</span></span> <span data-ttu-id="6973e-104">Użyj tej metody, aby określić zakres metody niezależnie od punktów sekwencji istniejących w metodzie.</span><span class="sxs-lookup"><span data-stu-id="6973e-104">Use this method to specify the extent of a method independently of the sequence points that exist within the method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6973e-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="6973e-105">Syntax</span></span>  
  
```cpp  
HRESULT SetMethodSourceRange(  
    [in] ISymUnmanagedDocumentWriter  *startDoc,  
    [in] ULONG32                      startLine,  
    [in] ULONG32                      startColumn,  
    [in] ISymUnmanagedDocumentWriter  *endDoc,  
    [in] ULONG32                      endLine,  
    [in] ULONG32                      endColumn);  
```  
  
## <a name="parameters"></a><span data-ttu-id="6973e-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="6973e-106">Parameters</span></span>  
 `startDoc`  
 <span data-ttu-id="6973e-107">podczas Wskaźnik do dokumentu zawierającego pozycję początkową.</span><span class="sxs-lookup"><span data-stu-id="6973e-107">[in] A pointer to the document containing the starting position.</span></span>  
  
 `startLine`  
 <span data-ttu-id="6973e-108">podczas Numer wiersza początkowego.</span><span class="sxs-lookup"><span data-stu-id="6973e-108">[in] The starting line number.</span></span>  
  
 `startColumn`  
 <span data-ttu-id="6973e-109">podczas Kolumna początkowa.</span><span class="sxs-lookup"><span data-stu-id="6973e-109">[in] The starting column.</span></span>  
  
 `endDoc`  
 <span data-ttu-id="6973e-110">podczas Wskaźnik do dokumentu zawierającego pozycję końcową.</span><span class="sxs-lookup"><span data-stu-id="6973e-110">[in] A pointer to the document containing the ending position.</span></span>  
  
 `endLine`  
 <span data-ttu-id="6973e-111">podczas Numer wiersza końcowego.</span><span class="sxs-lookup"><span data-stu-id="6973e-111">[in] The ending line number.</span></span>  
  
 `endColumn`  
 <span data-ttu-id="6973e-112">podczas Numer kolumny końcowej.</span><span class="sxs-lookup"><span data-stu-id="6973e-112">[in] The ending column number.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="6973e-113">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="6973e-113">Return Value</span></span>  
 <span data-ttu-id="6973e-114">S_OK, jeśli metoda się powiedzie; w przeciwnym razie E_FAIL lub inny kod błędu.</span><span class="sxs-lookup"><span data-stu-id="6973e-114">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6973e-115">Wymagania</span><span class="sxs-lookup"><span data-stu-id="6973e-115">Requirements</span></span>  
 <span data-ttu-id="6973e-116">**Nagłówek:** CorSym. idl, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="6973e-116">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6973e-117">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="6973e-117">See also</span></span>

- [<span data-ttu-id="6973e-118">ISymUnmanagedWriter, interfejs</span><span class="sxs-lookup"><span data-stu-id="6973e-118">ISymUnmanagedWriter Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-interface.md)
