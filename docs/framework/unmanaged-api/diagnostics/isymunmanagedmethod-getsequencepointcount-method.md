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
ms.openlocfilehash: 9eac17ec9599caba88ddaa73d28abcae538a4d19
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59215069"
---
# <a name="isymunmanagedmethodgetsequencepointcount-method"></a><span data-ttu-id="764ac-102">ISymUnmanagedMethod::GetSequencePointCount — Metoda</span><span class="sxs-lookup"><span data-stu-id="764ac-102">ISymUnmanagedMethod::GetSequencePointCount Method</span></span>
<span data-ttu-id="764ac-103">Pobiera liczbę punktów sekwencji w ramach tej metody.</span><span class="sxs-lookup"><span data-stu-id="764ac-103">Gets the count of sequence points within this method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="764ac-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="764ac-104">Syntax</span></span>  
  
```  
HRESULT GetSequencePointCount(  
    [out, retval] ULONG32* pRetVal);  
```  
  
## <a name="parameters"></a><span data-ttu-id="764ac-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="764ac-105">Parameters</span></span>  
 `pRetVal`  
 <span data-ttu-id="764ac-106">[out] Wskaźnik do `ULONG32` odbierająca rozmiar buforu, muszą zawierać punktów sekwencji.</span><span class="sxs-lookup"><span data-stu-id="764ac-106">[out] A pointer to a `ULONG32` that receives the size of the buffer required to contain the sequence points.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="764ac-107">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="764ac-107">Return Value</span></span>  
 <span data-ttu-id="764ac-108">S_OK, jeśli metoda się powiedzie; w przeciwnym razie E_FAIL lub innego kodu błędu.</span><span class="sxs-lookup"><span data-stu-id="764ac-108">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="764ac-109">Wymagania</span><span class="sxs-lookup"><span data-stu-id="764ac-109">Requirements</span></span>  
 <span data-ttu-id="764ac-110">**Nagłówek:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="764ac-110">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="764ac-111">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="764ac-111">See also</span></span>

- [<span data-ttu-id="764ac-112">ISymUnmanagedMethod, interfejs</span><span class="sxs-lookup"><span data-stu-id="764ac-112">ISymUnmanagedMethod Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedmethod-interface.md)
