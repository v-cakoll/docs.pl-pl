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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 74df7ee71fc541c35bc393f637ad1d7b9f7aa2a0
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33425529"
---
# <a name="isymunmanagedreadergetvariables-method"></a><span data-ttu-id="17243-102">ISymUnmanagedReader::GetVariables — Metoda</span><span class="sxs-lookup"><span data-stu-id="17243-102">ISymUnmanagedReader::GetVariables Method</span></span>
<span data-ttu-id="17243-103">Zwraca wartość zmiennej nie lokalnego na jego nadrzędny i nazwę.</span><span class="sxs-lookup"><span data-stu-id="17243-103">Returns a non-local variable, given its parent and name.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="17243-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="17243-104">Syntax</span></span>  
  
```  
HRESULT GetVariables (  
    [in]  mdToken  parent,  
    [in]  ULONG32  cVars,  
    [out] ULONG32  *pcVars,  
    [out, size_is (cVars),  
        length_is (*pcVars)] ISymUnmanagedVariable *pVars[]);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="17243-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="17243-105">Parameters</span></span>  
 `parent`  
 <span data-ttu-id="17243-106">[in] Element nadrzędny zmiennej.</span><span class="sxs-lookup"><span data-stu-id="17243-106">[in] The parent of the variable.</span></span>  
  
 `cVars`  
 <span data-ttu-id="17243-107">[in] Rozmiar `pVars` tablicy.</span><span class="sxs-lookup"><span data-stu-id="17243-107">[in] The size of the `pVars` array.</span></span>  
  
 `pcVars`  
 <span data-ttu-id="17243-108">[out] Wskaźnik do zmiennej, która odbiera liczba zmiennych zwracane w `pVars`.</span><span class="sxs-lookup"><span data-stu-id="17243-108">[out] A pointer to the variable that receives the number of variables returned in `pVars`.</span></span>  
  
 `pVars`  
 <span data-ttu-id="17243-109">[out] Wskaźnik do zmiennej, która odbiera zmienne.</span><span class="sxs-lookup"><span data-stu-id="17243-109">[out] A pointer to the variable that receives the variables.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="17243-110">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="17243-110">Return Value</span></span>  
 <span data-ttu-id="17243-111">Wartość S_OK, jeśli metoda zakończy się pomyślnie; w przeciwnym razie E_FAIL lub inny kod błędu.</span><span class="sxs-lookup"><span data-stu-id="17243-111">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="17243-112">Wymagania</span><span class="sxs-lookup"><span data-stu-id="17243-112">Requirements</span></span>  
 <span data-ttu-id="17243-113">**Header:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="17243-113">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="17243-114">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="17243-114">See Also</span></span>  
 [<span data-ttu-id="17243-115">ISymUnmanagedReader, interfejs</span><span class="sxs-lookup"><span data-stu-id="17243-115">ISymUnmanagedReader Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-interface.md)
