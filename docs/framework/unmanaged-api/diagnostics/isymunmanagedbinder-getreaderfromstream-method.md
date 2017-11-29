---
title: "ISymUnmanagedBinder::GetReaderFromStream — Metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ISymUnmanagedBinder.GetReaderFromStream
api_location: diasymreader.dll
api_type: COM
f1_keywords: ISymUnmanagedBinder::GetReaderFromStream
helpviewer_keywords:
- ISymUnmanagedBinder::GetReaderFromStream method [.NET Framework debugging]
- GetReaderFromStream method [.NET Framework debugging]
ms.assetid: aa38efd4-de7e-4482-a5d3-adc152093460
topic_type: apiref
caps.latest.revision: "9"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 96bd12b69b84537415ddf2e0ae992ec179f32493
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="isymunmanagedbindergetreaderfromstream-method"></a><span data-ttu-id="2b8d4-102">ISymUnmanagedBinder::GetReaderFromStream — Metoda</span><span class="sxs-lookup"><span data-stu-id="2b8d4-102">ISymUnmanagedBinder::GetReaderFromStream Method</span></span>
<span data-ttu-id="2b8d4-103">Podany interfejs metadanych i strumienia, który zawiera magazyn symbol zwraca poprawny <<!--zz xref:ISymUnmanagedReader --> `ISymUnmanagedReader`> Struktura, która będzie odczytywać debugowanie symboli z magazynu podanego symbolu.</span><span class="sxs-lookup"><span data-stu-id="2b8d4-103">Given a metadata interface and a stream that contains the symbol store, returns the correct <<!--zz xref:ISymUnmanagedReader --> `ISymUnmanagedReader`> structure that will read the debugging symbols from the given symbol store.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2b8d4-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="2b8d4-104">Syntax</span></span>  
  
```  
HRESULT GetReaderFromStream(  
    [in]  IUnknown  *importer,  
    [in]  IStream   *pstream,  
    [out,retval] ISymUnmanagedReader **pRetVal);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="2b8d4-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="2b8d4-105">Parameters</span></span>  
 `importer`  
 <span data-ttu-id="2b8d4-106">[in] Wskaźnik do interfejsu importu metadanych.</span><span class="sxs-lookup"><span data-stu-id="2b8d4-106">[in] A pointer to the metadata import interface.</span></span>  
  
 `pstream`  
 <span data-ttu-id="2b8d4-107">[in] Wskaźnik do strumienia, który zawiera magazynu symboli.</span><span class="sxs-lookup"><span data-stu-id="2b8d4-107">[in] A pointer to the stream that contains the symbol store.</span></span>  
  
 `pRetVal`  
 <span data-ttu-id="2b8d4-108">[out] Wskaźnik, który jest ustawiony na zwracana <<!--zz xref:ISymUnmanagedReader --> `ISymUnmanagedReader`> interfejsu.</span><span class="sxs-lookup"><span data-stu-id="2b8d4-108">[out] A pointer that is set to the returned <<!--zz xref:ISymUnmanagedReader --> `ISymUnmanagedReader`> interface.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="2b8d4-109">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="2b8d4-109">Return Value</span></span>  
 <span data-ttu-id="2b8d4-110">Wartość S_OK, jeśli metoda zakończy się pomyślnie; w przeciwnym razie E_FAIL lub inny kod błędu.</span><span class="sxs-lookup"><span data-stu-id="2b8d4-110">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2b8d4-111">Wymagania</span><span class="sxs-lookup"><span data-stu-id="2b8d4-111">Requirements</span></span>  
 <span data-ttu-id="2b8d4-112">**Nagłówek:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="2b8d4-112">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2b8d4-113">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="2b8d4-113">See Also</span></span>  
 [<span data-ttu-id="2b8d4-114">ISymUnmanagedBinder — interfejs</span><span class="sxs-lookup"><span data-stu-id="2b8d4-114">ISymUnmanagedBinder Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedbinder-interface.md)
