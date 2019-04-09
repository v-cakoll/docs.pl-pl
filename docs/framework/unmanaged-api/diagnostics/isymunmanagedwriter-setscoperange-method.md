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
ms.openlocfilehash: 7d7fe8f36c7a5dbe6e715402fd7253092b64e68e
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59078970"
---
# <a name="isymunmanagedwritersetscoperange-method"></a><span data-ttu-id="4cbef-102">ISymUnmanagedWriter::SetScopeRange — Metoda</span><span class="sxs-lookup"><span data-stu-id="4cbef-102">ISymUnmanagedWriter::SetScopeRange Method</span></span>
<span data-ttu-id="4cbef-103">Definiuje zakres przesunięcia dla określonego zakresu leksykalne.</span><span class="sxs-lookup"><span data-stu-id="4cbef-103">Defines the offset range for the specified lexical scope.</span></span> <span data-ttu-id="4cbef-104">Zakres staje się nowy zakres bieżący i są wypychane na stosie zakresów.</span><span class="sxs-lookup"><span data-stu-id="4cbef-104">The scope becomes the new current scope and is pushed onto a stack of scopes.</span></span> <span data-ttu-id="4cbef-105">Zakresy należy tworzą hierarchię.</span><span class="sxs-lookup"><span data-stu-id="4cbef-105">Scopes must form a hierarchy.</span></span> <span data-ttu-id="4cbef-106">Elementy równorzędne są niedozwolone nakładają się na siebie.</span><span class="sxs-lookup"><span data-stu-id="4cbef-106">Siblings are not allowed to overlap.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4cbef-107">Składnia</span><span class="sxs-lookup"><span data-stu-id="4cbef-107">Syntax</span></span>  
  
```  
HRESULT OpenScope(  
    [in] ULONG32  scopeID,  
    [in] ULONG32  startOffset,  
    [in] ULONG32  endOffset);  
```  
  
## <a name="parameters"></a><span data-ttu-id="4cbef-108">Parametry</span><span class="sxs-lookup"><span data-stu-id="4cbef-108">Parameters</span></span>  
 `scopeId`  
 <span data-ttu-id="4cbef-109">[in] Identyfikator zakresu dla zakresu.</span><span class="sxs-lookup"><span data-stu-id="4cbef-109">[in] The scope identifier for the scope.</span></span>  
  
 `startOffset`  
 <span data-ttu-id="4cbef-110">[in] Przesunięcie w bajtach, pierwsza instrukcja w zakresie leksykalnym od samego początku metody.</span><span class="sxs-lookup"><span data-stu-id="4cbef-110">[in] The offset, in bytes, of the first instruction in the lexical scope from the beginning of the method.</span></span>  
  
 `endOffset`  
 <span data-ttu-id="4cbef-111">[in] Przesunięcie w bajtach ostatniej instrukcji w zakresie leksykalnym od samego początku metody.</span><span class="sxs-lookup"><span data-stu-id="4cbef-111">[in] The offset, in bytes, of the last instruction in the lexical scope from the beginning of the method.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="4cbef-112">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="4cbef-112">Return Value</span></span>  
 <span data-ttu-id="4cbef-113">S_OK, jeśli metoda się powiedzie; w przeciwnym razie E_FAIL lub innego kodu błędu.</span><span class="sxs-lookup"><span data-stu-id="4cbef-113">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="4cbef-114">Uwagi</span><span class="sxs-lookup"><span data-stu-id="4cbef-114">Remarks</span></span>  
 <span data-ttu-id="4cbef-115">[ISymUnmanagedWriter::OpenScope](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-openscope-method.md) zwraca identyfikator nieprzezroczysty zakres, który może być używany z `ISymUnmanagedWriter::SetScopeRange` Aby zdefiniować zakres użytkownika początkowe i końcowe przesunięcie w późniejszym czasie.</span><span class="sxs-lookup"><span data-stu-id="4cbef-115">[ISymUnmanagedWriter::OpenScope](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-openscope-method.md) returns an opaque scope identifier that can be used with `ISymUnmanagedWriter::SetScopeRange` to define a scope's starting and ending offset at a later time.</span></span> <span data-ttu-id="4cbef-116">W tym przypadku przesunięcia przekazany do `ISymUnmanagedWriter::OpenScope` i [ISymUnmanagedWriter::CloseScope](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-closescope-method.md) są ignorowane.</span><span class="sxs-lookup"><span data-stu-id="4cbef-116">In this case, the offsets passed to `ISymUnmanagedWriter::OpenScope` and [ISymUnmanagedWriter::CloseScope](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-closescope-method.md) are ignored.</span></span> <span data-ttu-id="4cbef-117">Zakres identyfikatorów są prawidłowe tylko w bieżącej metodzie.</span><span class="sxs-lookup"><span data-stu-id="4cbef-117">Scope identifiers are only valid in the current method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4cbef-118">Wymagania</span><span class="sxs-lookup"><span data-stu-id="4cbef-118">Requirements</span></span>  
 <span data-ttu-id="4cbef-119">**Nagłówek:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="4cbef-119">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4cbef-120">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="4cbef-120">See also</span></span>

- [<span data-ttu-id="4cbef-121">ISymUnmanagedWriter — Interfejs</span><span class="sxs-lookup"><span data-stu-id="4cbef-121">ISymUnmanagedWriter Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-interface.md)
