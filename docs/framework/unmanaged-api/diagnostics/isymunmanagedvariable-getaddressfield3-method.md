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
ms.openlocfilehash: dd474c7f149b8eff542b674c2ba6527b6a0cbcb7
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33427001"
---
# <a name="isymunmanagedvariablegetaddressfield3-method"></a><span data-ttu-id="e49f9-102">ISymUnmanagedVariable::GetAddressField3 — Metoda</span><span class="sxs-lookup"><span data-stu-id="e49f9-102">ISymUnmanagedVariable::GetAddressField3 Method</span></span>
<span data-ttu-id="e49f9-103">Pobiera trzecie pole adresu dla tej zmiennej.</span><span class="sxs-lookup"><span data-stu-id="e49f9-103">Gets the third address field for this variable.</span></span> <span data-ttu-id="e49f9-104">Znaczenia zależy od rodzaju adres.</span><span class="sxs-lookup"><span data-stu-id="e49f9-104">Its meaning depends on the kind of address.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e49f9-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="e49f9-105">Syntax</span></span>  
  
```  
HRESULT GetAddressField3(  
    [out, retval] ULONG32* pRetVal);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="e49f9-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="e49f9-106">Parameters</span></span>  
 `pRetVal`  
 <span data-ttu-id="e49f9-107">[out] Wskaźnik do `ULONG32` odbierająca pola trzeci adres.</span><span class="sxs-lookup"><span data-stu-id="e49f9-107">[out] A pointer to a `ULONG32` that receives the third address field.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="e49f9-108">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="e49f9-108">Return Value</span></span>  
 <span data-ttu-id="e49f9-109">Wartość S_OK, jeśli metoda zakończy się pomyślnie; w przeciwnym razie E_FAIL lub inny kod błędu.</span><span class="sxs-lookup"><span data-stu-id="e49f9-109">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e49f9-110">Wymagania</span><span class="sxs-lookup"><span data-stu-id="e49f9-110">Requirements</span></span>  
 <span data-ttu-id="e49f9-111">**Header:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="e49f9-111">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e49f9-112">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="e49f9-112">See Also</span></span>  
 [<span data-ttu-id="e49f9-113">ISymUnmanagedVariable, interfejs</span><span class="sxs-lookup"><span data-stu-id="e49f9-113">ISymUnmanagedVariable Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedvariable-interface.md)  
 [<span data-ttu-id="e49f9-114">GetAddressField1, metoda</span><span class="sxs-lookup"><span data-stu-id="e49f9-114">GetAddressField1 Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedvariable-getaddressfield1-method.md)  
 [<span data-ttu-id="e49f9-115">GetAddressField2, metoda</span><span class="sxs-lookup"><span data-stu-id="e49f9-115">GetAddressField2 Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedvariable-getaddressfield2-method.md)  
 [<span data-ttu-id="e49f9-116">GetAddressKind, metoda</span><span class="sxs-lookup"><span data-stu-id="e49f9-116">GetAddressKind Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedvariable-getaddresskind-method.md)
