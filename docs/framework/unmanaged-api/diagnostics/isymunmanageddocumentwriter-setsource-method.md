---
title: "ISymUnmanagedDocumentWriter::SetSource — Metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
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
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 287eba260ca20bae9da94ed2d00dcf1661fe14cf
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="isymunmanageddocumentwritersetsource-method"></a><span data-ttu-id="9e6a8-102">ISymUnmanagedDocumentWriter::SetSource — Metoda</span><span class="sxs-lookup"><span data-stu-id="9e6a8-102">ISymUnmanagedDocumentWriter::SetSource Method</span></span>
<span data-ttu-id="9e6a8-103">Zestawy osadzone źródło dla dokumentu, który jest zapisywany.</span><span class="sxs-lookup"><span data-stu-id="9e6a8-103">Sets embedded source for a document that is being written.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9e6a8-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="9e6a8-104">Syntax</span></span>  
  
```  
HRESULT SetSource(  
    [in]  ULONG32  sourceSize,  
    [in, size_is(sourceSize)] BYTE  source[]);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="9e6a8-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="9e6a8-105">Parameters</span></span>  
 `sourceSize`  
 <span data-ttu-id="9e6a8-106">[in] A `ULONG32` zawierający rozmiar `source` buforu.</span><span class="sxs-lookup"><span data-stu-id="9e6a8-106">[in] A `ULONG32` that contains the size of the `source` buffer.</span></span>  
  
 `source`  
 <span data-ttu-id="9e6a8-107">[in] Bufor, który przechowuje osadzone źródło.</span><span class="sxs-lookup"><span data-stu-id="9e6a8-107">[in] The buffer that stores the embedded source.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="9e6a8-108">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="9e6a8-108">Return Value</span></span>  
 <span data-ttu-id="9e6a8-109">Wartość S_OK, jeśli metoda zakończy się pomyślnie; w przeciwnym razie E_FAIL lub inny kod błędu.</span><span class="sxs-lookup"><span data-stu-id="9e6a8-109">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9e6a8-110">Wymagania</span><span class="sxs-lookup"><span data-stu-id="9e6a8-110">Requirements</span></span>  
 <span data-ttu-id="9e6a8-111">**Nagłówek:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="9e6a8-111">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9e6a8-112">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="9e6a8-112">See Also</span></span>  
 [<span data-ttu-id="9e6a8-113">ISymUnmanagedDocumentWriter, interfejs</span><span class="sxs-lookup"><span data-stu-id="9e6a8-113">ISymUnmanagedDocumentWriter Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanageddocumentwriter-interface.md)
