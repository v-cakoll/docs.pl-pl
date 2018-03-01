---
title: "ISymUnmanagedBinder::GetReaderFromStream — Metoda"
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
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 36d4d0067cd638eb39ce82eb042242b7b08d3647
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="isymunmanagedbindergetreaderfromstream-method"></a><span data-ttu-id="d6503-102">ISymUnmanagedBinder::GetReaderFromStream — Metoda</span><span class="sxs-lookup"><span data-stu-id="d6503-102">ISymUnmanagedBinder::GetReaderFromStream Method</span></span>
<span data-ttu-id="d6503-103">Podany interfejs metadanych i strumienia, który zawiera magazyn symbol zwraca poprawny [ISymUnmanagedReader](isymunmanagedreader-interface.md) strukturę, która będzie odczytywać debugowanie symboli z magazynu podanego symbolu.</span><span class="sxs-lookup"><span data-stu-id="d6503-103">Given a metadata interface and a stream that contains the symbol store, returns the correct [ISymUnmanagedReader](isymunmanagedreader-interface.md) structure that will read the debugging symbols from the given symbol store.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d6503-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="d6503-104">Syntax</span></span>  
  
```  
HRESULT GetReaderFromStream(  
    [in]  IUnknown  *importer,  
    [in]  IStream   *pstream,  
    [out,retval] ISymUnmanagedReader **pRetVal);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="d6503-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="d6503-105">Parameters</span></span>  
 `importer`  
 <span data-ttu-id="d6503-106">[in] Wskaźnik do interfejsu importu metadanych.</span><span class="sxs-lookup"><span data-stu-id="d6503-106">[in] A pointer to the metadata import interface.</span></span>  
  
 `pstream`  
 <span data-ttu-id="d6503-107">[in] Wskaźnik do strumienia, który zawiera magazynu symboli.</span><span class="sxs-lookup"><span data-stu-id="d6503-107">[in] A pointer to the stream that contains the symbol store.</span></span>  
  
 `pRetVal`  
 <span data-ttu-id="d6503-108">[out] Wskaźnik, który jest ustawiony na zwróconego [ISymUnmanagedReader](isymunmanagedreader-interface.md) interfejsu.</span><span class="sxs-lookup"><span data-stu-id="d6503-108">[out] A pointer that is set to the returned [ISymUnmanagedReader](isymunmanagedreader-interface.md) interface.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="d6503-109">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="d6503-109">Return Value</span></span>  
 <span data-ttu-id="d6503-110">Wartość S_OK, jeśli metoda zakończy się pomyślnie; w przeciwnym razie E_FAIL lub inny kod błędu.</span><span class="sxs-lookup"><span data-stu-id="d6503-110">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d6503-111">Wymagania</span><span class="sxs-lookup"><span data-stu-id="d6503-111">Requirements</span></span>  
 <span data-ttu-id="d6503-112">**Nagłówek:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="d6503-112">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d6503-113">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="d6503-113">See Also</span></span>  
 [<span data-ttu-id="d6503-114">ISymUnmanagedBinder, interfejs</span><span class="sxs-lookup"><span data-stu-id="d6503-114">ISymUnmanagedBinder Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedbinder-interface.md)
