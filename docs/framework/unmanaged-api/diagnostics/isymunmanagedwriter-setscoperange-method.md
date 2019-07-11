---
title: ISymUnmanagedWriter::SetScopeRange — Metoda
ms.date: 03/30/2017
api_name:
- ISymUnmanagedWriter.SetScopeRange
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedWriter::SetScopeRange
helpviewer_keywords:
- SetScopeRange method [.NET Framework debugging]
- ISymUnmanagedWriter::SetScopeRange method [.NET Framework debugging]
ms.assetid: d4d98676-444b-46ca-bfe6-0d827385cd22
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: c13eb7ca16cdb7c70f3fef0dd4efcb9362cd3d87
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/10/2019
ms.locfileid: "67776584"
---
# <a name="isymunmanagedwritersetscoperange-method"></a><span data-ttu-id="fdc0b-102">ISymUnmanagedWriter::SetScopeRange — Metoda</span><span class="sxs-lookup"><span data-stu-id="fdc0b-102">ISymUnmanagedWriter::SetScopeRange Method</span></span>
<span data-ttu-id="fdc0b-103">Definiuje zakres przesunięcia dla określonego zakresu leksykalne.</span><span class="sxs-lookup"><span data-stu-id="fdc0b-103">Defines the offset range for the specified lexical scope.</span></span> <span data-ttu-id="fdc0b-104">Zakres staje się nowy zakres bieżący i są wypychane na stosie zakresów.</span><span class="sxs-lookup"><span data-stu-id="fdc0b-104">The scope becomes the new current scope and is pushed onto a stack of scopes.</span></span> <span data-ttu-id="fdc0b-105">Zakresy należy tworzą hierarchię.</span><span class="sxs-lookup"><span data-stu-id="fdc0b-105">Scopes must form a hierarchy.</span></span> <span data-ttu-id="fdc0b-106">Elementy równorzędne są niedozwolone nakładają się na siebie.</span><span class="sxs-lookup"><span data-stu-id="fdc0b-106">Siblings are not allowed to overlap.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fdc0b-107">Składnia</span><span class="sxs-lookup"><span data-stu-id="fdc0b-107">Syntax</span></span>  
  
```cpp  
HRESULT OpenScope(  
    [in] ULONG32  scopeID,  
    [in] ULONG32  startOffset,  
    [in] ULONG32  endOffset);  
```  
  
## <a name="parameters"></a><span data-ttu-id="fdc0b-108">Parametry</span><span class="sxs-lookup"><span data-stu-id="fdc0b-108">Parameters</span></span>  
 `scopeId`  
 <span data-ttu-id="fdc0b-109">[in] Identyfikator zakresu dla zakresu.</span><span class="sxs-lookup"><span data-stu-id="fdc0b-109">[in] The scope identifier for the scope.</span></span>  
  
 `startOffset`  
 <span data-ttu-id="fdc0b-110">[in] Przesunięcie w bajtach, pierwsza instrukcja w zakresie leksykalnym od samego początku metody.</span><span class="sxs-lookup"><span data-stu-id="fdc0b-110">[in] The offset, in bytes, of the first instruction in the lexical scope from the beginning of the method.</span></span>  
  
 `endOffset`  
 <span data-ttu-id="fdc0b-111">[in] Przesunięcie w bajtach ostatniej instrukcji w zakresie leksykalnym od samego początku metody.</span><span class="sxs-lookup"><span data-stu-id="fdc0b-111">[in] The offset, in bytes, of the last instruction in the lexical scope from the beginning of the method.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="fdc0b-112">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="fdc0b-112">Return Value</span></span>  
 <span data-ttu-id="fdc0b-113">S_OK, jeśli metoda się powiedzie; w przeciwnym razie E_FAIL lub innego kodu błędu.</span><span class="sxs-lookup"><span data-stu-id="fdc0b-113">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="fdc0b-114">Uwagi</span><span class="sxs-lookup"><span data-stu-id="fdc0b-114">Remarks</span></span>  
 <span data-ttu-id="fdc0b-115">[ISymUnmanagedWriter::OpenScope](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-openscope-method.md) zwraca identyfikator nieprzezroczysty zakres, który może być używany z `ISymUnmanagedWriter::SetScopeRange` Aby zdefiniować zakres użytkownika początkowe i końcowe przesunięcie w późniejszym czasie.</span><span class="sxs-lookup"><span data-stu-id="fdc0b-115">[ISymUnmanagedWriter::OpenScope](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-openscope-method.md) returns an opaque scope identifier that can be used with `ISymUnmanagedWriter::SetScopeRange` to define a scope's starting and ending offset at a later time.</span></span> <span data-ttu-id="fdc0b-116">W tym przypadku przesunięcia przekazany do `ISymUnmanagedWriter::OpenScope` i [ISymUnmanagedWriter::CloseScope](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-closescope-method.md) są ignorowane.</span><span class="sxs-lookup"><span data-stu-id="fdc0b-116">In this case, the offsets passed to `ISymUnmanagedWriter::OpenScope` and [ISymUnmanagedWriter::CloseScope](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-closescope-method.md) are ignored.</span></span> <span data-ttu-id="fdc0b-117">Zakres identyfikatorów są prawidłowe tylko w bieżącej metodzie.</span><span class="sxs-lookup"><span data-stu-id="fdc0b-117">Scope identifiers are only valid in the current method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="fdc0b-118">Wymagania</span><span class="sxs-lookup"><span data-stu-id="fdc0b-118">Requirements</span></span>  
 <span data-ttu-id="fdc0b-119">**Nagłówek:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="fdc0b-119">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fdc0b-120">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="fdc0b-120">See also</span></span>

- [<span data-ttu-id="fdc0b-121">ISymUnmanagedWriter, interfejs</span><span class="sxs-lookup"><span data-stu-id="fdc0b-121">ISymUnmanagedWriter Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-interface.md)
