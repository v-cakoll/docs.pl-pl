---
title: ISymUnmanagedReader::GetMethod — Metoda
ms.date: 03/30/2017
api_name:
- ISymUnmanagedReader.GetMethod
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedReader::GetMethod
helpviewer_keywords:
- GetMethod method, ISymUnmanagedReader interface [.NET Framework debugging]
- ISymUnmanagedReader::GetMethod method [.NET Framework debugging]
ms.assetid: ae6cfb29-bc2c-4606-af86-1d32ebd31020
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 031e51919d9abd7092756cc42fb35dcc0592758c
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/06/2019
ms.locfileid: "57503051"
---
# <a name="isymunmanagedreadergetmethod-method"></a><span data-ttu-id="e7f1c-102">ISymUnmanagedReader::GetMethod — Metoda</span><span class="sxs-lookup"><span data-stu-id="e7f1c-102">ISymUnmanagedReader::GetMethod Method</span></span>
<span data-ttu-id="e7f1c-103">Pobiera metodę czytnika symboli podany token metody.</span><span class="sxs-lookup"><span data-stu-id="e7f1c-103">Gets a symbol reader method, given a method token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e7f1c-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="e7f1c-104">Syntax</span></span>  
  
```  
HRESULT GetMethod (  
    [in]  mdMethodDef  token,  
    [out, retval] ISymUnmanagedMethod**  pRetVal);  
```  
  
## <a name="parameters"></a><span data-ttu-id="e7f1c-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="e7f1c-105">Parameters</span></span>  
 `token`  
 <span data-ttu-id="e7f1c-106">[in] Token metody.</span><span class="sxs-lookup"><span data-stu-id="e7f1c-106">[in] The method token.</span></span>  
  
 `pRetVal`  
 <span data-ttu-id="e7f1c-107">[out] Wskaźnik do interfejsu zwrócone.</span><span class="sxs-lookup"><span data-stu-id="e7f1c-107">[out] A pointer to the returned interface.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="e7f1c-108">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="e7f1c-108">Return Value</span></span>  
 <span data-ttu-id="e7f1c-109">S_OK, jeśli metoda się powiedzie; w przeciwnym razie E_FAIL lub innego kodu błędu.</span><span class="sxs-lookup"><span data-stu-id="e7f1c-109">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e7f1c-110">Wymagania</span><span class="sxs-lookup"><span data-stu-id="e7f1c-110">Requirements</span></span>  
 <span data-ttu-id="e7f1c-111">**Nagłówek:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="e7f1c-111">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e7f1c-112">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="e7f1c-112">See also</span></span>
- [<span data-ttu-id="e7f1c-113">ISymUnmanagedReader, interfejs</span><span class="sxs-lookup"><span data-stu-id="e7f1c-113">ISymUnmanagedReader Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-interface.md)
