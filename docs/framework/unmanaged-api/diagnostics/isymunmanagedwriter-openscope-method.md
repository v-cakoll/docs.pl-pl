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
ms.openlocfilehash: 4008b2a7d785781da5f35b3dc1e564487cb8e760
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/19/2020
ms.locfileid: "83609784"
---
# <a name="isymunmanagedwriteropenscope-method"></a><span data-ttu-id="26506-102">ISymUnmanagedWriter::OpenScope — Metoda</span><span class="sxs-lookup"><span data-stu-id="26506-102">ISymUnmanagedWriter::OpenScope Method</span></span>
<span data-ttu-id="26506-103">Otwiera nowy zakres leksykalny w bieżącej metodzie.</span><span class="sxs-lookup"><span data-stu-id="26506-103">Opens a new lexical scope in the current method.</span></span> <span data-ttu-id="26506-104">Zakres będzie nowym bieżącym zakresem i jest wypychany do stosu zakresów.</span><span class="sxs-lookup"><span data-stu-id="26506-104">The scope becomes the new current scope and is pushed onto a stack of scopes.</span></span> <span data-ttu-id="26506-105">Zakresy muszą tworzyć hierarchię.</span><span class="sxs-lookup"><span data-stu-id="26506-105">Scopes must form a hierarchy.</span></span> <span data-ttu-id="26506-106">Elementy równorzędne nie mogą nakładać się na siebie.</span><span class="sxs-lookup"><span data-stu-id="26506-106">Siblings are not allowed to overlap.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="26506-107">Składnia</span><span class="sxs-lookup"><span data-stu-id="26506-107">Syntax</span></span>  
  
```cpp  
HRESULT OpenScope(  
    [in] ULONG32 startOffset,  
    [out, retval] ULONG32* pRetVal);  
```  
  
## <a name="parameters"></a><span data-ttu-id="26506-108">Parametry</span><span class="sxs-lookup"><span data-stu-id="26506-108">Parameters</span></span>  
 `startOffset`  
 <span data-ttu-id="26506-109">podczas Przesunięcie pierwszej instrukcji w zakresie leksykalnym (w bajtach) od początku metody.</span><span class="sxs-lookup"><span data-stu-id="26506-109">[in] The offset of the first instruction in the lexical scope, in bytes, from the beginning of the method.</span></span>  
  
 `pRetVal`  
 <span data-ttu-id="26506-110">określoną Wskaźnik do elementu `ULONG32` , który odbiera identyfikator zakresu.</span><span class="sxs-lookup"><span data-stu-id="26506-110">[out] A pointer to a `ULONG32` that receives the scope identifier.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="26506-111">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="26506-111">Return Value</span></span>  
 <span data-ttu-id="26506-112">S_OK, jeśli metoda się powiedzie; w przeciwnym razie E_FAIL lub inny kod błędu.</span><span class="sxs-lookup"><span data-stu-id="26506-112">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="26506-113">Uwagi</span><span class="sxs-lookup"><span data-stu-id="26506-113">Remarks</span></span>  
 <span data-ttu-id="26506-114">`ISymUnmanagedWriter::OpenScope`zwraca nieprzezroczysty identyfikator zakresu, który może być używany z [ISymUnmanagedWriter:: SetScopeRange —](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-setscoperange-method.md) w celu zdefiniowania początkowego i końcowego przesunięcia zakresu w późniejszym czasie.</span><span class="sxs-lookup"><span data-stu-id="26506-114">`ISymUnmanagedWriter::OpenScope` returns an opaque scope identifier that can be used with [ISymUnmanagedWriter::SetScopeRange](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-setscoperange-method.md) to define a scope's starting and ending offset at a later time.</span></span> <span data-ttu-id="26506-115">W takim przypadku przesunięcia przesłane do `ISymUnmanagedWriter::OpenScope` i [ISymUnmanagedWriter:: CloseScope —](isymunmanagedwriter-closescope-method.md) są ignorowane.</span><span class="sxs-lookup"><span data-stu-id="26506-115">In this case, the offsets passed to `ISymUnmanagedWriter::OpenScope` and [ISymUnmanagedWriter::CloseScope](isymunmanagedwriter-closescope-method.md) are ignored.</span></span> <span data-ttu-id="26506-116">Identyfikatory zakresów są prawidłowe tylko w bieżącej metodzie.</span><span class="sxs-lookup"><span data-stu-id="26506-116">Scope identifiers are valid only in the current method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="26506-117">Wymagania</span><span class="sxs-lookup"><span data-stu-id="26506-117">Requirements</span></span>  
 <span data-ttu-id="26506-118">**Nagłówek:** CorSym. idl, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="26506-118">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="26506-119">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="26506-119">See also</span></span>

- [<span data-ttu-id="26506-120">ISymUnmanagedWriter — Interfejs</span><span class="sxs-lookup"><span data-stu-id="26506-120">ISymUnmanagedWriter Interface</span></span>](isymunmanagedwriter-interface.md)
