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
ms.openlocfilehash: 979d14b4c404c3bf12c427bd5b8b1d4997805e7b
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59160683"
---
# <a name="isymunmanagedwriterremaptoken-method"></a><span data-ttu-id="155b8-102">ISymUnmanagedWriter::RemapToken — Metoda</span><span class="sxs-lookup"><span data-stu-id="155b8-102">ISymUnmanagedWriter::RemapToken Method</span></span>
<span data-ttu-id="155b8-103">Powiadamia moduł zapisujący symboli, czy token metadanych ma został ponownie mapowany jako metadane zostały wyemitowane.</span><span class="sxs-lookup"><span data-stu-id="155b8-103">Notifies the symbol writer that a metadata token has been remapped as the metadata was emitted.</span></span> <span data-ttu-id="155b8-104">Jeśli moduł zapisujący symbol ma być przechowywany stary token w magazynie symboli, musi ona albo zaktualizować przechowywanych token z nową wartością lub go najpierw zapisać mapy dla odpowiedniego czytnika symboli ponownie zamapować fazie odczytu.</span><span class="sxs-lookup"><span data-stu-id="155b8-104">If the symbol writer has stored the old token within the symbol store, it must either update the stored token with the new value, or it must save the map for the corresponding symbol reader to remap during the read phase.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="155b8-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="155b8-105">Syntax</span></span>  
  
```  
HRESULT RemapToken(  
    [in] mdToken  oldToken,  
    [in] mdToken  newToken);  
```  
  
## <a name="parameters"></a><span data-ttu-id="155b8-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="155b8-106">Parameters</span></span>  
 `oldToken`  
 <span data-ttu-id="155b8-107">[in] Token metadanych, który został ponownie mapowany.</span><span class="sxs-lookup"><span data-stu-id="155b8-107">[in] The metadata token that was remapped.</span></span>  
  
 `newToken`  
 <span data-ttu-id="155b8-108">[in] Nowy token metadanych, do którego `oldToken` został ponownie mapowany.</span><span class="sxs-lookup"><span data-stu-id="155b8-108">[in] The new metadata token to which `oldToken` was remapped.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="155b8-109">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="155b8-109">Return Value</span></span>  
 <span data-ttu-id="155b8-110">S_OK, jeśli metoda się powiedzie; w przeciwnym razie E_FAIL lub innego kodu błędu.</span><span class="sxs-lookup"><span data-stu-id="155b8-110">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="155b8-111">Wymagania</span><span class="sxs-lookup"><span data-stu-id="155b8-111">Requirements</span></span>  
 <span data-ttu-id="155b8-112">**Nagłówek:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="155b8-112">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="155b8-113">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="155b8-113">See also</span></span>

- [<span data-ttu-id="155b8-114">ISymUnmanagedWriter, interfejs</span><span class="sxs-lookup"><span data-stu-id="155b8-114">ISymUnmanagedWriter Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-interface.md)
