---
title: "ISymUnmanagedVariable::GetAddressField1 — Metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ISymUnmanagedVariable.GetAddressField1
api_location: diasymreader.dll
api_type: COM
f1_keywords: ISymUnmanagedVariable::GetAddressField1
helpviewer_keywords:
- GetAddressField1 method [.NET Framework debugging]
- ISymUnmanagedVariable::GetAddressField1 method [.NET Framework debugging]
ms.assetid: 25788ed1-0ce3-4b97-96fc-88f8997812a3
topic_type: apiref
caps.latest.revision: "9"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 460535813ed684424ae51710f09c731505805773
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="isymunmanagedvariablegetaddressfield1-method"></a><span data-ttu-id="5df85-102">ISymUnmanagedVariable::GetAddressField1 — Metoda</span><span class="sxs-lookup"><span data-stu-id="5df85-102">ISymUnmanagedVariable::GetAddressField1 Method</span></span>
<span data-ttu-id="5df85-103">Pobiera pierwsze pole adresu dla tej zmiennej.</span><span class="sxs-lookup"><span data-stu-id="5df85-103">Gets the first address field for this variable.</span></span> <span data-ttu-id="5df85-104">Znaczenia zależy od rodzaju adres.</span><span class="sxs-lookup"><span data-stu-id="5df85-104">Its meaning depends on the kind of address.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5df85-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="5df85-105">Syntax</span></span>  
  
```  
HRESULT GetAddressField1(  
    [out, retval] ULONG32* pRetVal);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="5df85-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="5df85-106">Parameters</span></span>  
 `pRetVal`  
 <span data-ttu-id="5df85-107">[out] Wskaźnik do `ULONG32` odbierająca pierwsze pole adresu.</span><span class="sxs-lookup"><span data-stu-id="5df85-107">[out] A pointer to a `ULONG32` that receives the first address field.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="5df85-108">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="5df85-108">Return Value</span></span>  
 <span data-ttu-id="5df85-109">Wartość S_OK, jeśli metoda zakończy się pomyślnie; w przeciwnym razie E_FAIL lub inny kod błędu.</span><span class="sxs-lookup"><span data-stu-id="5df85-109">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5df85-110">Wymagania</span><span class="sxs-lookup"><span data-stu-id="5df85-110">Requirements</span></span>  
 <span data-ttu-id="5df85-111">**Nagłówek:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="5df85-111">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5df85-112">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="5df85-112">See Also</span></span>  
 [<span data-ttu-id="5df85-113">ISymUnmanagedVariable — interfejs</span><span class="sxs-lookup"><span data-stu-id="5df85-113">ISymUnmanagedVariable Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedvariable-interface.md)  
 [<span data-ttu-id="5df85-114">GetAddressField2 — metoda</span><span class="sxs-lookup"><span data-stu-id="5df85-114">GetAddressField2 Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedvariable-getaddressfield2-method.md)  
 [<span data-ttu-id="5df85-115">GetAddressField3 — metoda</span><span class="sxs-lookup"><span data-stu-id="5df85-115">GetAddressField3 Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedvariable-getaddressfield3-method.md)  
 [<span data-ttu-id="5df85-116">GetAddressKind — metoda</span><span class="sxs-lookup"><span data-stu-id="5df85-116">GetAddressKind Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedvariable-getaddresskind-method.md)
