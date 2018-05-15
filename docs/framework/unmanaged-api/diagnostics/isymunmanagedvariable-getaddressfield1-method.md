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
ms.openlocfilehash: f9e0e234a8f77ef35ad93302fe8fc676cf9dbaeb
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="isymunmanagedvariablegetaddressfield1-method"></a><span data-ttu-id="d4af6-102">ISymUnmanagedVariable::GetAddressField1 — Metoda</span><span class="sxs-lookup"><span data-stu-id="d4af6-102">ISymUnmanagedVariable::GetAddressField1 Method</span></span>
<span data-ttu-id="d4af6-103">Pobiera pierwsze pole adresu dla tej zmiennej.</span><span class="sxs-lookup"><span data-stu-id="d4af6-103">Gets the first address field for this variable.</span></span> <span data-ttu-id="d4af6-104">Znaczenia zależy od rodzaju adres.</span><span class="sxs-lookup"><span data-stu-id="d4af6-104">Its meaning depends on the kind of address.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d4af6-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="d4af6-105">Syntax</span></span>  
  
```  
HRESULT GetAddressField1(  
    [out, retval] ULONG32* pRetVal);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="d4af6-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="d4af6-106">Parameters</span></span>  
 `pRetVal`  
 <span data-ttu-id="d4af6-107">[out] Wskaźnik do `ULONG32` odbierająca pierwsze pole adresu.</span><span class="sxs-lookup"><span data-stu-id="d4af6-107">[out] A pointer to a `ULONG32` that receives the first address field.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="d4af6-108">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="d4af6-108">Return Value</span></span>  
 <span data-ttu-id="d4af6-109">Wartość S_OK, jeśli metoda zakończy się pomyślnie; w przeciwnym razie E_FAIL lub inny kod błędu.</span><span class="sxs-lookup"><span data-stu-id="d4af6-109">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d4af6-110">Wymagania</span><span class="sxs-lookup"><span data-stu-id="d4af6-110">Requirements</span></span>  
 <span data-ttu-id="d4af6-111">**Header:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="d4af6-111">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d4af6-112">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="d4af6-112">See Also</span></span>  
 [<span data-ttu-id="d4af6-113">ISymUnmanagedVariable, interfejs</span><span class="sxs-lookup"><span data-stu-id="d4af6-113">ISymUnmanagedVariable Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedvariable-interface.md)  
 [<span data-ttu-id="d4af6-114">GetAddressField2, metoda</span><span class="sxs-lookup"><span data-stu-id="d4af6-114">GetAddressField2 Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedvariable-getaddressfield2-method.md)  
 [<span data-ttu-id="d4af6-115">GetAddressField3, metoda</span><span class="sxs-lookup"><span data-stu-id="d4af6-115">GetAddressField3 Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedvariable-getaddressfield3-method.md)  
 [<span data-ttu-id="d4af6-116">GetAddressKind, metoda</span><span class="sxs-lookup"><span data-stu-id="d4af6-116">GetAddressKind Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedvariable-getaddresskind-method.md)
