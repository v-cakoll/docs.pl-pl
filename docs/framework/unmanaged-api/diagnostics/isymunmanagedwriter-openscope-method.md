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
ms.openlocfilehash: 6aad2df19ec5563d8d48b0c286ab888a727c21ac
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="isymunmanagedwriteropenscope-method"></a><span data-ttu-id="ead33-102">ISymUnmanagedWriter::OpenScope — Metoda</span><span class="sxs-lookup"><span data-stu-id="ead33-102">ISymUnmanagedWriter::OpenScope Method</span></span>
<span data-ttu-id="ead33-103">Zostanie otwarty nowy zakres leksykalne w bieżącej metodzie.</span><span class="sxs-lookup"><span data-stu-id="ead33-103">Opens a new lexical scope in the current method.</span></span> <span data-ttu-id="ead33-104">Zakres staje się nowego zakresu i spoczywa na stosie zakresów.</span><span class="sxs-lookup"><span data-stu-id="ead33-104">The scope becomes the new current scope and is pushed onto a stack of scopes.</span></span> <span data-ttu-id="ead33-105">Zakresy muszą tworzyć hierarchię.</span><span class="sxs-lookup"><span data-stu-id="ead33-105">Scopes must form a hierarchy.</span></span> <span data-ttu-id="ead33-106">Elementy równorzędne nie może nakładać się.</span><span class="sxs-lookup"><span data-stu-id="ead33-106">Siblings are not allowed to overlap.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ead33-107">Składnia</span><span class="sxs-lookup"><span data-stu-id="ead33-107">Syntax</span></span>  
  
```  
HRESULT OpenScope(  
    [in] ULONG32 startOffset,  
    [out, retval] ULONG32* pRetVal);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="ead33-108">Parametry</span><span class="sxs-lookup"><span data-stu-id="ead33-108">Parameters</span></span>  
 `startOffset`  
 <span data-ttu-id="ead33-109">[in] Przesunięcie pierwszej instrukcji w zakresie leksykalne, w bajtach, od początku metody.</span><span class="sxs-lookup"><span data-stu-id="ead33-109">[in] The offset of the first instruction in the lexical scope, in bytes, from the beginning of the method.</span></span>  
  
 `pRetVal`  
 <span data-ttu-id="ead33-110">[out] Wskaźnik do `ULONG32` odbierająca identyfikator zakresu.</span><span class="sxs-lookup"><span data-stu-id="ead33-110">[out] A pointer to a `ULONG32` that receives the scope identifier.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="ead33-111">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="ead33-111">Return Value</span></span>  
 <span data-ttu-id="ead33-112">Wartość S_OK, jeśli metoda zakończy się pomyślnie; w przeciwnym razie E_FAIL lub inny kod błędu.</span><span class="sxs-lookup"><span data-stu-id="ead33-112">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ead33-113">Uwagi</span><span class="sxs-lookup"><span data-stu-id="ead33-113">Remarks</span></span>  
 <span data-ttu-id="ead33-114">`ISymUnmanagedWriter::OpenScope` Zwraca identyfikator zakresu nieprzezroczyste, który może być używany z [ISymUnmanagedWriter::SetScopeRange](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-setscoperange-method.md) do definiowania zakresu na początkową i końcową przesunięcie w późniejszym czasie.</span><span class="sxs-lookup"><span data-stu-id="ead33-114">`ISymUnmanagedWriter::OpenScope` returns an opaque scope identifier that can be used with [ISymUnmanagedWriter::SetScopeRange](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-setscoperange-method.md) to define a scope's starting and ending offset at a later time.</span></span> <span data-ttu-id="ead33-115">W takim przypadku przesunięcia przekazany do `ISymUnmanagedWriter::OpenScope` i [ISymUnmanagedWriter::CloseScope](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-closescope-method.md) są ignorowane.</span><span class="sxs-lookup"><span data-stu-id="ead33-115">In this case, the offsets passed to `ISymUnmanagedWriter::OpenScope` and [ISymUnmanagedWriter::CloseScope](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-closescope-method.md) are ignored.</span></span> <span data-ttu-id="ead33-116">Zakres identyfikatorów są prawidłowe tylko w bieżącej metodzie.</span><span class="sxs-lookup"><span data-stu-id="ead33-116">Scope identifiers are valid only in the current method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ead33-117">Wymagania</span><span class="sxs-lookup"><span data-stu-id="ead33-117">Requirements</span></span>  
 <span data-ttu-id="ead33-118">**Header:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="ead33-118">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ead33-119">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="ead33-119">See Also</span></span>  
 [<span data-ttu-id="ead33-120">ISymUnmanagedWriter, interfejs</span><span class="sxs-lookup"><span data-stu-id="ead33-120">ISymUnmanagedWriter Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-interface.md)
