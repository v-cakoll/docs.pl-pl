---
title: ISymUnmanagedReader::GetVariables — Metoda
ms.date: 03/30/2017
api_name:
- ISymUnmanagedReader.GetVariables
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedReader::GetVariables
helpviewer_keywords:
- ISymUnmanagedReader::GetVariables method [.NET Framework debugging]
- GetVariables method, ISymUnmanagedReader interface [.NET Framework debugging]
ms.assetid: 16dc49cb-2c60-4ac8-9c35-020e9afba3f8
topic_type:
- apiref
ms.openlocfilehash: 4590d2734ea89bc1bc8a30db1c7ecac5effafd7b
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/23/2019
ms.locfileid: "74429755"
---
# <a name="isymunmanagedreadergetvariables-method"></a><span data-ttu-id="f3acd-102">ISymUnmanagedReader::GetVariables — Metoda</span><span class="sxs-lookup"><span data-stu-id="f3acd-102">ISymUnmanagedReader::GetVariables Method</span></span>
<span data-ttu-id="f3acd-103">Zwraca zmienną nielokalną, używając jej elementu nadrzędnego i nazwy.</span><span class="sxs-lookup"><span data-stu-id="f3acd-103">Returns a non-local variable, given its parent and name.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f3acd-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="f3acd-104">Syntax</span></span>  
  
```cpp  
HRESULT GetVariables (  
    [in]  mdToken  parent,  
    [in]  ULONG32  cVars,  
    [out] ULONG32  *pcVars,  
    [out, size_is (cVars),  
        length_is (*pcVars)] ISymUnmanagedVariable *pVars[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="f3acd-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="f3acd-105">Parameters</span></span>  
 `parent`  
 <span data-ttu-id="f3acd-106">podczas Element nadrzędny zmiennej.</span><span class="sxs-lookup"><span data-stu-id="f3acd-106">[in] The parent of the variable.</span></span>  
  
 `cVars`  
 <span data-ttu-id="f3acd-107">podczas Rozmiar tablicy `pVars`.</span><span class="sxs-lookup"><span data-stu-id="f3acd-107">[in] The size of the `pVars` array.</span></span>  
  
 `pcVars`  
 <span data-ttu-id="f3acd-108">określoną Wskaźnik do zmiennej, która otrzymuje liczbę zmiennych zwracanych w `pVars`.</span><span class="sxs-lookup"><span data-stu-id="f3acd-108">[out] A pointer to the variable that receives the number of variables returned in `pVars`.</span></span>  
  
 `pVars`  
 <span data-ttu-id="f3acd-109">określoną Wskaźnik do zmiennej, która odbiera zmienne.</span><span class="sxs-lookup"><span data-stu-id="f3acd-109">[out] A pointer to the variable that receives the variables.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="f3acd-110">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="f3acd-110">Return Value</span></span>  
 <span data-ttu-id="f3acd-111">S_OK, jeśli metoda się powiedzie; w przeciwnym razie E_FAIL lub inny kod błędu.</span><span class="sxs-lookup"><span data-stu-id="f3acd-111">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f3acd-112">Wymagania</span><span class="sxs-lookup"><span data-stu-id="f3acd-112">Requirements</span></span>  
 <span data-ttu-id="f3acd-113">**Nagłówek:** CorSym. idl, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="f3acd-113">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f3acd-114">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="f3acd-114">See also</span></span>

- [<span data-ttu-id="f3acd-115">ISymUnmanagedReader, interfejs</span><span class="sxs-lookup"><span data-stu-id="f3acd-115">ISymUnmanagedReader Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-interface.md)
