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
ms.openlocfilehash: 2808606be24399c9a4fe03df4c53202d31cbbe91
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/08/2020
ms.locfileid: "84501719"
---
# <a name="isymunmanagedwriteropenscope-method"></a><span data-ttu-id="e947e-102">ISymUnmanagedWriter::OpenScope — Metoda</span><span class="sxs-lookup"><span data-stu-id="e947e-102">ISymUnmanagedWriter::OpenScope Method</span></span>
<span data-ttu-id="e947e-103">Otwiera nowy zakres leksykalny w bieżącej metodzie.</span><span class="sxs-lookup"><span data-stu-id="e947e-103">Opens a new lexical scope in the current method.</span></span> <span data-ttu-id="e947e-104">Zakres będzie nowym bieżącym zakresem i jest wypychany do stosu zakresów.</span><span class="sxs-lookup"><span data-stu-id="e947e-104">The scope becomes the new current scope and is pushed onto a stack of scopes.</span></span> <span data-ttu-id="e947e-105">Zakresy muszą tworzyć hierarchię.</span><span class="sxs-lookup"><span data-stu-id="e947e-105">Scopes must form a hierarchy.</span></span> <span data-ttu-id="e947e-106">Elementy równorzędne nie mogą nakładać się na siebie.</span><span class="sxs-lookup"><span data-stu-id="e947e-106">Siblings are not allowed to overlap.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e947e-107">Składnia</span><span class="sxs-lookup"><span data-stu-id="e947e-107">Syntax</span></span>  
  
```cpp  
HRESULT OpenScope(  
    [in] ULONG32 startOffset,  
    [out, retval] ULONG32* pRetVal);  
```  
  
## <a name="parameters"></a><span data-ttu-id="e947e-108">Parametry</span><span class="sxs-lookup"><span data-stu-id="e947e-108">Parameters</span></span>  
 `startOffset`  
 <span data-ttu-id="e947e-109">podczas Przesunięcie pierwszej instrukcji w zakresie leksykalnym (w bajtach) od początku metody.</span><span class="sxs-lookup"><span data-stu-id="e947e-109">[in] The offset of the first instruction in the lexical scope, in bytes, from the beginning of the method.</span></span>  
  
 `pRetVal`  
 <span data-ttu-id="e947e-110">określoną Wskaźnik do elementu `ULONG32` , który odbiera identyfikator zakresu.</span><span class="sxs-lookup"><span data-stu-id="e947e-110">[out] A pointer to a `ULONG32` that receives the scope identifier.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="e947e-111">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="e947e-111">Return Value</span></span>  
 <span data-ttu-id="e947e-112">S_OK, jeśli metoda się powiedzie; w przeciwnym razie E_FAIL lub inny kod błędu.</span><span class="sxs-lookup"><span data-stu-id="e947e-112">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="e947e-113">Uwagi</span><span class="sxs-lookup"><span data-stu-id="e947e-113">Remarks</span></span>  
 <span data-ttu-id="e947e-114">`ISymUnmanagedWriter::OpenScope`zwraca nieprzezroczysty identyfikator zakresu, który może być używany z [ISymUnmanagedWriter:: SetScopeRange —](isymunmanagedwriter-setscoperange-method.md) w celu zdefiniowania początkowego i końcowego przesunięcia zakresu w późniejszym czasie.</span><span class="sxs-lookup"><span data-stu-id="e947e-114">`ISymUnmanagedWriter::OpenScope` returns an opaque scope identifier that can be used with [ISymUnmanagedWriter::SetScopeRange](isymunmanagedwriter-setscoperange-method.md) to define a scope's starting and ending offset at a later time.</span></span> <span data-ttu-id="e947e-115">W takim przypadku przesunięcia przesłane do `ISymUnmanagedWriter::OpenScope` i [ISymUnmanagedWriter:: CloseScope —](isymunmanagedwriter-closescope-method.md) są ignorowane.</span><span class="sxs-lookup"><span data-stu-id="e947e-115">In this case, the offsets passed to `ISymUnmanagedWriter::OpenScope` and [ISymUnmanagedWriter::CloseScope](isymunmanagedwriter-closescope-method.md) are ignored.</span></span> <span data-ttu-id="e947e-116">Identyfikatory zakresów są prawidłowe tylko w bieżącej metodzie.</span><span class="sxs-lookup"><span data-stu-id="e947e-116">Scope identifiers are valid only in the current method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e947e-117">Wymagania</span><span class="sxs-lookup"><span data-stu-id="e947e-117">Requirements</span></span>  
 <span data-ttu-id="e947e-118">**Nagłówek:** CorSym. idl, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="e947e-118">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e947e-119">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="e947e-119">See also</span></span>

- [<span data-ttu-id="e947e-120">ISymUnmanagedWriter — Interfejs</span><span class="sxs-lookup"><span data-stu-id="e947e-120">ISymUnmanagedWriter Interface</span></span>](isymunmanagedwriter-interface.md)
