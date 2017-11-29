---
title: "ISymUnmanagedDocumentWriter::SetCheckSum — Metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ISymUnmanagedDocumentWriter.SetCheckSum
api_location: diasymreader.dll
api_type: COM
f1_keywords: ISymUnmanagedDocumentWriter::SetCheckSum
helpviewer_keywords:
- ISymUnmanagedDocumentWriter::SetCheckSum method [.NET Framework debugging]
- SetCheckSum method [.NET Framework debugging]
ms.assetid: c7e99879-421f-43ce-b193-34733cf30085
topic_type: apiref
caps.latest.revision: "9"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 9693b21c2b3819096ec4aeb0a275fccf76307de0
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="isymunmanageddocumentwritersetchecksum-method"></a><span data-ttu-id="c1f66-102">ISymUnmanagedDocumentWriter::SetCheckSum — Metoda</span><span class="sxs-lookup"><span data-stu-id="c1f66-102">ISymUnmanagedDocumentWriter::SetCheckSum Method</span></span>
<span data-ttu-id="c1f66-103">Ustawia informacje o sumy kontrolnej.</span><span class="sxs-lookup"><span data-stu-id="c1f66-103">Sets checksum information.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c1f66-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="c1f66-104">Syntax</span></span>  
  
```  
HRESULT SetCheckSum(  
    [in]  GUID     algorithmId,  
    [in]  ULONG32  checkSumSize,  
    [in, size_is(checkSumSize)]  BYTE checkSum[]);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="c1f66-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="c1f66-105">Parameters</span></span>  
 `algorithmId`  
 <span data-ttu-id="c1f66-106">[in] Identyfikator GUID to identyfikator algorytmu.</span><span class="sxs-lookup"><span data-stu-id="c1f66-106">[in] The GUID that represents the algorithm identifier.</span></span>  
  
 `checkSumSize`  
 <span data-ttu-id="c1f66-107">[in] A `ULONG32` rozmiar w bajtach, który wskazuje z `checkSum` buforu.</span><span class="sxs-lookup"><span data-stu-id="c1f66-107">[in] A `ULONG32` that indicates the size, in bytes, of the `checkSum` buffer.</span></span>  
  
 `checkSum`  
 <span data-ttu-id="c1f66-108">[in] Bufor, który przechowuje informacji o sumie kontrolnej.</span><span class="sxs-lookup"><span data-stu-id="c1f66-108">[in] The buffer that stores the checksum information.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="c1f66-109">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="c1f66-109">Return Value</span></span>  
 <span data-ttu-id="c1f66-110">Wartość S_OK, jeśli metoda zakończy się pomyślnie; w przeciwnym razie E_FAIL lub inny kod błędu.</span><span class="sxs-lookup"><span data-stu-id="c1f66-110">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c1f66-111">Wymagania</span><span class="sxs-lookup"><span data-stu-id="c1f66-111">Requirements</span></span>  
 <span data-ttu-id="c1f66-112">**Nagłówek:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="c1f66-112">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c1f66-113">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="c1f66-113">See Also</span></span>  
 [<span data-ttu-id="c1f66-114">ISymUnmanagedDocumentWriter — interfejs</span><span class="sxs-lookup"><span data-stu-id="c1f66-114">ISymUnmanagedDocumentWriter Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanageddocumentwriter-interface.md)
