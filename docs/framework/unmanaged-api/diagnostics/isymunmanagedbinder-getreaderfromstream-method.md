---
title: ISymUnmanagedBinder::GetReaderFromStream — Metoda
ms.date: 03/30/2017
api_name:
- ISymUnmanagedBinder.GetReaderFromStream
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedBinder::GetReaderFromStream
helpviewer_keywords:
- ISymUnmanagedBinder::GetReaderFromStream method [.NET Framework debugging]
- GetReaderFromStream method [.NET Framework debugging]
ms.assetid: aa38efd4-de7e-4482-a5d3-adc152093460
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: af4e9124140c2b311fb2c10800200f5d4d8dc679
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54545767"
---
# <a name="isymunmanagedbindergetreaderfromstream-method"></a><span data-ttu-id="4cf40-102">ISymUnmanagedBinder::GetReaderFromStream — Metoda</span><span class="sxs-lookup"><span data-stu-id="4cf40-102">ISymUnmanagedBinder::GetReaderFromStream Method</span></span>
<span data-ttu-id="4cf40-103">Podany interfejs metadanych i strumienia, który zawiera magazyn symboli, zwraca poprawny [isymunmanagedreader —](isymunmanagedreader-interface.md) strukturę, która będzie odczytywać debugowanie symboli z magazynu podanego symbolu.</span><span class="sxs-lookup"><span data-stu-id="4cf40-103">Given a metadata interface and a stream that contains the symbol store, returns the correct [ISymUnmanagedReader](isymunmanagedreader-interface.md) structure that will read the debugging symbols from the given symbol store.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4cf40-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="4cf40-104">Syntax</span></span>  
  
```  
HRESULT GetReaderFromStream(  
    [in]  IUnknown  *importer,  
    [in]  IStream   *pstream,  
    [out,retval] ISymUnmanagedReader **pRetVal);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="4cf40-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="4cf40-105">Parameters</span></span>  
 `importer`  
 <span data-ttu-id="4cf40-106">[in] Wskaźnik do interfejsu Importowanie metadanych.</span><span class="sxs-lookup"><span data-stu-id="4cf40-106">[in] A pointer to the metadata import interface.</span></span>  
  
 `pstream`  
 <span data-ttu-id="4cf40-107">[in] Wskaźnik do strumienia, który zawiera magazyn symboli.</span><span class="sxs-lookup"><span data-stu-id="4cf40-107">[in] A pointer to the stream that contains the symbol store.</span></span>  
  
 `pRetVal`  
 <span data-ttu-id="4cf40-108">[out] Wskaźnik, który jest ustawiony do zwracanego [isymunmanagedreader —](isymunmanagedreader-interface.md) interfejsu.</span><span class="sxs-lookup"><span data-stu-id="4cf40-108">[out] A pointer that is set to the returned [ISymUnmanagedReader](isymunmanagedreader-interface.md) interface.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="4cf40-109">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="4cf40-109">Return Value</span></span>  
 <span data-ttu-id="4cf40-110">S_OK, jeśli metoda się powiedzie; w przeciwnym razie E_FAIL lub innego kodu błędu.</span><span class="sxs-lookup"><span data-stu-id="4cf40-110">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4cf40-111">Wymagania</span><span class="sxs-lookup"><span data-stu-id="4cf40-111">Requirements</span></span>  
 <span data-ttu-id="4cf40-112">**Nagłówek:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="4cf40-112">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4cf40-113">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="4cf40-113">See also</span></span>
- [<span data-ttu-id="4cf40-114">ISymUnmanagedBinder, interfejs</span><span class="sxs-lookup"><span data-stu-id="4cf40-114">ISymUnmanagedBinder Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedbinder-interface.md)
