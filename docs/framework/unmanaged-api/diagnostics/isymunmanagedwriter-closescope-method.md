---
title: ISymUnmanagedWriter::CloseScope — Metoda
ms.date: 03/30/2017
api_name:
- ISymUnmanagedWriter.CloseScope
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedWriter::CloseScope
helpviewer_keywords:
- CloseScope method [.NET Framework debugging]
- ISymUnmanagedWriter::CloseScope method [.NET Framework debugging]
ms.assetid: 6dade525-7770-4cb4-bafd-4bb995ad0d87
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: a11f689f1fa93e1122ffcc78187c4287db7ea534
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33427027"
---
# <a name="isymunmanagedwriterclosescope-method"></a><span data-ttu-id="8dcab-102">ISymUnmanagedWriter::CloseScope — Metoda</span><span class="sxs-lookup"><span data-stu-id="8dcab-102">ISymUnmanagedWriter::CloseScope Method</span></span>
<span data-ttu-id="8dcab-103">Zamyka leksykalne bieżącego zakresu.</span><span class="sxs-lookup"><span data-stu-id="8dcab-103">Closes the current lexical scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8dcab-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="8dcab-104">Syntax</span></span>  
  
```  
HRESULT CloseScope(  
    [in] ULONG32 endOffset);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="8dcab-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="8dcab-105">Parameters</span></span>  
 `endOffset`  
 <span data-ttu-id="8dcab-106">[in] Przesunięcie od początku metody punktu na końcu ostatniej instrukcji w zakresie leksykalne, w bajtach.</span><span class="sxs-lookup"><span data-stu-id="8dcab-106">[in] The offset from the beginning of the method of the point at the end of the last instruction in the lexical scope, in bytes.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="8dcab-107">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="8dcab-107">Return Value</span></span>  
 <span data-ttu-id="8dcab-108">Wartość S_OK, jeśli metoda zakończy się pomyślnie; w przeciwnym razie E_FAIL lub inny kod błędu.</span><span class="sxs-lookup"><span data-stu-id="8dcab-108">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="8dcab-109">Uwagi</span><span class="sxs-lookup"><span data-stu-id="8dcab-109">Remarks</span></span>  
 <span data-ttu-id="8dcab-110">Po zamknięciu zakresu nie więcej zmiennych mogą być definiowane w niej.</span><span class="sxs-lookup"><span data-stu-id="8dcab-110">Once a scope is closed, no more variables can be defined within it.</span></span>  
  
 <span data-ttu-id="8dcab-111">[ISymUnmanagedWriter::OpenScope](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-openscope-method.md) zwraca identyfikator zakresu nieprzezroczyste, który może być używany z [ISymUnmanagedWriter::SetScopeRange](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-setscoperange-method.md) później określenie zakresu na początkową i końcową przesunięcie.</span><span class="sxs-lookup"><span data-stu-id="8dcab-111">[ISymUnmanagedWriter::OpenScope](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-openscope-method.md) returns an opaque scope identifier that can be used with [ISymUnmanagedWriter::SetScopeRange](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-setscoperange-method.md) to later define a scope's starting and ending offset.</span></span> <span data-ttu-id="8dcab-112">W takim przypadku przesunięcia przekazany do `ISymUnmanagedWriter::OpenScope` i `ISymUnmanagedWriter::CloseScope` są ignorowane.</span><span class="sxs-lookup"><span data-stu-id="8dcab-112">In this case, the offsets passed to `ISymUnmanagedWriter::OpenScope` and `ISymUnmanagedWriter::CloseScope` are ignored.</span></span> <span data-ttu-id="8dcab-113">Zakres identyfikatorów są prawidłowe tylko w bieżącej metodzie.</span><span class="sxs-lookup"><span data-stu-id="8dcab-113">Scope identifiers are valid only in the current method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8dcab-114">Wymagania</span><span class="sxs-lookup"><span data-stu-id="8dcab-114">Requirements</span></span>  
 <span data-ttu-id="8dcab-115">**Header:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="8dcab-115">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8dcab-116">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="8dcab-116">See Also</span></span>  
 [<span data-ttu-id="8dcab-117">ISymUnmanagedWriter, interfejs</span><span class="sxs-lookup"><span data-stu-id="8dcab-117">ISymUnmanagedWriter Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-interface.md)
