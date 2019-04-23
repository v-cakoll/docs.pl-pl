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
ms.openlocfilehash: ab6228866434b35525b16e97b8cba718b849dea1
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59213210"
---
# <a name="isymunmanagedreadergetmethod-method"></a><span data-ttu-id="26e3e-102">ISymUnmanagedReader::GetMethod — Metoda</span><span class="sxs-lookup"><span data-stu-id="26e3e-102">ISymUnmanagedReader::GetMethod Method</span></span>
<span data-ttu-id="26e3e-103">Pobiera metodę czytnika symboli podany token metody.</span><span class="sxs-lookup"><span data-stu-id="26e3e-103">Gets a symbol reader method, given a method token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="26e3e-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="26e3e-104">Syntax</span></span>  
  
```  
HRESULT GetMethod (  
    [in]  mdMethodDef  token,  
    [out, retval] ISymUnmanagedMethod**  pRetVal);  
```  
  
## <a name="parameters"></a><span data-ttu-id="26e3e-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="26e3e-105">Parameters</span></span>  
 `token`  
 <span data-ttu-id="26e3e-106">[in] Token metody.</span><span class="sxs-lookup"><span data-stu-id="26e3e-106">[in] The method token.</span></span>  
  
 `pRetVal`  
 <span data-ttu-id="26e3e-107">[out] Wskaźnik do interfejsu zwrócone.</span><span class="sxs-lookup"><span data-stu-id="26e3e-107">[out] A pointer to the returned interface.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="26e3e-108">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="26e3e-108">Return Value</span></span>  
 <span data-ttu-id="26e3e-109">S_OK, jeśli metoda się powiedzie; w przeciwnym razie E_FAIL lub innego kodu błędu.</span><span class="sxs-lookup"><span data-stu-id="26e3e-109">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="26e3e-110">Wymagania</span><span class="sxs-lookup"><span data-stu-id="26e3e-110">Requirements</span></span>  
 <span data-ttu-id="26e3e-111">**Nagłówek:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="26e3e-111">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="26e3e-112">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="26e3e-112">See also</span></span>

- [<span data-ttu-id="26e3e-113">ISymUnmanagedReader, interfejs</span><span class="sxs-lookup"><span data-stu-id="26e3e-113">ISymUnmanagedReader Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-interface.md)
