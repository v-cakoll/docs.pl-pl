---
title: ISymUnmanagedWriter::OpenScope — Metoda
ms.date: 03/30/2017
api_name:
- ISymUnmanagedWriter.OpenScope
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedWriter::OpenScope
helpviewer_keywords:
- OpenScope method, ISymUnmanagedWriter interface [.NET Framework debugging]
- ISymUnmanagedWriter::OpenScope method [.NET Framework debugging]
ms.assetid: dbea0644-3873-4329-90b8-624163e87467
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: f6a862f0861416ebc80c7b6107267bcbb5ec51f4
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54657366"
---
# <a name="isymunmanagedwriteropenscope-method"></a><span data-ttu-id="abefc-102">ISymUnmanagedWriter::OpenScope — Metoda</span><span class="sxs-lookup"><span data-stu-id="abefc-102">ISymUnmanagedWriter::OpenScope Method</span></span>
<span data-ttu-id="abefc-103">Zostanie otwarty nowy zakres leksykalne w bieżącej metodzie.</span><span class="sxs-lookup"><span data-stu-id="abefc-103">Opens a new lexical scope in the current method.</span></span> <span data-ttu-id="abefc-104">Zakres staje się nowy zakres bieżący i są wypychane na stosie zakresów.</span><span class="sxs-lookup"><span data-stu-id="abefc-104">The scope becomes the new current scope and is pushed onto a stack of scopes.</span></span> <span data-ttu-id="abefc-105">Zakresy należy tworzą hierarchię.</span><span class="sxs-lookup"><span data-stu-id="abefc-105">Scopes must form a hierarchy.</span></span> <span data-ttu-id="abefc-106">Elementy równorzędne są niedozwolone nakładają się na siebie.</span><span class="sxs-lookup"><span data-stu-id="abefc-106">Siblings are not allowed to overlap.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="abefc-107">Składnia</span><span class="sxs-lookup"><span data-stu-id="abefc-107">Syntax</span></span>  
  
```  
HRESULT OpenScope(  
    [in] ULONG32 startOffset,  
    [out, retval] ULONG32* pRetVal);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="abefc-108">Parametry</span><span class="sxs-lookup"><span data-stu-id="abefc-108">Parameters</span></span>  
 `startOffset`  
 <span data-ttu-id="abefc-109">[in] Przesunięcie pierwsza instrukcja w zakresie leksykalnym, w bajtach od początku metody.</span><span class="sxs-lookup"><span data-stu-id="abefc-109">[in] The offset of the first instruction in the lexical scope, in bytes, from the beginning of the method.</span></span>  
  
 `pRetVal`  
 <span data-ttu-id="abefc-110">[out] Wskaźnik do `ULONG32` , która otrzymuje identyfikator zakresu.</span><span class="sxs-lookup"><span data-stu-id="abefc-110">[out] A pointer to a `ULONG32` that receives the scope identifier.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="abefc-111">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="abefc-111">Return Value</span></span>  
 <span data-ttu-id="abefc-112">S_OK, jeśli metoda się powiedzie; w przeciwnym razie E_FAIL lub innego kodu błędu.</span><span class="sxs-lookup"><span data-stu-id="abefc-112">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="abefc-113">Uwagi</span><span class="sxs-lookup"><span data-stu-id="abefc-113">Remarks</span></span>  
 <span data-ttu-id="abefc-114">`ISymUnmanagedWriter::OpenScope` Zwraca identyfikator nieprzezroczysty zakres, który może być używany z [ISymUnmanagedWriter::SetScopeRange](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-setscoperange-method.md) Aby zdefiniować zakres użytkownika początkowe i końcowe przesunięcie w późniejszym czasie.</span><span class="sxs-lookup"><span data-stu-id="abefc-114">`ISymUnmanagedWriter::OpenScope` returns an opaque scope identifier that can be used with [ISymUnmanagedWriter::SetScopeRange](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-setscoperange-method.md) to define a scope's starting and ending offset at a later time.</span></span> <span data-ttu-id="abefc-115">W tym przypadku przesunięcia przekazany do `ISymUnmanagedWriter::OpenScope` i [ISymUnmanagedWriter::CloseScope](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-closescope-method.md) są ignorowane.</span><span class="sxs-lookup"><span data-stu-id="abefc-115">In this case, the offsets passed to `ISymUnmanagedWriter::OpenScope` and [ISymUnmanagedWriter::CloseScope](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-closescope-method.md) are ignored.</span></span> <span data-ttu-id="abefc-116">Zakres identyfikatorów są prawidłowe tylko w bieżącej metodzie.</span><span class="sxs-lookup"><span data-stu-id="abefc-116">Scope identifiers are valid only in the current method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="abefc-117">Wymagania</span><span class="sxs-lookup"><span data-stu-id="abefc-117">Requirements</span></span>  
 <span data-ttu-id="abefc-118">**Nagłówek:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="abefc-118">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="abefc-119">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="abefc-119">See also</span></span>
- [<span data-ttu-id="abefc-120">ISymUnmanagedWriter, interfejs</span><span class="sxs-lookup"><span data-stu-id="abefc-120">ISymUnmanagedWriter Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-interface.md)
