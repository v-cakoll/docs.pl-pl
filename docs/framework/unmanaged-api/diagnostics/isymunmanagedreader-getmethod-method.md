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
ms.openlocfilehash: deb5d7aa24cf750a9584ef2aa32d10816ec12f57
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54614409"
---
# <a name="isymunmanagedreadergetmethod-method"></a><span data-ttu-id="bd311-102">ISymUnmanagedReader::GetMethod — Metoda</span><span class="sxs-lookup"><span data-stu-id="bd311-102">ISymUnmanagedReader::GetMethod Method</span></span>
<span data-ttu-id="bd311-103">Pobiera metodę czytnika symboli podany token metody.</span><span class="sxs-lookup"><span data-stu-id="bd311-103">Gets a symbol reader method, given a method token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bd311-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="bd311-104">Syntax</span></span>  
  
```  
HRESULT GetMethod (  
    [in]  mdMethodDef  token,  
    [out, retval] ISymUnmanagedMethod**  pRetVal);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="bd311-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="bd311-105">Parameters</span></span>  
 `token`  
 <span data-ttu-id="bd311-106">[in] Token metody.</span><span class="sxs-lookup"><span data-stu-id="bd311-106">[in] The method token.</span></span>  
  
 `pRetVal`  
 <span data-ttu-id="bd311-107">[out] Wskaźnik do interfejsu zwrócone.</span><span class="sxs-lookup"><span data-stu-id="bd311-107">[out] A pointer to the returned interface.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="bd311-108">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="bd311-108">Return Value</span></span>  
 <span data-ttu-id="bd311-109">S_OK, jeśli metoda się powiedzie; w przeciwnym razie E_FAIL lub innego kodu błędu.</span><span class="sxs-lookup"><span data-stu-id="bd311-109">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="bd311-110">Wymagania</span><span class="sxs-lookup"><span data-stu-id="bd311-110">Requirements</span></span>  
 <span data-ttu-id="bd311-111">**Nagłówek:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="bd311-111">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bd311-112">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="bd311-112">See also</span></span>
- [<span data-ttu-id="bd311-113">ISymUnmanagedReader, interfejs</span><span class="sxs-lookup"><span data-stu-id="bd311-113">ISymUnmanagedReader Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-interface.md)
