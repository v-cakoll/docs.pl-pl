---
title: ISymUnmanagedVariable::GetAttributes — Metoda
ms.date: 03/30/2017
api_name:
- ISymUnmanagedVariable.GetAttributes
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedVariable::GetAttributes
helpviewer_keywords:
- GetAttributes method [.NET Framework debugging]
- ISymUnmanagedVariable::GetAttributes method [.NET Framework debugging]
ms.assetid: 80f168af-a6a6-4c8f-b9e6-8a82dc834ed5
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: dc0f72168e076f661bfefc17c851d7d353e5e742
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33426755"
---
# <a name="isymunmanagedvariablegetattributes-method"></a><span data-ttu-id="29722-102">ISymUnmanagedVariable::GetAttributes — Metoda</span><span class="sxs-lookup"><span data-stu-id="29722-102">ISymUnmanagedVariable::GetAttributes Method</span></span>
<span data-ttu-id="29722-103">Pobiera atrybut Flagi dla tej zmiennej.</span><span class="sxs-lookup"><span data-stu-id="29722-103">Gets the attribute flags for this variable.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="29722-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="29722-104">Syntax</span></span>  
  
```  
HRESULT GetAttributes(  
    [out, retval] ULONG32* pRetVal);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="29722-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="29722-105">Parameters</span></span>  
 `pRetVal`  
 <span data-ttu-id="29722-106">[out] Wskaźnik do `ULONG32` odbierająca atrybutów.</span><span class="sxs-lookup"><span data-stu-id="29722-106">[out] A pointer to a `ULONG32` that receives the attributes.</span></span> <span data-ttu-id="29722-107">Zwrócona wartość będzie jedną z wartości zdefiniowanych w [CorSymVarFlag](../../../../docs/framework/unmanaged-api/diagnostics/corsymvarflag-enumeration.md) wyliczenia.</span><span class="sxs-lookup"><span data-stu-id="29722-107">The returned value will be one of the values defined in the [CorSymVarFlag](../../../../docs/framework/unmanaged-api/diagnostics/corsymvarflag-enumeration.md) enumeration.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="29722-108">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="29722-108">Return Value</span></span>  
 <span data-ttu-id="29722-109">Wartość S_OK, jeśli metoda zakończy się pomyślnie; w przeciwnym razie E_FAIL lub inny kod błędu.</span><span class="sxs-lookup"><span data-stu-id="29722-109">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="29722-110">Wymagania</span><span class="sxs-lookup"><span data-stu-id="29722-110">Requirements</span></span>  
 <span data-ttu-id="29722-111">**Header:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="29722-111">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="29722-112">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="29722-112">See Also</span></span>  
 [<span data-ttu-id="29722-113">ISymUnmanagedVariable, interfejs</span><span class="sxs-lookup"><span data-stu-id="29722-113">ISymUnmanagedVariable Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedvariable-interface.md)
