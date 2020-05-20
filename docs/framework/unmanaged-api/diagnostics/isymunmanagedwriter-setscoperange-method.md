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
ms.openlocfilehash: b57bb549278f62cdce6ed5deaaa62f154ec919b5
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/19/2020
ms.locfileid: "83609368"
---
# <a name="isymunmanagedwritersetscoperange-method"></a><span data-ttu-id="59c21-102">ISymUnmanagedWriter::SetScopeRange — Metoda</span><span class="sxs-lookup"><span data-stu-id="59c21-102">ISymUnmanagedWriter::SetScopeRange Method</span></span>
<span data-ttu-id="59c21-103">Definiuje zakres przesunięć dla określonego zakresu leksykalnego.</span><span class="sxs-lookup"><span data-stu-id="59c21-103">Defines the offset range for the specified lexical scope.</span></span> <span data-ttu-id="59c21-104">Zakres będzie nowym bieżącym zakresem i jest wypychany do stosu zakresów.</span><span class="sxs-lookup"><span data-stu-id="59c21-104">The scope becomes the new current scope and is pushed onto a stack of scopes.</span></span> <span data-ttu-id="59c21-105">Zakresy muszą tworzyć hierarchię.</span><span class="sxs-lookup"><span data-stu-id="59c21-105">Scopes must form a hierarchy.</span></span> <span data-ttu-id="59c21-106">Elementy równorzędne nie mogą nakładać się na siebie.</span><span class="sxs-lookup"><span data-stu-id="59c21-106">Siblings are not allowed to overlap.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="59c21-107">Składnia</span><span class="sxs-lookup"><span data-stu-id="59c21-107">Syntax</span></span>  
  
```cpp  
HRESULT OpenScope(  
    [in] ULONG32  scopeID,  
    [in] ULONG32  startOffset,  
    [in] ULONG32  endOffset);  
```  
  
## <a name="parameters"></a><span data-ttu-id="59c21-108">Parametry</span><span class="sxs-lookup"><span data-stu-id="59c21-108">Parameters</span></span>  
 `scopeId`  
 <span data-ttu-id="59c21-109">podczas Identyfikator zakresu dla zakresu.</span><span class="sxs-lookup"><span data-stu-id="59c21-109">[in] The scope identifier for the scope.</span></span>  
  
 `startOffset`  
 <span data-ttu-id="59c21-110">podczas Przesunięcie, w bajtach, pierwszej instrukcji w zakresie leksykalnym od początku metody.</span><span class="sxs-lookup"><span data-stu-id="59c21-110">[in] The offset, in bytes, of the first instruction in the lexical scope from the beginning of the method.</span></span>  
  
 `endOffset`  
 <span data-ttu-id="59c21-111">podczas Przesunięcie, w bajtach, ostatniej instrukcji w zakresie leksykalnym od początku metody.</span><span class="sxs-lookup"><span data-stu-id="59c21-111">[in] The offset, in bytes, of the last instruction in the lexical scope from the beginning of the method.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="59c21-112">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="59c21-112">Return Value</span></span>  
 <span data-ttu-id="59c21-113">S_OK, jeśli metoda się powiedzie; w przeciwnym razie E_FAIL lub inny kod błędu.</span><span class="sxs-lookup"><span data-stu-id="59c21-113">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="59c21-114">Uwagi</span><span class="sxs-lookup"><span data-stu-id="59c21-114">Remarks</span></span>  
 <span data-ttu-id="59c21-115">[ISymUnmanagedWriter:: OpenScope —](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-openscope-method.md) zwraca nieprzezroczysty identyfikator zakresu, którego można użyć w `ISymUnmanagedWriter::SetScopeRange` celu zdefiniowania początkowego i końcowego przesunięcia zakresu w późniejszym czasie.</span><span class="sxs-lookup"><span data-stu-id="59c21-115">[ISymUnmanagedWriter::OpenScope](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-openscope-method.md) returns an opaque scope identifier that can be used with `ISymUnmanagedWriter::SetScopeRange` to define a scope's starting and ending offset at a later time.</span></span> <span data-ttu-id="59c21-116">W takim przypadku przesunięcia przesłane do `ISymUnmanagedWriter::OpenScope` i [ISymUnmanagedWriter:: CloseScope —](isymunmanagedwriter-closescope-method.md) są ignorowane.</span><span class="sxs-lookup"><span data-stu-id="59c21-116">In this case, the offsets passed to `ISymUnmanagedWriter::OpenScope` and [ISymUnmanagedWriter::CloseScope](isymunmanagedwriter-closescope-method.md) are ignored.</span></span> <span data-ttu-id="59c21-117">Identyfikatory zakresów są prawidłowe tylko w bieżącej metodzie.</span><span class="sxs-lookup"><span data-stu-id="59c21-117">Scope identifiers are only valid in the current method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="59c21-118">Wymagania</span><span class="sxs-lookup"><span data-stu-id="59c21-118">Requirements</span></span>  
 <span data-ttu-id="59c21-119">**Nagłówek:** CorSym. idl, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="59c21-119">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="59c21-120">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="59c21-120">See also</span></span>

- [<span data-ttu-id="59c21-121">ISymUnmanagedWriter — Interfejs</span><span class="sxs-lookup"><span data-stu-id="59c21-121">ISymUnmanagedWriter Interface</span></span>](isymunmanagedwriter-interface.md)
