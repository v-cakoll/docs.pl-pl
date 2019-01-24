---
title: ISymUnmanagedDocumentWriter::SetSource — Metoda
ms.date: 03/30/2017
api_name:
- ISymUnmanagedDocumentWriter.SetSource
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedDocumentWriter::SetSource
helpviewer_keywords:
- ISymUnmanagedDocumentWriter::SetSource method [.NET Framework debugging]
- SetSource method [.NET Framework debugging]
ms.assetid: ea5b9d9f-ff06-4bd3-8de5-6435343aba59
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: da19a77637e64fec676fdaac7ba56d47b5b07769
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54549892"
---
# <a name="isymunmanageddocumentwritersetsource-method"></a><span data-ttu-id="db92b-102">ISymUnmanagedDocumentWriter::SetSource — Metoda</span><span class="sxs-lookup"><span data-stu-id="db92b-102">ISymUnmanagedDocumentWriter::SetSource Method</span></span>
<span data-ttu-id="db92b-103">Ustawia osadzone źródło dla dokumentu, który jest zapisywany.</span><span class="sxs-lookup"><span data-stu-id="db92b-103">Sets embedded source for a document that is being written.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="db92b-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="db92b-104">Syntax</span></span>  
  
```  
HRESULT SetSource(  
    [in]  ULONG32  sourceSize,  
    [in, size_is(sourceSize)] BYTE  source[]);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="db92b-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="db92b-105">Parameters</span></span>  
 `sourceSize`  
 <span data-ttu-id="db92b-106">[in] A `ULONG32` zawierający rozmiar `source` buforu.</span><span class="sxs-lookup"><span data-stu-id="db92b-106">[in] A `ULONG32` that contains the size of the `source` buffer.</span></span>  
  
 `source`  
 <span data-ttu-id="db92b-107">[in] Bufor, który przechowuje osadzonego źródła.</span><span class="sxs-lookup"><span data-stu-id="db92b-107">[in] The buffer that stores the embedded source.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="db92b-108">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="db92b-108">Return Value</span></span>  
 <span data-ttu-id="db92b-109">S_OK, jeśli metoda się powiedzie; w przeciwnym razie E_FAIL lub innego kodu błędu.</span><span class="sxs-lookup"><span data-stu-id="db92b-109">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="db92b-110">Wymagania</span><span class="sxs-lookup"><span data-stu-id="db92b-110">Requirements</span></span>  
 <span data-ttu-id="db92b-111">**Nagłówek:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="db92b-111">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="db92b-112">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="db92b-112">See also</span></span>
- [<span data-ttu-id="db92b-113">ISymUnmanagedDocumentWriter, interfejs</span><span class="sxs-lookup"><span data-stu-id="db92b-113">ISymUnmanagedDocumentWriter Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanageddocumentwriter-interface.md)
