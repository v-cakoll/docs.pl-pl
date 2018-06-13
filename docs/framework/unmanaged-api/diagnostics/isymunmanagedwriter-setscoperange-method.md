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
ms.openlocfilehash: 495089ca33df3b36656da149da45019c30b81d39
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33428729"
---
# <a name="isymunmanagedwritersetscoperange-method"></a><span data-ttu-id="56734-102">ISymUnmanagedWriter::SetScopeRange — Metoda</span><span class="sxs-lookup"><span data-stu-id="56734-102">ISymUnmanagedWriter::SetScopeRange Method</span></span>
<span data-ttu-id="56734-103">Definiuje zakres przesunięcia dla określonego zakresu leksykalne.</span><span class="sxs-lookup"><span data-stu-id="56734-103">Defines the offset range for the specified lexical scope.</span></span> <span data-ttu-id="56734-104">Zakres staje się nowego zakresu i spoczywa na stosie zakresów.</span><span class="sxs-lookup"><span data-stu-id="56734-104">The scope becomes the new current scope and is pushed onto a stack of scopes.</span></span> <span data-ttu-id="56734-105">Zakresy muszą tworzyć hierarchię.</span><span class="sxs-lookup"><span data-stu-id="56734-105">Scopes must form a hierarchy.</span></span> <span data-ttu-id="56734-106">Elementy równorzędne nie może nakładać się.</span><span class="sxs-lookup"><span data-stu-id="56734-106">Siblings are not allowed to overlap.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="56734-107">Składnia</span><span class="sxs-lookup"><span data-stu-id="56734-107">Syntax</span></span>  
  
```  
HRESULT OpenScope(  
    [in] ULONG32  scopeID,  
    [in] ULONG32  startOffset,  
    [in] ULONG32  endOffset);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="56734-108">Parametry</span><span class="sxs-lookup"><span data-stu-id="56734-108">Parameters</span></span>  
 `scopeId`  
 <span data-ttu-id="56734-109">[in] Identyfikator zakresu dla zakresu.</span><span class="sxs-lookup"><span data-stu-id="56734-109">[in] The scope identifier for the scope.</span></span>  
  
 `startOffset`  
 <span data-ttu-id="56734-110">[in] Przesunięcie w bajtach pierwszej instrukcji w zakresie leksykalne od początku metody.</span><span class="sxs-lookup"><span data-stu-id="56734-110">[in] The offset, in bytes, of the first instruction in the lexical scope from the beginning of the method.</span></span>  
  
 `endOffset`  
 <span data-ttu-id="56734-111">[in] Przesunięcie w bajtach ostatniej instrukcji w zakresie leksykalne od początku metody.</span><span class="sxs-lookup"><span data-stu-id="56734-111">[in] The offset, in bytes, of the last instruction in the lexical scope from the beginning of the method.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="56734-112">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="56734-112">Return Value</span></span>  
 <span data-ttu-id="56734-113">Wartość S_OK, jeśli metoda zakończy się pomyślnie; w przeciwnym razie E_FAIL lub inny kod błędu.</span><span class="sxs-lookup"><span data-stu-id="56734-113">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="56734-114">Uwagi</span><span class="sxs-lookup"><span data-stu-id="56734-114">Remarks</span></span>  
 <span data-ttu-id="56734-115">[ISymUnmanagedWriter::OpenScope](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-openscope-method.md) zwraca identyfikator zakresu nieprzezroczyste, który może być używany z `ISymUnmanagedWriter::SetScopeRange` do definiowania zakresu na początkową i końcową przesunięcie w późniejszym czasie.</span><span class="sxs-lookup"><span data-stu-id="56734-115">[ISymUnmanagedWriter::OpenScope](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-openscope-method.md) returns an opaque scope identifier that can be used with `ISymUnmanagedWriter::SetScopeRange` to define a scope's starting and ending offset at a later time.</span></span> <span data-ttu-id="56734-116">W takim przypadku przesunięcia przekazany do `ISymUnmanagedWriter::OpenScope` i [ISymUnmanagedWriter::CloseScope](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-closescope-method.md) są ignorowane.</span><span class="sxs-lookup"><span data-stu-id="56734-116">In this case, the offsets passed to `ISymUnmanagedWriter::OpenScope` and [ISymUnmanagedWriter::CloseScope](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-closescope-method.md) are ignored.</span></span> <span data-ttu-id="56734-117">Zakres identyfikatorów są prawidłowe tylko w bieżącej metodzie.</span><span class="sxs-lookup"><span data-stu-id="56734-117">Scope identifiers are only valid in the current method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="56734-118">Wymagania</span><span class="sxs-lookup"><span data-stu-id="56734-118">Requirements</span></span>  
 <span data-ttu-id="56734-119">**Header:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="56734-119">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="56734-120">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="56734-120">See Also</span></span>  
 [<span data-ttu-id="56734-121">ISymUnmanagedWriter, interfejs</span><span class="sxs-lookup"><span data-stu-id="56734-121">ISymUnmanagedWriter Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-interface.md)
