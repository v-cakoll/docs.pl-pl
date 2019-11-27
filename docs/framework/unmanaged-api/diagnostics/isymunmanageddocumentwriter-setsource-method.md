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
ms.openlocfilehash: ff18f95bd6b4cfde5aaa4d3f6f68b58fd37c04b3
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/23/2019
ms.locfileid: "74449069"
---
# <a name="isymunmanageddocumentwritersetsource-method"></a><span data-ttu-id="06125-102">ISymUnmanagedDocumentWriter::SetSource — Metoda</span><span class="sxs-lookup"><span data-stu-id="06125-102">ISymUnmanagedDocumentWriter::SetSource Method</span></span>
<span data-ttu-id="06125-103">Ustawia osadzone źródło dla dokumentu, który jest zapisywany.</span><span class="sxs-lookup"><span data-stu-id="06125-103">Sets embedded source for a document that is being written.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="06125-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="06125-104">Syntax</span></span>  
  
```cpp  
HRESULT SetSource(  
    [in]  ULONG32  sourceSize,  
    [in, size_is(sourceSize)] BYTE  source[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="06125-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="06125-105">Parameters</span></span>  
 `sourceSize`  
 <span data-ttu-id="06125-106">podczas `ULONG32`, który zawiera rozmiar buforu `source`.</span><span class="sxs-lookup"><span data-stu-id="06125-106">[in] A `ULONG32` that contains the size of the `source` buffer.</span></span>  
  
 `source`  
 <span data-ttu-id="06125-107">podczas Bufor przechowujący osadzone źródło.</span><span class="sxs-lookup"><span data-stu-id="06125-107">[in] The buffer that stores the embedded source.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="06125-108">Wartość zwrócona</span><span class="sxs-lookup"><span data-stu-id="06125-108">Return Value</span></span>  
 <span data-ttu-id="06125-109">S_OK, jeśli metoda się powiedzie; w przeciwnym razie E_FAIL lub inny kod błędu.</span><span class="sxs-lookup"><span data-stu-id="06125-109">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="06125-110">Wymagania</span><span class="sxs-lookup"><span data-stu-id="06125-110">Requirements</span></span>  
 <span data-ttu-id="06125-111">**Nagłówek:** CorSym. idl, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="06125-111">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="06125-112">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="06125-112">See also</span></span>

- [<span data-ttu-id="06125-113">ISymUnmanagedDocumentWriter, interfejs</span><span class="sxs-lookup"><span data-stu-id="06125-113">ISymUnmanagedDocumentWriter Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanageddocumentwriter-interface.md)
