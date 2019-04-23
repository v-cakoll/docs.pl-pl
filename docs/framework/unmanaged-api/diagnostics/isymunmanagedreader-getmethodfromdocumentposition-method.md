---
title: ISymUnmanagedReader::GetMethodFromDocumentPosition — Metoda
ms.date: 03/30/2017
api_name:
- ISymUnmanagedReader.GetMethodFromDocumentPosition
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedReader::GetMethodFromDocumentPosition
helpviewer_keywords:
- GetMethodFromDocumentPosition method [.NET Framework debugging]
- ISymUnmanagedReader::GetMethodFromDocumentPosition method [.NET Framework debugging]
ms.assetid: 55773dbc-9053-46e3-8a3c-86caa9d91fb4
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 4ed13397748b2668c275b221e38bd75c0dd37f03
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59197701"
---
# <a name="isymunmanagedreadergetmethodfromdocumentposition-method"></a><span data-ttu-id="b5110-102">ISymUnmanagedReader::GetMethodFromDocumentPosition — Metoda</span><span class="sxs-lookup"><span data-stu-id="b5110-102">ISymUnmanagedReader::GetMethodFromDocumentPosition Method</span></span>
<span data-ttu-id="b5110-103">Zwraca metodę, która zawiera punkt przerwania na pozycji w dokumencie.</span><span class="sxs-lookup"><span data-stu-id="b5110-103">Returns the method that contains the breakpoint at the given position in a document.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b5110-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="b5110-104">Syntax</span></span>  
  
```  
HRESULT GetMethodFromDocumentPosition (  
    [in]  ISymUnmanagedDocument*  document,  
    [in]  ULONG32  line,  
    [in]  ULONG32  column,  
    [out, retval] ISymUnmanagedMethod**  pRetVal);  
```  
  
## <a name="parameters"></a><span data-ttu-id="b5110-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="b5110-105">Parameters</span></span>  
 `document`  
 <span data-ttu-id="b5110-106">[in] Określony dokument.</span><span class="sxs-lookup"><span data-stu-id="b5110-106">[in] The specified document.</span></span>  
  
 `line`  
 <span data-ttu-id="b5110-107">[in] Wiersz określonego dokumentu.</span><span class="sxs-lookup"><span data-stu-id="b5110-107">[in] The line of the specified document.</span></span>  
  
 `column`  
 <span data-ttu-id="b5110-108">[in] Kolumna określonego dokumentu.</span><span class="sxs-lookup"><span data-stu-id="b5110-108">[in] The column of the specified document.</span></span>  
  
 `pRetVal`  
 <span data-ttu-id="b5110-109">[out] Wskaźnik na adres [isymunmanagedmethod — interfejs](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedmethod-interface.md) obiekt, który reprezentuje metodę zawierającego punkt przerwania.</span><span class="sxs-lookup"><span data-stu-id="b5110-109">[out] A pointer to the address of a [ISymUnmanagedMethod Interface](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedmethod-interface.md) object that represents the method containing the breakpoint.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="b5110-110">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="b5110-110">Return Value</span></span>  
 <span data-ttu-id="b5110-111">S_OK, jeśli metoda się powiedzie; w przeciwnym razie E_FAIL lub innego kodu błędu.</span><span class="sxs-lookup"><span data-stu-id="b5110-111">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b5110-112">Wymagania</span><span class="sxs-lookup"><span data-stu-id="b5110-112">Requirements</span></span>  
 <span data-ttu-id="b5110-113">**Nagłówek:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="b5110-113">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b5110-114">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="b5110-114">See also</span></span>

- [<span data-ttu-id="b5110-115">ISymUnmanagedReader, interfejs</span><span class="sxs-lookup"><span data-stu-id="b5110-115">ISymUnmanagedReader Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-interface.md)
