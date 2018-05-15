---
title: ISymUnmanagedWriter::RemapToken — Metoda
ms.date: 03/30/2017
api_name:
- ISymUnmanagedWriter.RemapToken
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedWriter::RemapToken
helpviewer_keywords:
- ISymUnmanagedWriter::RemapToken method [.NET Framework debugging]
- RemapToken method [.NET Framework debugging]
ms.assetid: bca92682-ee1e-467f-8fb0-d8d4617f82fe
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: f37630c9631e2e76d9b98730b84086b8b86ec55d
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="isymunmanagedwriterremaptoken-method"></a><span data-ttu-id="e3688-102">ISymUnmanagedWriter::RemapToken — Metoda</span><span class="sxs-lookup"><span data-stu-id="e3688-102">ISymUnmanagedWriter::RemapToken Method</span></span>
<span data-ttu-id="e3688-103">Powiadamia twórcę symbolu, że token metadanych ma przeprowadzono ponowne mapowanie udziałów jak metadanych zostały wyemitowane.</span><span class="sxs-lookup"><span data-stu-id="e3688-103">Notifies the symbol writer that a metadata token has been remapped as the metadata was emitted.</span></span> <span data-ttu-id="e3688-104">Jeśli moduł zapisujący symbol przechowywanych stary token w magazynie symboli, musi albo aktualizacji przechowywanych token z nową wartością lub go zapisać mapy dla odpowiedniego czytnika symboli ponownie zamapować podczas fazy odczytu.</span><span class="sxs-lookup"><span data-stu-id="e3688-104">If the symbol writer has stored the old token within the symbol store, it must either update the stored token with the new value, or it must save the map for the corresponding symbol reader to remap during the read phase.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e3688-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="e3688-105">Syntax</span></span>  
  
```  
HRESULT RemapToken(  
    [in] mdToken  oldToken,  
    [in] mdToken  newToken);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="e3688-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="e3688-106">Parameters</span></span>  
 `oldToken`  
 <span data-ttu-id="e3688-107">[in] Token metadanych, które zostało zmienione.</span><span class="sxs-lookup"><span data-stu-id="e3688-107">[in] The metadata token that was remapped.</span></span>  
  
 `newToken`  
 <span data-ttu-id="e3688-108">[in] Nowy token metadanych, do którego `oldToken` zostało zmienione.</span><span class="sxs-lookup"><span data-stu-id="e3688-108">[in] The new metadata token to which `oldToken` was remapped.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="e3688-109">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="e3688-109">Return Value</span></span>  
 <span data-ttu-id="e3688-110">Wartość S_OK, jeśli metoda zakończy się pomyślnie; w przeciwnym razie E_FAIL lub inny kod błędu.</span><span class="sxs-lookup"><span data-stu-id="e3688-110">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e3688-111">Wymagania</span><span class="sxs-lookup"><span data-stu-id="e3688-111">Requirements</span></span>  
 <span data-ttu-id="e3688-112">**Header:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="e3688-112">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e3688-113">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="e3688-113">See Also</span></span>  
 [<span data-ttu-id="e3688-114">ISymUnmanagedWriter, interfejs</span><span class="sxs-lookup"><span data-stu-id="e3688-114">ISymUnmanagedWriter Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-interface.md)
