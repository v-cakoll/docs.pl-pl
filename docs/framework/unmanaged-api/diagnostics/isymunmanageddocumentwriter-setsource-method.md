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
ms.openlocfilehash: 64982308c6eb7e9df4b94b4e123857c65939f044
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61939753"
---
# <a name="isymunmanageddocumentwritersetsource-method"></a><span data-ttu-id="ad251-102">ISymUnmanagedDocumentWriter::SetSource — Metoda</span><span class="sxs-lookup"><span data-stu-id="ad251-102">ISymUnmanagedDocumentWriter::SetSource Method</span></span>
<span data-ttu-id="ad251-103">Ustawia osadzone źródło dla dokumentu, który jest zapisywany.</span><span class="sxs-lookup"><span data-stu-id="ad251-103">Sets embedded source for a document that is being written.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ad251-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="ad251-104">Syntax</span></span>  
  
```  
HRESULT SetSource(  
    [in]  ULONG32  sourceSize,  
    [in, size_is(sourceSize)] BYTE  source[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ad251-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="ad251-105">Parameters</span></span>  
 `sourceSize`  
 <span data-ttu-id="ad251-106">[in] A `ULONG32` zawierający rozmiar `source` buforu.</span><span class="sxs-lookup"><span data-stu-id="ad251-106">[in] A `ULONG32` that contains the size of the `source` buffer.</span></span>  
  
 `source`  
 <span data-ttu-id="ad251-107">[in] Bufor, który przechowuje osadzonego źródła.</span><span class="sxs-lookup"><span data-stu-id="ad251-107">[in] The buffer that stores the embedded source.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="ad251-108">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="ad251-108">Return Value</span></span>  
 <span data-ttu-id="ad251-109">S_OK, jeśli metoda się powiedzie; w przeciwnym razie E_FAIL lub innego kodu błędu.</span><span class="sxs-lookup"><span data-stu-id="ad251-109">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ad251-110">Wymagania</span><span class="sxs-lookup"><span data-stu-id="ad251-110">Requirements</span></span>  
 <span data-ttu-id="ad251-111">**Nagłówek:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="ad251-111">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ad251-112">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="ad251-112">See also</span></span>

- [<span data-ttu-id="ad251-113">ISymUnmanagedDocumentWriter, interfejs</span><span class="sxs-lookup"><span data-stu-id="ad251-113">ISymUnmanagedDocumentWriter Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanageddocumentwriter-interface.md)
