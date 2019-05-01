---
title: ISymUnmanagedVariable::GetAddressField1 — Metoda
ms.date: 03/30/2017
api_name:
- ISymUnmanagedVariable.GetAddressField1
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedVariable::GetAddressField1
helpviewer_keywords:
- GetAddressField1 method [.NET Framework debugging]
- ISymUnmanagedVariable::GetAddressField1 method [.NET Framework debugging]
ms.assetid: 25788ed1-0ce3-4b97-96fc-88f8997812a3
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 67634024b04e82aa3a3c0b96dc260114c4c16371
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61797634"
---
# <a name="isymunmanagedvariablegetaddressfield1-method"></a><span data-ttu-id="a0197-102">ISymUnmanagedVariable::GetAddressField1 — Metoda</span><span class="sxs-lookup"><span data-stu-id="a0197-102">ISymUnmanagedVariable::GetAddressField1 Method</span></span>
<span data-ttu-id="a0197-103">Pobiera pierwsze pole Adres dla tej zmiennej.</span><span class="sxs-lookup"><span data-stu-id="a0197-103">Gets the first address field for this variable.</span></span> <span data-ttu-id="a0197-104">Znaczenia, zależy od rodzaju adresu.</span><span class="sxs-lookup"><span data-stu-id="a0197-104">Its meaning depends on the kind of address.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a0197-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="a0197-105">Syntax</span></span>  
  
```  
HRESULT GetAddressField1(  
    [out, retval] ULONG32* pRetVal);  
```  
  
## <a name="parameters"></a><span data-ttu-id="a0197-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="a0197-106">Parameters</span></span>  
 `pRetVal`  
 <span data-ttu-id="a0197-107">[out] Wskaźnik do `ULONG32` odbierająca na pierwsze pole adres.</span><span class="sxs-lookup"><span data-stu-id="a0197-107">[out] A pointer to a `ULONG32` that receives the first address field.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="a0197-108">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="a0197-108">Return Value</span></span>  
 <span data-ttu-id="a0197-109">S_OK, jeśli metoda się powiedzie; w przeciwnym razie E_FAIL lub innego kodu błędu.</span><span class="sxs-lookup"><span data-stu-id="a0197-109">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a0197-110">Wymagania</span><span class="sxs-lookup"><span data-stu-id="a0197-110">Requirements</span></span>  
 <span data-ttu-id="a0197-111">**Nagłówek:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="a0197-111">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a0197-112">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="a0197-112">See also</span></span>

- [<span data-ttu-id="a0197-113">ISymUnmanagedVariable, interfejs</span><span class="sxs-lookup"><span data-stu-id="a0197-113">ISymUnmanagedVariable Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedvariable-interface.md)
- [<span data-ttu-id="a0197-114">GetAddressField2, metoda</span><span class="sxs-lookup"><span data-stu-id="a0197-114">GetAddressField2 Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedvariable-getaddressfield2-method.md)
- [<span data-ttu-id="a0197-115">GetAddressField3, metoda</span><span class="sxs-lookup"><span data-stu-id="a0197-115">GetAddressField3 Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedvariable-getaddressfield3-method.md)
- [<span data-ttu-id="a0197-116">GetAddressKind, metoda</span><span class="sxs-lookup"><span data-stu-id="a0197-116">GetAddressKind Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedvariable-getaddresskind-method.md)
