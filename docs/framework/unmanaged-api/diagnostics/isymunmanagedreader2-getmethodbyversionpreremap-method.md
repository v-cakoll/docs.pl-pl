---
title: ISymUnmanagedReader2::GetMethodByVersionPreRemap — Metoda
ms.date: 03/30/2017
api_name:
- ISymUnmanagedReader2.GetMethodByVersionPreRemap
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedReader2::GetMethodByVersionPreRemap
helpviewer_keywords:
- GetMethodByVersionPreRemap method [.NET Framework debugging]
- ISymUnmanagedReader2::GetMethodByVersionPreRemap method [.NET Framework debugging]
ms.assetid: 0d144ed4-bdb0-4cac-960c-cb90f4dca173
topic_type:
- apiref
ms.openlocfilehash: b12ecfdaf7c90589ce2e96b39f7437444cb91b09
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/19/2020
ms.locfileid: "83615426"
---
# <a name="isymunmanagedreader2getmethodbyversionpreremap-method"></a><span data-ttu-id="40c83-102">ISymUnmanagedReader2::GetMethodByVersionPreRemap — Metoda</span><span class="sxs-lookup"><span data-stu-id="40c83-102">ISymUnmanagedReader2::GetMethodByVersionPreRemap Method</span></span>
<span data-ttu-id="40c83-103">Pobiera metodę czytnika symboli, używając tokenu metody oraz numeru wersji Edit-and-Continue.</span><span class="sxs-lookup"><span data-stu-id="40c83-103">Gets a symbol reader method, given a method token and an edit-and-continue version number.</span></span> <span data-ttu-id="40c83-104">Numery wersji zaczynają się od 1 i zwiększają się za każdym razem, gdy metoda zostanie zmieniona w wyniku operacji Edit-and-Continue.</span><span class="sxs-lookup"><span data-stu-id="40c83-104">Version numbers start at 1 and are incremented each time the method is changed as a result of an edit-and-continue operation.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="40c83-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="40c83-105">Syntax</span></span>  
  
```cpp  
HRESULT GetMethodByVersionPreRemap(  
    [in]  mdMethodDef token,  
    [in]  int version,  
    [out, retval] ISymUnmanagedMethod** pRetVal);  
```  
  
## <a name="parameters"></a><span data-ttu-id="40c83-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="40c83-106">Parameters</span></span>  
 `token`  
 <span data-ttu-id="40c83-107">podczas Token metadanych metody.</span><span class="sxs-lookup"><span data-stu-id="40c83-107">[in] The method metadata token.</span></span>  
  
 `version`  
 <span data-ttu-id="40c83-108">podczas Wersja metody.</span><span class="sxs-lookup"><span data-stu-id="40c83-108">[in] The method version.</span></span>  
  
 `pRetVal`  
 <span data-ttu-id="40c83-109">określoną Wskaźnik do zwracanego interfejsu [ISymUnmanagedMethod](isymunmanagedmethod-interface.md) .</span><span class="sxs-lookup"><span data-stu-id="40c83-109">[out] A pointer to the returned [ISymUnmanagedMethod](isymunmanagedmethod-interface.md) interface.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="40c83-110">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="40c83-110">Return Value</span></span>  
 <span data-ttu-id="40c83-111">S_OK, jeśli metoda się powiedzie; w przeciwnym razie E_FAIL lub inny kod błędu.</span><span class="sxs-lookup"><span data-stu-id="40c83-111">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="40c83-112">Wymagania</span><span class="sxs-lookup"><span data-stu-id="40c83-112">Requirements</span></span>  
 <span data-ttu-id="40c83-113">**Nagłówek:** CorSym. idl.</span><span class="sxs-lookup"><span data-stu-id="40c83-113">**Header:** CorSym.idl.</span></span> <span data-ttu-id="40c83-114">CorSym. h</span><span class="sxs-lookup"><span data-stu-id="40c83-114">CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="40c83-115">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="40c83-115">See also</span></span>

- [<span data-ttu-id="40c83-116">ISymUnmanagedReader2 — Interfejs</span><span class="sxs-lookup"><span data-stu-id="40c83-116">ISymUnmanagedReader2 Interface</span></span>](isymunmanagedreader2-interface.md)
