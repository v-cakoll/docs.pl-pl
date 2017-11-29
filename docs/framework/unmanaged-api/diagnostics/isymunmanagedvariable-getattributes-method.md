---
title: "ISymUnmanagedVariable::GetAttributes — Metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ISymUnmanagedVariable.GetAttributes
api_location: diasymreader.dll
api_type: COM
f1_keywords: ISymUnmanagedVariable::GetAttributes
helpviewer_keywords:
- GetAttributes method [.NET Framework debugging]
- ISymUnmanagedVariable::GetAttributes method [.NET Framework debugging]
ms.assetid: 80f168af-a6a6-4c8f-b9e6-8a82dc834ed5
topic_type: apiref
caps.latest.revision: "10"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 41bdbf20d3905ba218802a6801c7394b237f6e0f
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="isymunmanagedvariablegetattributes-method"></a><span data-ttu-id="6f5e7-102">ISymUnmanagedVariable::GetAttributes — Metoda</span><span class="sxs-lookup"><span data-stu-id="6f5e7-102">ISymUnmanagedVariable::GetAttributes Method</span></span>
<span data-ttu-id="6f5e7-103">Pobiera atrybut Flagi dla tej zmiennej.</span><span class="sxs-lookup"><span data-stu-id="6f5e7-103">Gets the attribute flags for this variable.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6f5e7-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="6f5e7-104">Syntax</span></span>  
  
```  
HRESULT GetAttributes(  
    [out, retval] ULONG32* pRetVal);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="6f5e7-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="6f5e7-105">Parameters</span></span>  
 `pRetVal`  
 <span data-ttu-id="6f5e7-106">[out] Wskaźnik do `ULONG32` odbierająca atrybutów.</span><span class="sxs-lookup"><span data-stu-id="6f5e7-106">[out] A pointer to a `ULONG32` that receives the attributes.</span></span> <span data-ttu-id="6f5e7-107">Zwrócona wartość będzie jedną z wartości zdefiniowanych w [CorSymVarFlag](../../../../docs/framework/unmanaged-api/diagnostics/corsymvarflag-enumeration.md) wyliczenia.</span><span class="sxs-lookup"><span data-stu-id="6f5e7-107">The returned value will be one of the values defined in the [CorSymVarFlag](../../../../docs/framework/unmanaged-api/diagnostics/corsymvarflag-enumeration.md) enumeration.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="6f5e7-108">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="6f5e7-108">Return Value</span></span>  
 <span data-ttu-id="6f5e7-109">Wartość S_OK, jeśli metoda zakończy się pomyślnie; w przeciwnym razie E_FAIL lub inny kod błędu.</span><span class="sxs-lookup"><span data-stu-id="6f5e7-109">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6f5e7-110">Wymagania</span><span class="sxs-lookup"><span data-stu-id="6f5e7-110">Requirements</span></span>  
 <span data-ttu-id="6f5e7-111">**Nagłówek:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="6f5e7-111">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6f5e7-112">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="6f5e7-112">See Also</span></span>  
 [<span data-ttu-id="6f5e7-113">ISymUnmanagedVariable — interfejs</span><span class="sxs-lookup"><span data-stu-id="6f5e7-113">ISymUnmanagedVariable Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedvariable-interface.md)
