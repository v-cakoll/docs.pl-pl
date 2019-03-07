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
ms.openlocfilehash: 796a71ac941497801c749295fb2f6bb201547bd7
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/06/2019
ms.locfileid: "57478313"
---
# <a name="isymunmanagedvariablegetaddressfield1-method"></a><span data-ttu-id="f72e0-102">ISymUnmanagedVariable::GetAddressField1 — Metoda</span><span class="sxs-lookup"><span data-stu-id="f72e0-102">ISymUnmanagedVariable::GetAddressField1 Method</span></span>
<span data-ttu-id="f72e0-103">Pobiera pierwsze pole Adres dla tej zmiennej.</span><span class="sxs-lookup"><span data-stu-id="f72e0-103">Gets the first address field for this variable.</span></span> <span data-ttu-id="f72e0-104">Znaczenia, zależy od rodzaju adresu.</span><span class="sxs-lookup"><span data-stu-id="f72e0-104">Its meaning depends on the kind of address.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f72e0-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="f72e0-105">Syntax</span></span>  
  
```  
HRESULT GetAddressField1(  
    [out, retval] ULONG32* pRetVal);  
```  
  
## <a name="parameters"></a><span data-ttu-id="f72e0-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="f72e0-106">Parameters</span></span>  
 `pRetVal`  
 <span data-ttu-id="f72e0-107">[out] Wskaźnik do `ULONG32` odbierająca na pierwsze pole adres.</span><span class="sxs-lookup"><span data-stu-id="f72e0-107">[out] A pointer to a `ULONG32` that receives the first address field.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="f72e0-108">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="f72e0-108">Return Value</span></span>  
 <span data-ttu-id="f72e0-109">S_OK, jeśli metoda się powiedzie; w przeciwnym razie E_FAIL lub innego kodu błędu.</span><span class="sxs-lookup"><span data-stu-id="f72e0-109">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f72e0-110">Wymagania</span><span class="sxs-lookup"><span data-stu-id="f72e0-110">Requirements</span></span>  
 <span data-ttu-id="f72e0-111">**Nagłówek:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="f72e0-111">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f72e0-112">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="f72e0-112">See also</span></span>
- [<span data-ttu-id="f72e0-113">ISymUnmanagedVariable, interfejs</span><span class="sxs-lookup"><span data-stu-id="f72e0-113">ISymUnmanagedVariable Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedvariable-interface.md)
- [<span data-ttu-id="f72e0-114">GetAddressField2, metoda</span><span class="sxs-lookup"><span data-stu-id="f72e0-114">GetAddressField2 Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedvariable-getaddressfield2-method.md)
- [<span data-ttu-id="f72e0-115">GetAddressField3, metoda</span><span class="sxs-lookup"><span data-stu-id="f72e0-115">GetAddressField3 Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedvariable-getaddressfield3-method.md)
- [<span data-ttu-id="f72e0-116">GetAddressKind, metoda</span><span class="sxs-lookup"><span data-stu-id="f72e0-116">GetAddressKind Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedvariable-getaddresskind-method.md)
