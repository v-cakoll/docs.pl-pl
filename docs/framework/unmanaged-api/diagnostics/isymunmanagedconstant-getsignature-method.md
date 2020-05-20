---
title: ISymUnmanagedConstant::GetSignature — Metoda
ms.date: 03/30/2017
api_name:
- ISymUnmanagedConstant.GetSignature
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedConstant::GetSignature
helpviewer_keywords:
- GetSignature method, ISymUnmanagedConstant interface [.NET Framework debugging]
- ISymUnmanagedConstant::GetSignature method [.NET Framework debugging]
ms.assetid: 3eb41151-a228-43e3-ba8f-e6dd3ceb8542
topic_type:
- apiref
ms.openlocfilehash: 332d60418c744a9391c7c0afc20248c2239b090c
ms.sourcegitcommit: 7b1497c1927cb449cefd313bc5126ae37df30746
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/16/2020
ms.locfileid: "83441623"
---
# <a name="isymunmanagedconstantgetsignature-method"></a><span data-ttu-id="3a5cc-102">ISymUnmanagedConstant::GetSignature — Metoda</span><span class="sxs-lookup"><span data-stu-id="3a5cc-102">ISymUnmanagedConstant::GetSignature Method</span></span>
<span data-ttu-id="3a5cc-103">Pobiera sygnaturę stałej.</span><span class="sxs-lookup"><span data-stu-id="3a5cc-103">Gets the signature of the constant.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3a5cc-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="3a5cc-104">Syntax</span></span>  
  
```cpp  
HRESULT GetSignature(  
    [in]  ULONG32  cSig,  
    [out] ULONG32  *pcSig,  
    [out, size_is(cSig),  
        length_is(*pcSig)] BYTE sig[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="3a5cc-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="3a5cc-105">Parameters</span></span>  
 `cSig`  
 <span data-ttu-id="3a5cc-106">podczas Długość buforu, `pcSig` do którego wskazuje parametr.</span><span class="sxs-lookup"><span data-stu-id="3a5cc-106">[in] The length of the buffer that the `pcSig` parameter points to.</span></span>  
  
 `pcSig`  
 <span data-ttu-id="3a5cc-107">określoną Wskaźnik do obiektu, `ULONG32` który odbiera rozmiar (w znakach) bufora wymaganego do zawierania podpisu.</span><span class="sxs-lookup"><span data-stu-id="3a5cc-107">[out] A pointer to a `ULONG32` that receives the size, in characters, of the buffer required to contain the signature.</span></span>  
  
 `sig`  
 <span data-ttu-id="3a5cc-108">określoną Bufor przechowujący podpis.</span><span class="sxs-lookup"><span data-stu-id="3a5cc-108">[out] The buffer that stores the signature.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="3a5cc-109">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="3a5cc-109">Return Value</span></span>  
 <span data-ttu-id="3a5cc-110">S_OK, jeśli metoda się powiedzie; w przeciwnym razie E_FAIL lub inny kod błędu.</span><span class="sxs-lookup"><span data-stu-id="3a5cc-110">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3a5cc-111">Wymagania</span><span class="sxs-lookup"><span data-stu-id="3a5cc-111">Requirements</span></span>  
 <span data-ttu-id="3a5cc-112">**Nagłówek:** CorSym. idl, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="3a5cc-112">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3a5cc-113">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="3a5cc-113">See also</span></span>

- [<span data-ttu-id="3a5cc-114">ISymUnmanagedConstant — Interfejs</span><span class="sxs-lookup"><span data-stu-id="3a5cc-114">ISymUnmanagedConstant Interface</span></span>](isymunmanagedconstant-interface.md)
- [<span data-ttu-id="3a5cc-115">GetName — Metoda</span><span class="sxs-lookup"><span data-stu-id="3a5cc-115">GetName Method</span></span>](isymunmanagedconstant-getname-method.md)
- [<span data-ttu-id="3a5cc-116">GetValue — Metoda</span><span class="sxs-lookup"><span data-stu-id="3a5cc-116">GetValue Method</span></span>](isymunmanagedconstant-getvalue-method.md)
