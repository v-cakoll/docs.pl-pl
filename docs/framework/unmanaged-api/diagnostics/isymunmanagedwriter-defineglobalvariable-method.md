---
title: ISymUnmanagedWriter::DefineGlobalVariable — Metoda
ms.date: 03/30/2017
api_name:
- ISymUnmanagedWriter.DefineGlobalVariable
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedWriter::DefineGlobalVariable
helpviewer_keywords:
- ISymUnmanagedWriter::DefineGlobalVariable method [.NET Framework debugging]
- DefineGlobalVariable method [.NET Framework debugging]
ms.assetid: 843c904a-8176-4d8f-bd47-b4d4c29f4c5c
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 66efe5ae1fe2154684d2ac6791895b7fcbe4f7b6
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59225923"
---
# <a name="isymunmanagedwriterdefineglobalvariable-method"></a><span data-ttu-id="75719-102">ISymUnmanagedWriter::DefineGlobalVariable — Metoda</span><span class="sxs-lookup"><span data-stu-id="75719-102">ISymUnmanagedWriter::DefineGlobalVariable Method</span></span>
<span data-ttu-id="75719-103">Definiuje jednej zmiennej globalnej.</span><span class="sxs-lookup"><span data-stu-id="75719-103">Defines a single global variable.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="75719-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="75719-104">Syntax</span></span>  
  
```  
HRESULT DefineGlobalVariable(  
    [in] const WCHAR  *name,  
    [in] ULONG32      attributes,  
    [in] ULONG32      cSig,  
    [in, size_is(cSig)] unsigned char signature[],  
    [in] ULONG32      addrKind,  
    [in] ULONG32      addr1,  
    [in] ULONG32      addr2,  
    [in] ULONG32      addr3);  
```  
  
## <a name="parameters"></a><span data-ttu-id="75719-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="75719-105">Parameters</span></span>  
 `name`  
 <span data-ttu-id="75719-106">[in] Wskaźnik do `WCHAR` definiujący nazwa zmiennej globalnej.</span><span class="sxs-lookup"><span data-stu-id="75719-106">[in] A pointer to a `WCHAR` that defines the global variable name.</span></span>  
  
 `attributes`  
 <span data-ttu-id="75719-107">[in] Atrybuty globalne zmiennej.</span><span class="sxs-lookup"><span data-stu-id="75719-107">[in] The global variable attributes.</span></span>  
  
 `cSig`  
 <span data-ttu-id="75719-108">[in] A `ULONG32` rozmiar, w postaci, który wskazuje z `signature` buforu.</span><span class="sxs-lookup"><span data-stu-id="75719-108">[in] A `ULONG32` that indicates the size, in characters, of the `signature` buffer.</span></span>  
  
 `signature`  
 <span data-ttu-id="75719-109">[in] Globalne podpis zmiennej.</span><span class="sxs-lookup"><span data-stu-id="75719-109">[in] The global variable signature.</span></span>  
  
 `addrKind`  
 <span data-ttu-id="75719-110">[in] Typ adresu.</span><span class="sxs-lookup"><span data-stu-id="75719-110">[in] The address type.</span></span>  
  
 `addr1`  
 <span data-ttu-id="75719-111">[in] Pierwszy adres specyfikację parametru.</span><span class="sxs-lookup"><span data-stu-id="75719-111">[in] The first address for the parameter specification.</span></span>  
  
 `addr2`  
 <span data-ttu-id="75719-112">[in] Drugi adres specyfikację parametru.</span><span class="sxs-lookup"><span data-stu-id="75719-112">[in] The second address for the parameter specification.</span></span>  
  
 `addr3`  
 <span data-ttu-id="75719-113">[in] Trzeci adres specyfikację parametru.</span><span class="sxs-lookup"><span data-stu-id="75719-113">[in] The third address for the parameter specification.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="75719-114">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="75719-114">Return Value</span></span>  
 <span data-ttu-id="75719-115">S_OK, jeśli metoda się powiedzie; w przeciwnym razie E_FAIL lub innego kodu błędu.</span><span class="sxs-lookup"><span data-stu-id="75719-115">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="75719-116">Wymagania</span><span class="sxs-lookup"><span data-stu-id="75719-116">Requirements</span></span>  
 <span data-ttu-id="75719-117">**Nagłówek:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="75719-117">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="75719-118">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="75719-118">See also</span></span>

- [<span data-ttu-id="75719-119">ISymUnmanagedWriter — Interfejs</span><span class="sxs-lookup"><span data-stu-id="75719-119">ISymUnmanagedWriter Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-interface.md)
- [<span data-ttu-id="75719-120">DefineLocalVariable, metoda</span><span class="sxs-lookup"><span data-stu-id="75719-120">DefineLocalVariable Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-definelocalvariable-method.md)
- [<span data-ttu-id="75719-121">DefineGlobalVariable2, metoda</span><span class="sxs-lookup"><span data-stu-id="75719-121">DefineGlobalVariable2 Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter2-defineglobalvariable2-method.md)
