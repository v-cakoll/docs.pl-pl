---
title: "ISymUnmanagedWriter::CloseScope — Metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ISymUnmanagedWriter.CloseScope
api_location: diasymreader.dll
api_type: COM
f1_keywords: ISymUnmanagedWriter::CloseScope
helpviewer_keywords:
- CloseScope method [.NET Framework debugging]
- ISymUnmanagedWriter::CloseScope method [.NET Framework debugging]
ms.assetid: 6dade525-7770-4cb4-bafd-4bb995ad0d87
topic_type: apiref
caps.latest.revision: "11"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: a8df22e5f9ea2ca294f502fcebf4b2ed5cd7900d
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="isymunmanagedwriterclosescope-method"></a><span data-ttu-id="a0d20-102">ISymUnmanagedWriter::CloseScope — Metoda</span><span class="sxs-lookup"><span data-stu-id="a0d20-102">ISymUnmanagedWriter::CloseScope Method</span></span>
<span data-ttu-id="a0d20-103">Zamyka leksykalne bieżącego zakresu.</span><span class="sxs-lookup"><span data-stu-id="a0d20-103">Closes the current lexical scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a0d20-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="a0d20-104">Syntax</span></span>  
  
```  
HRESULT CloseScope(  
    [in] ULONG32 endOffset);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="a0d20-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="a0d20-105">Parameters</span></span>  
 `endOffset`  
 <span data-ttu-id="a0d20-106">[in] Przesunięcie od początku metody punktu na końcu ostatniej instrukcji w zakresie leksykalne, w bajtach.</span><span class="sxs-lookup"><span data-stu-id="a0d20-106">[in] The offset from the beginning of the method of the point at the end of the last instruction in the lexical scope, in bytes.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="a0d20-107">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="a0d20-107">Return Value</span></span>  
 <span data-ttu-id="a0d20-108">Wartość S_OK, jeśli metoda zakończy się pomyślnie; w przeciwnym razie E_FAIL lub inny kod błędu.</span><span class="sxs-lookup"><span data-stu-id="a0d20-108">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="a0d20-109">Uwagi</span><span class="sxs-lookup"><span data-stu-id="a0d20-109">Remarks</span></span>  
 <span data-ttu-id="a0d20-110">Po zamknięciu zakresu nie więcej zmiennych mogą być definiowane w niej.</span><span class="sxs-lookup"><span data-stu-id="a0d20-110">Once a scope is closed, no more variables can be defined within it.</span></span>  
  
 <span data-ttu-id="a0d20-111">[ISymUnmanagedWriter::OpenScope](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-openscope-method.md) zwraca identyfikator zakresu nieprzezroczyste, który może być używany z [ISymUnmanagedWriter::SetScopeRange](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-setscoperange-method.md) później określenie zakresu na początkową i końcową przesunięcie.</span><span class="sxs-lookup"><span data-stu-id="a0d20-111">[ISymUnmanagedWriter::OpenScope](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-openscope-method.md) returns an opaque scope identifier that can be used with [ISymUnmanagedWriter::SetScopeRange](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-setscoperange-method.md) to later define a scope's starting and ending offset.</span></span> <span data-ttu-id="a0d20-112">W takim przypadku przesunięcia przekazany do `ISymUnmanagedWriter::OpenScope` i `ISymUnmanagedWriter::CloseScope` są ignorowane.</span><span class="sxs-lookup"><span data-stu-id="a0d20-112">In this case, the offsets passed to `ISymUnmanagedWriter::OpenScope` and `ISymUnmanagedWriter::CloseScope` are ignored.</span></span> <span data-ttu-id="a0d20-113">Zakres identyfikatorów są prawidłowe tylko w bieżącej metodzie.</span><span class="sxs-lookup"><span data-stu-id="a0d20-113">Scope identifiers are valid only in the current method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a0d20-114">Wymagania</span><span class="sxs-lookup"><span data-stu-id="a0d20-114">Requirements</span></span>  
 <span data-ttu-id="a0d20-115">**Nagłówek:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="a0d20-115">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a0d20-116">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="a0d20-116">See Also</span></span>  
 [<span data-ttu-id="a0d20-117">ISymUnmanagedWriter — interfejs</span><span class="sxs-lookup"><span data-stu-id="a0d20-117">ISymUnmanagedWriter Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-interface.md)
