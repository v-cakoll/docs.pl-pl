---
title: "ISymUnmanagedMethod::GetOffset — Metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ISymUnmanagedMethod.GetOffset
api_location: diasymreader.dll
api_type: COM
f1_keywords: ISymUnmanagedMethod::GetOffset
helpviewer_keywords:
- GetOffset method, ISymUnmanagedMethod interface [.NET Framework debugging]
- ISymUnmanagedMethod::GetOffset method [.NET Framework debugging]
ms.assetid: 8bf3cb62-89bf-4159-ad53-de606aba89e8
topic_type: apiref
caps.latest.revision: "8"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: f75236ae954b4ff3df9dd1c322cef45dfaf7fb2d
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="isymunmanagedmethodgetoffset-method"></a><span data-ttu-id="b1ab3-102">ISymUnmanagedMethod::GetOffset — Metoda</span><span class="sxs-lookup"><span data-stu-id="b1ab3-102">ISymUnmanagedMethod::GetOffset Method</span></span>
<span data-ttu-id="b1ab3-103">Zwraca przesunięcie w ramach tej metody, która odpowiada na określonej pozycji w dokumencie.</span><span class="sxs-lookup"><span data-stu-id="b1ab3-103">Returns the offset within this method that corresponds to a given position within a document.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b1ab3-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="b1ab3-104">Syntax</span></span>  
  
```  
HRESULT GetOffset(  
    [in]  ISymUnmanagedDocument*  document,  
    [in]  ULONG32                 line,  
    [in]  ULONG32                 column,  
    [out, retval] ULONG32*        pRetVal);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="b1ab3-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="b1ab3-105">Parameters</span></span>  
 `document`  
 <span data-ttu-id="b1ab3-106">[in] Wskaźnik do dokumentu, dla którego wnioskuje się przesunięcie.</span><span class="sxs-lookup"><span data-stu-id="b1ab3-106">[in] A pointer to the document for which the offset is requested.</span></span>  
  
 `line`  
 <span data-ttu-id="b1ab3-107">[in] Wiersz dokumentu, dla którego wnioskuje się przesunięcie.</span><span class="sxs-lookup"><span data-stu-id="b1ab3-107">[in] The document line for which the offset is requested.</span></span>  
  
 `column`  
 <span data-ttu-id="b1ab3-108">[in] Kolumna dokumentu, dla którego wnioskuje się przesunięcie.</span><span class="sxs-lookup"><span data-stu-id="b1ab3-108">[in] The document column for which the offset is requested.</span></span>  
  
 `pRetVal`  
 <span data-ttu-id="b1ab3-109">[out] Wskaźnik do `ULONG32` odbierająca przesunięcia.</span><span class="sxs-lookup"><span data-stu-id="b1ab3-109">[out] A pointer to a `ULONG32` that receives the offsets.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="b1ab3-110">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="b1ab3-110">Return Value</span></span>  
 <span data-ttu-id="b1ab3-111">Wartość S_OK, jeśli metoda zakończy się pomyślnie; w przeciwnym razie E_FAIL lub inny kod błędu.</span><span class="sxs-lookup"><span data-stu-id="b1ab3-111">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b1ab3-112">Wymagania</span><span class="sxs-lookup"><span data-stu-id="b1ab3-112">Requirements</span></span>  
 <span data-ttu-id="b1ab3-113">**Nagłówek:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="b1ab3-113">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b1ab3-114">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="b1ab3-114">See Also</span></span>  
 [<span data-ttu-id="b1ab3-115">ISymUnmanagedMethod — interfejs</span><span class="sxs-lookup"><span data-stu-id="b1ab3-115">ISymUnmanagedMethod Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedmethod-interface.md)
