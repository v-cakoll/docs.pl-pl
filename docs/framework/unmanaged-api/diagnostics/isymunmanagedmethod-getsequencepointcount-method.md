---
title: ISymUnmanagedMethod::GetSequencePointCount — Metoda
ms.date: 03/30/2017
api_name:
- ISymUnmanagedMethod.GetSequencePointCount
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedMethod::GetSequencePointCount
helpviewer_keywords:
- ISymUnmanagedMethod::GetSequencePointCount method [.NET Framework debugging]
- GetSequencePointCount method [.NET Framework debugging]
ms.assetid: 836133e8-6108-4b9b-b0a9-bce4e08dccda
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: c1a9ef59cfe63ba745e6f5eba3ba2c3f3f983886
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="isymunmanagedmethodgetsequencepointcount-method"></a><span data-ttu-id="270be-102">ISymUnmanagedMethod::GetSequencePointCount — Metoda</span><span class="sxs-lookup"><span data-stu-id="270be-102">ISymUnmanagedMethod::GetSequencePointCount Method</span></span>
<span data-ttu-id="270be-103">Pobiera liczbę punktów sekwencji w ramach tej metody.</span><span class="sxs-lookup"><span data-stu-id="270be-103">Gets the count of sequence points within this method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="270be-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="270be-104">Syntax</span></span>  
  
```  
HRESULT GetSequencePointCount(  
    [out, retval] ULONG32* pRetVal);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="270be-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="270be-105">Parameters</span></span>  
 `pRetVal`  
 <span data-ttu-id="270be-106">[out] Wskaźnik do `ULONG32` odbierająca rozmiar buforu, muszą zawierać punkty sekwencji.</span><span class="sxs-lookup"><span data-stu-id="270be-106">[out] A pointer to a `ULONG32` that receives the size of the buffer required to contain the sequence points.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="270be-107">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="270be-107">Return Value</span></span>  
 <span data-ttu-id="270be-108">Wartość S_OK, jeśli metoda zakończy się pomyślnie; w przeciwnym razie E_FAIL lub inny kod błędu.</span><span class="sxs-lookup"><span data-stu-id="270be-108">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="270be-109">Wymagania</span><span class="sxs-lookup"><span data-stu-id="270be-109">Requirements</span></span>  
 <span data-ttu-id="270be-110">**Header:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="270be-110">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="270be-111">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="270be-111">See Also</span></span>  
 [<span data-ttu-id="270be-112">ISymUnmanagedMethod, interfejs</span><span class="sxs-lookup"><span data-stu-id="270be-112">ISymUnmanagedMethod Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedmethod-interface.md)
