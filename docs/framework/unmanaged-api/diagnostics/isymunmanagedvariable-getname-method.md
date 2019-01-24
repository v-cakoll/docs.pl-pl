---
title: ISymUnmanagedVariable::GetName — Metoda
ms.date: 03/30/2017
api_name:
- ISymUnmanagedVariable.GetName
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedVariable::GetName
helpviewer_keywords:
- GetName method, ISymUnmanagedVariable interface [.NET Framework debugging]
- ISymUnmanagedVariable::GetName method [.NET Framework debugging]
ms.assetid: eedf1ef0-9d4a-4847-a201-4e99572dfe5e
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 6323b7d94ca32646d3aa63af6d3efc4de95e67fb
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54534530"
---
# <a name="isymunmanagedvariablegetname-method"></a><span data-ttu-id="029ac-102">ISymUnmanagedVariable::GetName — Metoda</span><span class="sxs-lookup"><span data-stu-id="029ac-102">ISymUnmanagedVariable::GetName Method</span></span>
<span data-ttu-id="029ac-103">Pobiera nazwę tej zmiennej.</span><span class="sxs-lookup"><span data-stu-id="029ac-103">Gets the name of this variable.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="029ac-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="029ac-104">Syntax</span></span>  
  
```  
HRESULT GetName(  
    [in]  ULONG32  cchName,  
    [out] ULONG32  *pcchName,  
    [out, size_is(cchName),  
        length_is(*pcchName)] WCHAR szName[]);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="029ac-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="029ac-105">Parameters</span></span>  
 `cchName`  
 <span data-ttu-id="029ac-106">[in] Długość buforu, `pcchName` parametr wskazuje.</span><span class="sxs-lookup"><span data-stu-id="029ac-106">[in] The length of the buffer that the `pcchName` parameter points to.</span></span>  
  
 `pcchName`  
 <span data-ttu-id="029ac-107">[out] Wskaźnik do `ULONG32` rozmiar, który odbiera w postaci, buforu, muszą zawierać nazwę, w tym zakończenia o wartości null.</span><span class="sxs-lookup"><span data-stu-id="029ac-107">[out] A pointer to a `ULONG32` that receives the size, in characters, of the buffer required to contain the name, including the null termination.</span></span>  
  
 `szName`  
 <span data-ttu-id="029ac-108">[out] Bufor, który przechowuje nazwę.</span><span class="sxs-lookup"><span data-stu-id="029ac-108">[out] The buffer that stores the name.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="029ac-109">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="029ac-109">Return Value</span></span>  
 <span data-ttu-id="029ac-110">S_OK, jeśli metoda się powiedzie; w przeciwnym razie E_FAIL lub innego kodu błędu.</span><span class="sxs-lookup"><span data-stu-id="029ac-110">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="029ac-111">Wymagania</span><span class="sxs-lookup"><span data-stu-id="029ac-111">Requirements</span></span>  
 <span data-ttu-id="029ac-112">**Nagłówek:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="029ac-112">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="029ac-113">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="029ac-113">See also</span></span>
- [<span data-ttu-id="029ac-114">ISymUnmanagedVariable, interfejs</span><span class="sxs-lookup"><span data-stu-id="029ac-114">ISymUnmanagedVariable Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedvariable-interface.md)
