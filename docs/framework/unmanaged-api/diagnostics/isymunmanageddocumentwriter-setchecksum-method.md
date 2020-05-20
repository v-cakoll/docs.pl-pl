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
ms.openlocfilehash: 06a331e24622e0a155d974ca869818a6532baa1f
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/19/2020
ms.locfileid: "83615543"
---
# <a name="isymunmanageddocumentwritersetchecksum-method"></a><span data-ttu-id="fecaf-102">ISymUnmanagedDocumentWriter::SetCheckSum — Metoda</span><span class="sxs-lookup"><span data-stu-id="fecaf-102">ISymUnmanagedDocumentWriter::SetCheckSum Method</span></span>
<span data-ttu-id="fecaf-103">Ustawia informacje o sumie kontrolnej.</span><span class="sxs-lookup"><span data-stu-id="fecaf-103">Sets checksum information.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fecaf-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="fecaf-104">Syntax</span></span>  
  
```cpp  
HRESULT SetCheckSum(  
    [in]  GUID     algorithmId,  
    [in]  ULONG32  checkSumSize,  
    [in, size_is(checkSumSize)]  BYTE checkSum[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="fecaf-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="fecaf-105">Parameters</span></span>  
 `algorithmId`  
 <span data-ttu-id="fecaf-106">podczas Identyfikator GUID, który reprezentuje identyfikator algorytmu.</span><span class="sxs-lookup"><span data-stu-id="fecaf-106">[in] The GUID that represents the algorithm identifier.</span></span>  
  
 `checkSumSize`  
 <span data-ttu-id="fecaf-107">podczas `ULONG32`Wskazuje rozmiar bufora (w bajtach) `checkSum` .</span><span class="sxs-lookup"><span data-stu-id="fecaf-107">[in] A `ULONG32` that indicates the size, in bytes, of the `checkSum` buffer.</span></span>  
  
 `checkSum`  
 <span data-ttu-id="fecaf-108">podczas Bufor przechowujący informacje o sumie kontrolnej.</span><span class="sxs-lookup"><span data-stu-id="fecaf-108">[in] The buffer that stores the checksum information.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="fecaf-109">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="fecaf-109">Return Value</span></span>  
 <span data-ttu-id="fecaf-110">S_OK, jeśli metoda się powiedzie; w przeciwnym razie E_FAIL lub inny kod błędu.</span><span class="sxs-lookup"><span data-stu-id="fecaf-110">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="fecaf-111">Wymagania</span><span class="sxs-lookup"><span data-stu-id="fecaf-111">Requirements</span></span>  
 <span data-ttu-id="fecaf-112">**Nagłówek:** CorSym. idl, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="fecaf-112">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fecaf-113">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="fecaf-113">See also</span></span>

- [<span data-ttu-id="fecaf-114">ISymUnmanagedDocumentWriter, interfejs</span><span class="sxs-lookup"><span data-stu-id="fecaf-114">ISymUnmanagedDocumentWriter Interface</span></span>](isymunmanageddocumentwriter-interface.md)
