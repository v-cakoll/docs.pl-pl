---
title: ISymUnmanagedMethod::GetOffset — Metoda
ms.date: 03/30/2017
api_name:
- ISymUnmanagedMethod.GetOffset
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedMethod::GetOffset
helpviewer_keywords:
- GetOffset method, ISymUnmanagedMethod interface [.NET Framework debugging]
- ISymUnmanagedMethod::GetOffset method [.NET Framework debugging]
ms.assetid: 8bf3cb62-89bf-4159-ad53-de606aba89e8
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: a42dc624d4de9cddebad287f6d90590f96b30272
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59223657"
---
# <a name="isymunmanagedmethodgetoffset-method"></a><span data-ttu-id="65139-102">ISymUnmanagedMethod::GetOffset — Metoda</span><span class="sxs-lookup"><span data-stu-id="65139-102">ISymUnmanagedMethod::GetOffset Method</span></span>
<span data-ttu-id="65139-103">Zwraca przesunięcie w ramach tej metody, która odnosi się do określonej pozycji w dokumencie.</span><span class="sxs-lookup"><span data-stu-id="65139-103">Returns the offset within this method that corresponds to a given position within a document.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="65139-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="65139-104">Syntax</span></span>  
  
```  
HRESULT GetOffset(  
    [in]  ISymUnmanagedDocument*  document,  
    [in]  ULONG32                 line,  
    [in]  ULONG32                 column,  
    [out, retval] ULONG32*        pRetVal);  
```  
  
## <a name="parameters"></a><span data-ttu-id="65139-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="65139-105">Parameters</span></span>  
 `document`  
 <span data-ttu-id="65139-106">[in] Wskaźnik do dokumentu, dla którego żądana jest przesunięcie.</span><span class="sxs-lookup"><span data-stu-id="65139-106">[in] A pointer to the document for which the offset is requested.</span></span>  
  
 `line`  
 <span data-ttu-id="65139-107">[in] Wiersz dokumentu, dla którego żądana jest przesunięcie.</span><span class="sxs-lookup"><span data-stu-id="65139-107">[in] The document line for which the offset is requested.</span></span>  
  
 `column`  
 <span data-ttu-id="65139-108">[in] Kolumna dokumentu, dla którego żądana jest przesunięcie.</span><span class="sxs-lookup"><span data-stu-id="65139-108">[in] The document column for which the offset is requested.</span></span>  
  
 `pRetVal`  
 <span data-ttu-id="65139-109">[out] Wskaźnik do `ULONG32` odbierająca przesunięcia.</span><span class="sxs-lookup"><span data-stu-id="65139-109">[out] A pointer to a `ULONG32` that receives the offsets.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="65139-110">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="65139-110">Return Value</span></span>  
 <span data-ttu-id="65139-111">S_OK, jeśli metoda się powiedzie; w przeciwnym razie E_FAIL lub innego kodu błędu.</span><span class="sxs-lookup"><span data-stu-id="65139-111">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="65139-112">Wymagania</span><span class="sxs-lookup"><span data-stu-id="65139-112">Requirements</span></span>  
 <span data-ttu-id="65139-113">**Nagłówek:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="65139-113">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="65139-114">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="65139-114">See also</span></span>

- [<span data-ttu-id="65139-115">ISymUnmanagedMethod, interfejs</span><span class="sxs-lookup"><span data-stu-id="65139-115">ISymUnmanagedMethod Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedmethod-interface.md)
