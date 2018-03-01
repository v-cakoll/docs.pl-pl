---
title: "ISymUnmanagedVariable::GetAddressField1 — Metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
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
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 8085deb0cdb0b16eddfa39663277ceecdde10341
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="isymunmanagedvariablegetaddressfield1-method"></a><span data-ttu-id="fcec8-102">ISymUnmanagedVariable::GetAddressField1 — Metoda</span><span class="sxs-lookup"><span data-stu-id="fcec8-102">ISymUnmanagedVariable::GetAddressField1 Method</span></span>
<span data-ttu-id="fcec8-103">Pobiera pierwsze pole adresu dla tej zmiennej.</span><span class="sxs-lookup"><span data-stu-id="fcec8-103">Gets the first address field for this variable.</span></span> <span data-ttu-id="fcec8-104">Znaczenia zależy od rodzaju adres.</span><span class="sxs-lookup"><span data-stu-id="fcec8-104">Its meaning depends on the kind of address.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fcec8-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="fcec8-105">Syntax</span></span>  
  
```  
HRESULT GetAddressField1(  
    [out, retval] ULONG32* pRetVal);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="fcec8-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="fcec8-106">Parameters</span></span>  
 `pRetVal`  
 <span data-ttu-id="fcec8-107">[out] Wskaźnik do `ULONG32` odbierająca pierwsze pole adresu.</span><span class="sxs-lookup"><span data-stu-id="fcec8-107">[out] A pointer to a `ULONG32` that receives the first address field.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="fcec8-108">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="fcec8-108">Return Value</span></span>  
 <span data-ttu-id="fcec8-109">Wartość S_OK, jeśli metoda zakończy się pomyślnie; w przeciwnym razie E_FAIL lub inny kod błędu.</span><span class="sxs-lookup"><span data-stu-id="fcec8-109">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="fcec8-110">Wymagania</span><span class="sxs-lookup"><span data-stu-id="fcec8-110">Requirements</span></span>  
 <span data-ttu-id="fcec8-111">**Nagłówek:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="fcec8-111">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fcec8-112">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="fcec8-112">See Also</span></span>  
 [<span data-ttu-id="fcec8-113">ISymUnmanagedVariable, interfejs</span><span class="sxs-lookup"><span data-stu-id="fcec8-113">ISymUnmanagedVariable Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedvariable-interface.md)  
 [<span data-ttu-id="fcec8-114">GetAddressField2, metoda</span><span class="sxs-lookup"><span data-stu-id="fcec8-114">GetAddressField2 Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedvariable-getaddressfield2-method.md)  
 [<span data-ttu-id="fcec8-115">GetAddressField3, metoda</span><span class="sxs-lookup"><span data-stu-id="fcec8-115">GetAddressField3 Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedvariable-getaddressfield3-method.md)  
 [<span data-ttu-id="fcec8-116">GetAddressKind, metoda</span><span class="sxs-lookup"><span data-stu-id="fcec8-116">GetAddressKind Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedvariable-getaddresskind-method.md)
