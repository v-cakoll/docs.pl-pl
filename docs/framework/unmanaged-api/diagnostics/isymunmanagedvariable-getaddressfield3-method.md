---
title: ISymUnmanagedVariable::GetAddressField3 — Metoda
ms.date: 03/30/2017
api_name:
- ISymUnmanagedVariable.GetAddressField3
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedVariable::GetAddressField3
helpviewer_keywords:
- ISymUnmanagedVariable::GetAddressField3 method [.NET Framework debugging]
- GetAddressField3 method [.NET Framework debugging]
ms.assetid: 4d834721-ad8d-439d-b356-c6b4aef022fc
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: c8b03b96c8cab43046d109d0dd11ae135cb70c9f
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59163612"
---
# <a name="isymunmanagedvariablegetaddressfield3-method"></a><span data-ttu-id="1f4b1-102">ISymUnmanagedVariable::GetAddressField3 — Metoda</span><span class="sxs-lookup"><span data-stu-id="1f4b1-102">ISymUnmanagedVariable::GetAddressField3 Method</span></span>
<span data-ttu-id="1f4b1-103">Pobiera trzecim polu adresów dla tej zmiennej.</span><span class="sxs-lookup"><span data-stu-id="1f4b1-103">Gets the third address field for this variable.</span></span> <span data-ttu-id="1f4b1-104">Znaczenia, zależy od rodzaju adresu.</span><span class="sxs-lookup"><span data-stu-id="1f4b1-104">Its meaning depends on the kind of address.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1f4b1-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="1f4b1-105">Syntax</span></span>  
  
```  
HRESULT GetAddressField3(  
    [out, retval] ULONG32* pRetVal);  
```  
  
## <a name="parameters"></a><span data-ttu-id="1f4b1-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="1f4b1-106">Parameters</span></span>  
 `pRetVal`  
 <span data-ttu-id="1f4b1-107">[out] Wskaźnik do `ULONG32` odbierająca trzecim polu adresu.</span><span class="sxs-lookup"><span data-stu-id="1f4b1-107">[out] A pointer to a `ULONG32` that receives the third address field.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="1f4b1-108">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="1f4b1-108">Return Value</span></span>  
 <span data-ttu-id="1f4b1-109">S_OK, jeśli metoda się powiedzie; w przeciwnym razie E_FAIL lub innego kodu błędu.</span><span class="sxs-lookup"><span data-stu-id="1f4b1-109">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1f4b1-110">Wymagania</span><span class="sxs-lookup"><span data-stu-id="1f4b1-110">Requirements</span></span>  
 <span data-ttu-id="1f4b1-111">**Nagłówek:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="1f4b1-111">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1f4b1-112">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="1f4b1-112">See also</span></span>

- [<span data-ttu-id="1f4b1-113">ISymUnmanagedVariable, interfejs</span><span class="sxs-lookup"><span data-stu-id="1f4b1-113">ISymUnmanagedVariable Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedvariable-interface.md)
- [<span data-ttu-id="1f4b1-114">GetAddressField1, metoda</span><span class="sxs-lookup"><span data-stu-id="1f4b1-114">GetAddressField1 Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedvariable-getaddressfield1-method.md)
- [<span data-ttu-id="1f4b1-115">GetAddressField2, metoda</span><span class="sxs-lookup"><span data-stu-id="1f4b1-115">GetAddressField2 Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedvariable-getaddressfield2-method.md)
- [<span data-ttu-id="1f4b1-116">GetAddressKind, metoda</span><span class="sxs-lookup"><span data-stu-id="1f4b1-116">GetAddressKind Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedvariable-getaddresskind-method.md)
