---
title: ISymUnmanagedWriter::DefineField — Metoda
ms.date: 03/30/2017
api_name:
- ISymUnmanagedWriter.DefineField
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedWriter::DefineField
helpviewer_keywords:
- ISymUnmanagedWriter::DefineField method [.NET Framework debugging]
- DefineField method, ISymUnmanagedWriter interface [.NET Framework debugging]
ms.assetid: c6a1f797-dbf4-40f5-ab99-d9b4bfb26148
topic_type:
- apiref
ms.openlocfilehash: 7eea63cae27c08260177dfc7746046b975434611
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/23/2019
ms.locfileid: "74428033"
---
# <a name="isymunmanagedwriterdefinefield-method"></a><span data-ttu-id="df557-102">ISymUnmanagedWriter::DefineField — Metoda</span><span class="sxs-lookup"><span data-stu-id="df557-102">ISymUnmanagedWriter::DefineField Method</span></span>
<span data-ttu-id="df557-103">Definiuje pojedynczą zmienną, która nie znajduje się w metodzie.</span><span class="sxs-lookup"><span data-stu-id="df557-103">Defines a single variable that is not within a method.</span></span> <span data-ttu-id="df557-104">Ta metoda jest używana w przypadku niektórych pól klas, pól bitowych i tak dalej.</span><span class="sxs-lookup"><span data-stu-id="df557-104">This method is used for certain fields in classes, bit fields, and so on.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="df557-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="df557-105">Syntax</span></span>  
  
```cpp  
HRESULT DefineField(  
    [in] mdTypeDef    parent,  
    [in] const WCHAR  *name,  
    [in] ULONG32      attributes,  
    [in] ULONG32      cSig,  
    [in, size_is(cSig)] unsigned char signature[],  
    [in] ULONG32      addrKind,  
    [in] ULONG32      addr1,  
    [in] ULONG32      addr2,  
    [in] ULONG32      addr3);  
```  
  
## <a name="parameters"></a><span data-ttu-id="df557-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="df557-106">Parameters</span></span>  
 `parent`  
 <span data-ttu-id="df557-107">podczas Typ metadanych lub token metody.</span><span class="sxs-lookup"><span data-stu-id="df557-107">[in] The metadata type or method token.</span></span>  
  
 `name`  
 <span data-ttu-id="df557-108">podczas Nazwa pola.</span><span class="sxs-lookup"><span data-stu-id="df557-108">[in] The field name.</span></span>  
  
 `attributes`  
 <span data-ttu-id="df557-109">podczas Atrybuty pola.</span><span class="sxs-lookup"><span data-stu-id="df557-109">[in] The field attributes.</span></span>  
  
 `cSig`  
 <span data-ttu-id="df557-110">podczas `ULONG32`, który jest rozmiarem (w znakach) bufora wymaganego do zawierania podpisu pola.</span><span class="sxs-lookup"><span data-stu-id="df557-110">[in] A `ULONG32` that is the size, in characters, of the buffer required to contain the field signature.</span></span>  
  
 `signature`  
 <span data-ttu-id="df557-111">podczas Tablica sygnatur pól.</span><span class="sxs-lookup"><span data-stu-id="df557-111">[in] The array of field signatures.</span></span>  
  
 `addrKind`  
 <span data-ttu-id="df557-112">podczas Typ adresu.</span><span class="sxs-lookup"><span data-stu-id="df557-112">[in] The address type.</span></span>  
  
 `addr1`  
 <span data-ttu-id="df557-113">podczas Pierwszy adres dla specyfikacji pola.</span><span class="sxs-lookup"><span data-stu-id="df557-113">[in] The first address for the field specification.</span></span>  
  
 `addr2`  
 <span data-ttu-id="df557-114">podczas Drugi adres dla specyfikacji pola.</span><span class="sxs-lookup"><span data-stu-id="df557-114">[in] The second address for the field specification.</span></span>  
  
 `addr3`  
 <span data-ttu-id="df557-115">podczas Trzeci adres dla specyfikacji pola.</span><span class="sxs-lookup"><span data-stu-id="df557-115">[in] The third address for the field specification.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="df557-116">Wartość zwrócona</span><span class="sxs-lookup"><span data-stu-id="df557-116">Return Value</span></span>  
 <span data-ttu-id="df557-117">S_OK, jeśli metoda się powiedzie; w przeciwnym razie E_FAIL lub inny kod błędu.</span><span class="sxs-lookup"><span data-stu-id="df557-117">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="df557-118">Wymagania</span><span class="sxs-lookup"><span data-stu-id="df557-118">Requirements</span></span>  
 <span data-ttu-id="df557-119">**Nagłówek:** CorSym. idl, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="df557-119">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="df557-120">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="df557-120">See also</span></span>

- [<span data-ttu-id="df557-121">ISymUnmanagedWriter, interfejs</span><span class="sxs-lookup"><span data-stu-id="df557-121">ISymUnmanagedWriter Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-interface.md)
