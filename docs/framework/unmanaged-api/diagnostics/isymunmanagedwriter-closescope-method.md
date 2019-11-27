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
ms.openlocfilehash: 264b4487483ed5439a9809feefcdc1b20af402dc
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/23/2019
ms.locfileid: "74428074"
---
# <a name="isymunmanagedwriterclosescope-method"></a><span data-ttu-id="2c2ee-102">ISymUnmanagedWriter::CloseScope — Metoda</span><span class="sxs-lookup"><span data-stu-id="2c2ee-102">ISymUnmanagedWriter::CloseScope Method</span></span>
<span data-ttu-id="2c2ee-103">Zamyka bieżący zakres leksykalny.</span><span class="sxs-lookup"><span data-stu-id="2c2ee-103">Closes the current lexical scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2c2ee-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="2c2ee-104">Syntax</span></span>  
  
```cpp  
HRESULT CloseScope(  
    [in] ULONG32 endOffset);  
```  
  
## <a name="parameters"></a><span data-ttu-id="2c2ee-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="2c2ee-105">Parameters</span></span>  
 `endOffset`  
 <span data-ttu-id="2c2ee-106">podczas Przesunięcie od początku metody punktu na końcu ostatniej instrukcji w zakresie leksykalnym w bajtach.</span><span class="sxs-lookup"><span data-stu-id="2c2ee-106">[in] The offset from the beginning of the method of the point at the end of the last instruction in the lexical scope, in bytes.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="2c2ee-107">Wartość zwrócona</span><span class="sxs-lookup"><span data-stu-id="2c2ee-107">Return Value</span></span>  
 <span data-ttu-id="2c2ee-108">S_OK, jeśli metoda się powiedzie; w przeciwnym razie E_FAIL lub inny kod błędu.</span><span class="sxs-lookup"><span data-stu-id="2c2ee-108">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="2c2ee-109">Uwagi</span><span class="sxs-lookup"><span data-stu-id="2c2ee-109">Remarks</span></span>  
 <span data-ttu-id="2c2ee-110">Po zamknięciu zakresu nie można w nim definiować więcej zmiennych.</span><span class="sxs-lookup"><span data-stu-id="2c2ee-110">Once a scope is closed, no more variables can be defined within it.</span></span>  
  
 <span data-ttu-id="2c2ee-111">[ISymUnmanagedWriter:: OpenScope —](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-openscope-method.md) zwraca nieprzezroczysty identyfikator zakresu, który może być używany z [ISymUnmanagedWriter:: SetScopeRange —](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-setscoperange-method.md) w celu późniejszego zdefiniowania początkowego i końcowego przesunięcia zakresu.</span><span class="sxs-lookup"><span data-stu-id="2c2ee-111">[ISymUnmanagedWriter::OpenScope](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-openscope-method.md) returns an opaque scope identifier that can be used with [ISymUnmanagedWriter::SetScopeRange](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-setscoperange-method.md) to later define a scope's starting and ending offset.</span></span> <span data-ttu-id="2c2ee-112">W takim przypadku przesunięcia przesłane do `ISymUnmanagedWriter::OpenScope` i `ISymUnmanagedWriter::CloseScope` są ignorowane.</span><span class="sxs-lookup"><span data-stu-id="2c2ee-112">In this case, the offsets passed to `ISymUnmanagedWriter::OpenScope` and `ISymUnmanagedWriter::CloseScope` are ignored.</span></span> <span data-ttu-id="2c2ee-113">Identyfikatory zakresów są prawidłowe tylko w bieżącej metodzie.</span><span class="sxs-lookup"><span data-stu-id="2c2ee-113">Scope identifiers are valid only in the current method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2c2ee-114">Wymagania</span><span class="sxs-lookup"><span data-stu-id="2c2ee-114">Requirements</span></span>  
 <span data-ttu-id="2c2ee-115">**Nagłówek:** CorSym. idl, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="2c2ee-115">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2c2ee-116">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="2c2ee-116">See also</span></span>

- [<span data-ttu-id="2c2ee-117">ISymUnmanagedWriter, interfejs</span><span class="sxs-lookup"><span data-stu-id="2c2ee-117">ISymUnmanagedWriter Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-interface.md)
