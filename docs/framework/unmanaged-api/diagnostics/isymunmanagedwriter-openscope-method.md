---
title: "ISymUnmanagedWriter::OpenScope — Metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ISymUnmanagedWriter.OpenScope
api_location: diasymreader.dll
api_type: COM
f1_keywords: ISymUnmanagedWriter::OpenScope
helpviewer_keywords:
- OpenScope method, ISymUnmanagedWriter interface [.NET Framework debugging]
- ISymUnmanagedWriter::OpenScope method [.NET Framework debugging]
ms.assetid: dbea0644-3873-4329-90b8-624163e87467
topic_type: apiref
caps.latest.revision: "11"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: f56bc14b096b5086db1fc8d046ed699559381fb0
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="isymunmanagedwriteropenscope-method"></a><span data-ttu-id="f63d0-102">ISymUnmanagedWriter::OpenScope — Metoda</span><span class="sxs-lookup"><span data-stu-id="f63d0-102">ISymUnmanagedWriter::OpenScope Method</span></span>
<span data-ttu-id="f63d0-103">Zostanie otwarty nowy zakres leksykalne w bieżącej metodzie.</span><span class="sxs-lookup"><span data-stu-id="f63d0-103">Opens a new lexical scope in the current method.</span></span> <span data-ttu-id="f63d0-104">Zakres staje się nowego zakresu i spoczywa na stosie zakresów.</span><span class="sxs-lookup"><span data-stu-id="f63d0-104">The scope becomes the new current scope and is pushed onto a stack of scopes.</span></span> <span data-ttu-id="f63d0-105">Zakresy muszą tworzyć hierarchię.</span><span class="sxs-lookup"><span data-stu-id="f63d0-105">Scopes must form a hierarchy.</span></span> <span data-ttu-id="f63d0-106">Elementy równorzędne nie może nakładać się.</span><span class="sxs-lookup"><span data-stu-id="f63d0-106">Siblings are not allowed to overlap.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f63d0-107">Składnia</span><span class="sxs-lookup"><span data-stu-id="f63d0-107">Syntax</span></span>  
  
```  
HRESULT OpenScope(  
    [in] ULONG32 startOffset,  
    [out, retval] ULONG32* pRetVal);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="f63d0-108">Parametry</span><span class="sxs-lookup"><span data-stu-id="f63d0-108">Parameters</span></span>  
 `startOffset`  
 <span data-ttu-id="f63d0-109">[in] Przesunięcie pierwszej instrukcji w zakresie leksykalne, w bajtach, od początku metody.</span><span class="sxs-lookup"><span data-stu-id="f63d0-109">[in] The offset of the first instruction in the lexical scope, in bytes, from the beginning of the method.</span></span>  
  
 `pRetVal`  
 <span data-ttu-id="f63d0-110">[out] Wskaźnik do `ULONG32` odbierająca identyfikator zakresu.</span><span class="sxs-lookup"><span data-stu-id="f63d0-110">[out] A pointer to a `ULONG32` that receives the scope identifier.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="f63d0-111">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="f63d0-111">Return Value</span></span>  
 <span data-ttu-id="f63d0-112">Wartość S_OK, jeśli metoda zakończy się pomyślnie; w przeciwnym razie E_FAIL lub inny kod błędu.</span><span class="sxs-lookup"><span data-stu-id="f63d0-112">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="f63d0-113">Uwagi</span><span class="sxs-lookup"><span data-stu-id="f63d0-113">Remarks</span></span>  
 <span data-ttu-id="f63d0-114">`ISymUnmanagedWriter::OpenScope`Zwraca identyfikator zakresu nieprzezroczyste, który może być używany z [ISymUnmanagedWriter::SetScopeRange](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-setscoperange-method.md) do definiowania zakresu na początkową i końcową przesunięcie w późniejszym czasie.</span><span class="sxs-lookup"><span data-stu-id="f63d0-114">`ISymUnmanagedWriter::OpenScope` returns an opaque scope identifier that can be used with [ISymUnmanagedWriter::SetScopeRange](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-setscoperange-method.md) to define a scope's starting and ending offset at a later time.</span></span> <span data-ttu-id="f63d0-115">W takim przypadku przesunięcia przekazany do `ISymUnmanagedWriter::OpenScope` i [ISymUnmanagedWriter::CloseScope](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-closescope-method.md) są ignorowane.</span><span class="sxs-lookup"><span data-stu-id="f63d0-115">In this case, the offsets passed to `ISymUnmanagedWriter::OpenScope` and [ISymUnmanagedWriter::CloseScope](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-closescope-method.md) are ignored.</span></span> <span data-ttu-id="f63d0-116">Zakres identyfikatorów są prawidłowe tylko w bieżącej metodzie.</span><span class="sxs-lookup"><span data-stu-id="f63d0-116">Scope identifiers are valid only in the current method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f63d0-117">Wymagania</span><span class="sxs-lookup"><span data-stu-id="f63d0-117">Requirements</span></span>  
 <span data-ttu-id="f63d0-118">**Nagłówek:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="f63d0-118">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f63d0-119">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="f63d0-119">See Also</span></span>  
 [<span data-ttu-id="f63d0-120">ISymUnmanagedWriter — interfejs</span><span class="sxs-lookup"><span data-stu-id="f63d0-120">ISymUnmanagedWriter Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-interface.md)
