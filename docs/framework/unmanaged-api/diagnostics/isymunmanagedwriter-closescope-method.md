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
ms.openlocfilehash: 250e58e4153edbee5c327ad46ecde73e94b83584
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/06/2019
ms.locfileid: "57468719"
---
# <a name="isymunmanagedwriterclosescope-method"></a><span data-ttu-id="39cd6-102">ISymUnmanagedWriter::CloseScope — Metoda</span><span class="sxs-lookup"><span data-stu-id="39cd6-102">ISymUnmanagedWriter::CloseScope Method</span></span>
<span data-ttu-id="39cd6-103">Zamyka bieżący zakresie leksykalnym.</span><span class="sxs-lookup"><span data-stu-id="39cd6-103">Closes the current lexical scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="39cd6-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="39cd6-104">Syntax</span></span>  
  
```  
HRESULT CloseScope(  
    [in] ULONG32 endOffset);  
```  
  
## <a name="parameters"></a><span data-ttu-id="39cd6-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="39cd6-105">Parameters</span></span>  
 `endOffset`  
 <span data-ttu-id="39cd6-106">[in] Przesunięcie od początku metody punktu na końcu ostatniego instrukcji w zakresie leksykalnym, w bajtach.</span><span class="sxs-lookup"><span data-stu-id="39cd6-106">[in] The offset from the beginning of the method of the point at the end of the last instruction in the lexical scope, in bytes.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="39cd6-107">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="39cd6-107">Return Value</span></span>  
 <span data-ttu-id="39cd6-108">S_OK, jeśli metoda się powiedzie; w przeciwnym razie E_FAIL lub innego kodu błędu.</span><span class="sxs-lookup"><span data-stu-id="39cd6-108">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="39cd6-109">Uwagi</span><span class="sxs-lookup"><span data-stu-id="39cd6-109">Remarks</span></span>  
 <span data-ttu-id="39cd6-110">Po zamknięciu zakresu nie więcej zmiennych można zdefiniować w nim.</span><span class="sxs-lookup"><span data-stu-id="39cd6-110">Once a scope is closed, no more variables can be defined within it.</span></span>  
  
 <span data-ttu-id="39cd6-111">[ISymUnmanagedWriter::OpenScope](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-openscope-method.md) zwraca identyfikator nieprzezroczysty zakres, który może być używany z [ISymUnmanagedWriter::SetScopeRange](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-setscoperange-method.md) później określić zakres użytkownika początkowe i końcowe przesunięcie.</span><span class="sxs-lookup"><span data-stu-id="39cd6-111">[ISymUnmanagedWriter::OpenScope](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-openscope-method.md) returns an opaque scope identifier that can be used with [ISymUnmanagedWriter::SetScopeRange](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-setscoperange-method.md) to later define a scope's starting and ending offset.</span></span> <span data-ttu-id="39cd6-112">W tym przypadku przesunięcia przekazany do `ISymUnmanagedWriter::OpenScope` i `ISymUnmanagedWriter::CloseScope` są ignorowane.</span><span class="sxs-lookup"><span data-stu-id="39cd6-112">In this case, the offsets passed to `ISymUnmanagedWriter::OpenScope` and `ISymUnmanagedWriter::CloseScope` are ignored.</span></span> <span data-ttu-id="39cd6-113">Zakres identyfikatorów są prawidłowe tylko w bieżącej metodzie.</span><span class="sxs-lookup"><span data-stu-id="39cd6-113">Scope identifiers are valid only in the current method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="39cd6-114">Wymagania</span><span class="sxs-lookup"><span data-stu-id="39cd6-114">Requirements</span></span>  
 <span data-ttu-id="39cd6-115">**Nagłówek:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="39cd6-115">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="39cd6-116">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="39cd6-116">See also</span></span>
- [<span data-ttu-id="39cd6-117">ISymUnmanagedWriter, interfejs</span><span class="sxs-lookup"><span data-stu-id="39cd6-117">ISymUnmanagedWriter Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-interface.md)
