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
ms.openlocfilehash: 29869abdd39f61c6c9cb51d6b2be50fa462c5b70
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/19/2020
ms.locfileid: "83615257"
---
# <a name="isymunmanagedvariablegetattributes-method"></a><span data-ttu-id="4ea6a-102">ISymUnmanagedVariable::GetAttributes — Metoda</span><span class="sxs-lookup"><span data-stu-id="4ea6a-102">ISymUnmanagedVariable::GetAttributes Method</span></span>
<span data-ttu-id="4ea6a-103">Pobiera flagi atrybutu dla tej zmiennej.</span><span class="sxs-lookup"><span data-stu-id="4ea6a-103">Gets the attribute flags for this variable.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4ea6a-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="4ea6a-104">Syntax</span></span>  
  
```cpp  
HRESULT GetAttributes(  
    [out, retval] ULONG32* pRetVal);  
```  
  
## <a name="parameters"></a><span data-ttu-id="4ea6a-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="4ea6a-105">Parameters</span></span>  
 `pRetVal`  
 <span data-ttu-id="4ea6a-106">określoną Wskaźnik do elementu `ULONG32` , który odbiera atrybuty.</span><span class="sxs-lookup"><span data-stu-id="4ea6a-106">[out] A pointer to a `ULONG32` that receives the attributes.</span></span> <span data-ttu-id="4ea6a-107">Zwrócona wartość będzie jedną z wartości zdefiniowanych w wyliczeniu [CorSymVarFlag —](corsymvarflag-enumeration.md) .</span><span class="sxs-lookup"><span data-stu-id="4ea6a-107">The returned value will be one of the values defined in the [CorSymVarFlag](corsymvarflag-enumeration.md) enumeration.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="4ea6a-108">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="4ea6a-108">Return Value</span></span>  
 <span data-ttu-id="4ea6a-109">S_OK, jeśli metoda się powiedzie; w przeciwnym razie E_FAIL lub inny kod błędu.</span><span class="sxs-lookup"><span data-stu-id="4ea6a-109">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4ea6a-110">Wymagania</span><span class="sxs-lookup"><span data-stu-id="4ea6a-110">Requirements</span></span>  
 <span data-ttu-id="4ea6a-111">**Nagłówek:** CorSym. idl, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="4ea6a-111">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4ea6a-112">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="4ea6a-112">See also</span></span>

- [<span data-ttu-id="4ea6a-113">ISymUnmanagedVariable, interfejs</span><span class="sxs-lookup"><span data-stu-id="4ea6a-113">ISymUnmanagedVariable Interface</span></span>](isymunmanagedvariable-interface.md)
