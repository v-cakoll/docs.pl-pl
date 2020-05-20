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
ms.openlocfilehash: 864acb07797676c825afe62321b0d65e37938fa6
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/19/2020
ms.locfileid: "83615010"
---
# <a name="isymunmanagedreadergetmethod-method"></a><span data-ttu-id="1781a-102">ISymUnmanagedReader::GetMethod — Metoda</span><span class="sxs-lookup"><span data-stu-id="1781a-102">ISymUnmanagedReader::GetMethod Method</span></span>
<span data-ttu-id="1781a-103">Pobiera metodę czytnika symboli, używając tokenu metody.</span><span class="sxs-lookup"><span data-stu-id="1781a-103">Gets a symbol reader method, given a method token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1781a-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="1781a-104">Syntax</span></span>  
  
```cpp  
HRESULT GetMethod (  
    [in]  mdMethodDef  token,  
    [out, retval] ISymUnmanagedMethod**  pRetVal);  
```  
  
## <a name="parameters"></a><span data-ttu-id="1781a-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="1781a-105">Parameters</span></span>  
 `token`  
 <span data-ttu-id="1781a-106">podczas Token metody.</span><span class="sxs-lookup"><span data-stu-id="1781a-106">[in] The method token.</span></span>  
  
 `pRetVal`  
 <span data-ttu-id="1781a-107">określoną Wskaźnik do zwracanego interfejsu.</span><span class="sxs-lookup"><span data-stu-id="1781a-107">[out] A pointer to the returned interface.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="1781a-108">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="1781a-108">Return Value</span></span>  
 <span data-ttu-id="1781a-109">S_OK, jeśli metoda się powiedzie; w przeciwnym razie E_FAIL lub inny kod błędu.</span><span class="sxs-lookup"><span data-stu-id="1781a-109">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1781a-110">Wymagania</span><span class="sxs-lookup"><span data-stu-id="1781a-110">Requirements</span></span>  
 <span data-ttu-id="1781a-111">**Nagłówek:** CorSym. idl, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="1781a-111">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1781a-112">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="1781a-112">See also</span></span>

- [<span data-ttu-id="1781a-113">ISymUnmanagedReader — Interfejs</span><span class="sxs-lookup"><span data-stu-id="1781a-113">ISymUnmanagedReader Interface</span></span>](isymunmanagedreader-interface.md)
