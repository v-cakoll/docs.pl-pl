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
ms.openlocfilehash: 674089f8a1076342a2479c64e253b7dda53ade87
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/19/2020
ms.locfileid: "83615205"
---
# <a name="isymunmanagedwriterdefineglobalvariable-method"></a><span data-ttu-id="4077e-102">ISymUnmanagedWriter::DefineGlobalVariable — Metoda</span><span class="sxs-lookup"><span data-stu-id="4077e-102">ISymUnmanagedWriter::DefineGlobalVariable Method</span></span>
<span data-ttu-id="4077e-103">Definiuje pojedynczą zmienną globalną.</span><span class="sxs-lookup"><span data-stu-id="4077e-103">Defines a single global variable.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4077e-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="4077e-104">Syntax</span></span>  
  
```cpp  
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
  
## <a name="parameters"></a><span data-ttu-id="4077e-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="4077e-105">Parameters</span></span>  
 `name`  
 <span data-ttu-id="4077e-106">podczas Wskaźnik do elementu `WCHAR` , który definiuje globalną nazwę zmiennej.</span><span class="sxs-lookup"><span data-stu-id="4077e-106">[in] A pointer to a `WCHAR` that defines the global variable name.</span></span>  
  
 `attributes`  
 <span data-ttu-id="4077e-107">podczas Atrybuty zmiennej globalnej.</span><span class="sxs-lookup"><span data-stu-id="4077e-107">[in] The global variable attributes.</span></span>  
  
 `cSig`  
 <span data-ttu-id="4077e-108">podczas `ULONG32`Wskazuje rozmiar bufora (w znakach) `signature` .</span><span class="sxs-lookup"><span data-stu-id="4077e-108">[in] A `ULONG32` that indicates the size, in characters, of the `signature` buffer.</span></span>  
  
 `signature`  
 <span data-ttu-id="4077e-109">podczas Podpis zmiennej globalnej.</span><span class="sxs-lookup"><span data-stu-id="4077e-109">[in] The global variable signature.</span></span>  
  
 `addrKind`  
 <span data-ttu-id="4077e-110">podczas Typ adresu.</span><span class="sxs-lookup"><span data-stu-id="4077e-110">[in] The address type.</span></span>  
  
 `addr1`  
 <span data-ttu-id="4077e-111">podczas Pierwszy adres dla specyfikacji parametru.</span><span class="sxs-lookup"><span data-stu-id="4077e-111">[in] The first address for the parameter specification.</span></span>  
  
 `addr2`  
 <span data-ttu-id="4077e-112">podczas Drugi adres dla specyfikacji parametru.</span><span class="sxs-lookup"><span data-stu-id="4077e-112">[in] The second address for the parameter specification.</span></span>  
  
 `addr3`  
 <span data-ttu-id="4077e-113">podczas Trzeci adres dla specyfikacji parametru.</span><span class="sxs-lookup"><span data-stu-id="4077e-113">[in] The third address for the parameter specification.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="4077e-114">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="4077e-114">Return Value</span></span>  
 <span data-ttu-id="4077e-115">S_OK, jeśli metoda się powiedzie; w przeciwnym razie E_FAIL lub inny kod błędu.</span><span class="sxs-lookup"><span data-stu-id="4077e-115">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4077e-116">Wymagania</span><span class="sxs-lookup"><span data-stu-id="4077e-116">Requirements</span></span>  
 <span data-ttu-id="4077e-117">**Nagłówek:** CorSym. idl, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="4077e-117">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4077e-118">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="4077e-118">See also</span></span>

- [<span data-ttu-id="4077e-119">ISymUnmanagedWriter — Interfejs</span><span class="sxs-lookup"><span data-stu-id="4077e-119">ISymUnmanagedWriter Interface</span></span>](isymunmanagedwriter-interface.md)
- [<span data-ttu-id="4077e-120">DefineLocalVariable, metoda</span><span class="sxs-lookup"><span data-stu-id="4077e-120">DefineLocalVariable Method</span></span>](isymunmanagedwriter-definelocalvariable-method.md)
- [<span data-ttu-id="4077e-121">DefineGlobalVariable2, metoda</span><span class="sxs-lookup"><span data-stu-id="4077e-121">DefineGlobalVariable2 Method</span></span>](isymunmanagedwriter2-defineglobalvariable2-method.md)
