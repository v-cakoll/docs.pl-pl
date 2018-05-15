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
ms.openlocfilehash: f25f66d7092c50247e24051280eaa7b714297c20
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="isymunmanageddocumentwritersetsource-method"></a><span data-ttu-id="eb2c3-102">ISymUnmanagedDocumentWriter::SetSource — Metoda</span><span class="sxs-lookup"><span data-stu-id="eb2c3-102">ISymUnmanagedDocumentWriter::SetSource Method</span></span>
<span data-ttu-id="eb2c3-103">Zestawy osadzone źródło dla dokumentu, który jest zapisywany.</span><span class="sxs-lookup"><span data-stu-id="eb2c3-103">Sets embedded source for a document that is being written.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="eb2c3-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="eb2c3-104">Syntax</span></span>  
  
```  
HRESULT SetSource(  
    [in]  ULONG32  sourceSize,  
    [in, size_is(sourceSize)] BYTE  source[]);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="eb2c3-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="eb2c3-105">Parameters</span></span>  
 `sourceSize`  
 <span data-ttu-id="eb2c3-106">[in] A `ULONG32` zawierający rozmiar `source` buforu.</span><span class="sxs-lookup"><span data-stu-id="eb2c3-106">[in] A `ULONG32` that contains the size of the `source` buffer.</span></span>  
  
 `source`  
 <span data-ttu-id="eb2c3-107">[in] Bufor, który przechowuje osadzone źródło.</span><span class="sxs-lookup"><span data-stu-id="eb2c3-107">[in] The buffer that stores the embedded source.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="eb2c3-108">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="eb2c3-108">Return Value</span></span>  
 <span data-ttu-id="eb2c3-109">Wartość S_OK, jeśli metoda zakończy się pomyślnie; w przeciwnym razie E_FAIL lub inny kod błędu.</span><span class="sxs-lookup"><span data-stu-id="eb2c3-109">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="eb2c3-110">Wymagania</span><span class="sxs-lookup"><span data-stu-id="eb2c3-110">Requirements</span></span>  
 <span data-ttu-id="eb2c3-111">**Header:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="eb2c3-111">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="eb2c3-112">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="eb2c3-112">See Also</span></span>  
 [<span data-ttu-id="eb2c3-113">ISymUnmanagedDocumentWriter, interfejs</span><span class="sxs-lookup"><span data-stu-id="eb2c3-113">ISymUnmanagedDocumentWriter Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanageddocumentwriter-interface.md)
