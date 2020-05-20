---
title: ISymUnmanagedVariable::GetSignature — Metoda
ms.date: 03/30/2017
api_name:
- ISymUnmanagedVariable.GetSignature
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedVariable::GetSignature
helpviewer_keywords:
- GetSignature method, ISymUnmanagedVariable interface [.NET Framework debugging]
- ISymUnmanagedVariable::GetSignature method [.NET Framework debugging]
ms.assetid: 78c1ba28-a410-4360-805c-23a95408964a
topic_type:
- apiref
ms.openlocfilehash: a3ec0af33f3f1201ce2f6b62291dfc67696fecab
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/19/2020
ms.locfileid: "83610447"
---
# <a name="isymunmanagedvariablegetsignature-method"></a><span data-ttu-id="8b293-102">ISymUnmanagedVariable::GetSignature — Metoda</span><span class="sxs-lookup"><span data-stu-id="8b293-102">ISymUnmanagedVariable::GetSignature Method</span></span>
<span data-ttu-id="8b293-103">Pobiera sygnaturę tej zmiennej.</span><span class="sxs-lookup"><span data-stu-id="8b293-103">Gets the signature of this variable.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8b293-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="8b293-104">Syntax</span></span>  
  
```cpp  
HRESULT GetSignature(  
    [in]  ULONG32  cSig,  
    [out] ULONG32  *pcSig,  
    [out, size_is(cSig),  
        length_is(*pcSig)] BYTE sig[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="8b293-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="8b293-105">Parameters</span></span>  
 `cSig`  
 <span data-ttu-id="8b293-106">podczas Długość buforu wskazywanego przez `sig` parametr.</span><span class="sxs-lookup"><span data-stu-id="8b293-106">[in] The length of the buffer pointed to by the `sig` parameter.</span></span>  
  
 `pcSig`  
 <span data-ttu-id="8b293-107">określoną Wskaźnik do obiektu, `ULONG32` który odbiera rozmiar (w znakach) bufora wymaganego do zawierania podpisu.</span><span class="sxs-lookup"><span data-stu-id="8b293-107">[out] A pointer to a `ULONG32` that receives the size, in characters, of the buffer required to contain the signature.</span></span>  
  
 `sig`  
 <span data-ttu-id="8b293-108">określoną Bufor przechowujący podpis.</span><span class="sxs-lookup"><span data-stu-id="8b293-108">[out] The buffer that stores the signature.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="8b293-109">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="8b293-109">Return Value</span></span>  
 <span data-ttu-id="8b293-110">S_OK, jeśli metoda się powiedzie; w przeciwnym razie E_FAIL lub inny kod błędu.</span><span class="sxs-lookup"><span data-stu-id="8b293-110">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8b293-111">Wymagania</span><span class="sxs-lookup"><span data-stu-id="8b293-111">Requirements</span></span>  
 <span data-ttu-id="8b293-112">**Nagłówek:** CorSym. idl, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="8b293-112">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8b293-113">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="8b293-113">See also</span></span>

- [<span data-ttu-id="8b293-114">ISymUnmanagedVariable, interfejs</span><span class="sxs-lookup"><span data-stu-id="8b293-114">ISymUnmanagedVariable Interface</span></span>](isymunmanagedvariable-interface.md)
