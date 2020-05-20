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
ms.openlocfilehash: 253fd17178c03bc0c4d8ea031888a404ad56f876
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/19/2020
ms.locfileid: "83615283"
---
# <a name="isymunmanagedvariablegetaddressfield1-method"></a><span data-ttu-id="eaa82-102">ISymUnmanagedVariable::GetAddressField1 — Metoda</span><span class="sxs-lookup"><span data-stu-id="eaa82-102">ISymUnmanagedVariable::GetAddressField1 Method</span></span>
<span data-ttu-id="eaa82-103">Pobiera pierwsze pole adresu dla tej zmiennej.</span><span class="sxs-lookup"><span data-stu-id="eaa82-103">Gets the first address field for this variable.</span></span> <span data-ttu-id="eaa82-104">Jego znaczenie zależy od rodzaju adresu.</span><span class="sxs-lookup"><span data-stu-id="eaa82-104">Its meaning depends on the kind of address.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="eaa82-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="eaa82-105">Syntax</span></span>  
  
```cpp  
HRESULT GetAddressField1(  
    [out, retval] ULONG32* pRetVal);  
```  
  
## <a name="parameters"></a><span data-ttu-id="eaa82-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="eaa82-106">Parameters</span></span>  
 `pRetVal`  
 <span data-ttu-id="eaa82-107">określoną Wskaźnik do elementu `ULONG32` , który odbiera pierwsze pole adresu.</span><span class="sxs-lookup"><span data-stu-id="eaa82-107">[out] A pointer to a `ULONG32` that receives the first address field.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="eaa82-108">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="eaa82-108">Return Value</span></span>  
 <span data-ttu-id="eaa82-109">S_OK, jeśli metoda się powiedzie; w przeciwnym razie E_FAIL lub inny kod błędu.</span><span class="sxs-lookup"><span data-stu-id="eaa82-109">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="eaa82-110">Wymagania</span><span class="sxs-lookup"><span data-stu-id="eaa82-110">Requirements</span></span>  
 <span data-ttu-id="eaa82-111">**Nagłówek:** CorSym. idl, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="eaa82-111">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="eaa82-112">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="eaa82-112">See also</span></span>

- [<span data-ttu-id="eaa82-113">ISymUnmanagedVariable, interfejs</span><span class="sxs-lookup"><span data-stu-id="eaa82-113">ISymUnmanagedVariable Interface</span></span>](isymunmanagedvariable-interface.md)
- [<span data-ttu-id="eaa82-114">GetAddressField2, metoda</span><span class="sxs-lookup"><span data-stu-id="eaa82-114">GetAddressField2 Method</span></span>](isymunmanagedvariable-getaddressfield2-method.md)
- [<span data-ttu-id="eaa82-115">GetAddressField3, metoda</span><span class="sxs-lookup"><span data-stu-id="eaa82-115">GetAddressField3 Method</span></span>](isymunmanagedvariable-getaddressfield3-method.md)
- [<span data-ttu-id="eaa82-116">GetAddressKind, metoda</span><span class="sxs-lookup"><span data-stu-id="eaa82-116">GetAddressKind Method</span></span>](isymunmanagedvariable-getaddresskind-method.md)
