---
title: ISymUnmanagedDocumentWriter::SetCheckSum — Metoda
ms.date: 03/30/2017
api_name:
- ISymUnmanagedDocumentWriter.SetCheckSum
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedDocumentWriter::SetCheckSum
helpviewer_keywords:
- ISymUnmanagedDocumentWriter::SetCheckSum method [.NET Framework debugging]
- SetCheckSum method [.NET Framework debugging]
ms.assetid: c7e99879-421f-43ce-b193-34733cf30085
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: ac3daccfade4f5ae10fe2ebbf83a7a11af34b89b
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61939766"
---
# <a name="isymunmanageddocumentwritersetchecksum-method"></a><span data-ttu-id="7b67a-102">ISymUnmanagedDocumentWriter::SetCheckSum — Metoda</span><span class="sxs-lookup"><span data-stu-id="7b67a-102">ISymUnmanagedDocumentWriter::SetCheckSum Method</span></span>
<span data-ttu-id="7b67a-103">Ustawia informacji o sumie kontrolnej.</span><span class="sxs-lookup"><span data-stu-id="7b67a-103">Sets checksum information.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7b67a-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="7b67a-104">Syntax</span></span>  
  
```  
HRESULT SetCheckSum(  
    [in]  GUID     algorithmId,  
    [in]  ULONG32  checkSumSize,  
    [in, size_is(checkSumSize)]  BYTE checkSum[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="7b67a-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="7b67a-105">Parameters</span></span>  
 `algorithmId`  
 <span data-ttu-id="7b67a-106">[in] Identyfikator GUID, który reprezentuje identyfikator algorytmu.</span><span class="sxs-lookup"><span data-stu-id="7b67a-106">[in] The GUID that represents the algorithm identifier.</span></span>  
  
 `checkSumSize`  
 <span data-ttu-id="7b67a-107">[in] A `ULONG32` rozmiar w bajtach, który wskazuje z `checkSum` buforu.</span><span class="sxs-lookup"><span data-stu-id="7b67a-107">[in] A `ULONG32` that indicates the size, in bytes, of the `checkSum` buffer.</span></span>  
  
 `checkSum`  
 <span data-ttu-id="7b67a-108">[in] Bufor, który przechowuje informacji o sumie kontrolnej.</span><span class="sxs-lookup"><span data-stu-id="7b67a-108">[in] The buffer that stores the checksum information.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="7b67a-109">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="7b67a-109">Return Value</span></span>  
 <span data-ttu-id="7b67a-110">S_OK, jeśli metoda się powiedzie; w przeciwnym razie E_FAIL lub innego kodu błędu.</span><span class="sxs-lookup"><span data-stu-id="7b67a-110">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7b67a-111">Wymagania</span><span class="sxs-lookup"><span data-stu-id="7b67a-111">Requirements</span></span>  
 <span data-ttu-id="7b67a-112">**Nagłówek:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="7b67a-112">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7b67a-113">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="7b67a-113">See also</span></span>

- [<span data-ttu-id="7b67a-114">ISymUnmanagedDocumentWriter, interfejs</span><span class="sxs-lookup"><span data-stu-id="7b67a-114">ISymUnmanagedDocumentWriter Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanageddocumentwriter-interface.md)
