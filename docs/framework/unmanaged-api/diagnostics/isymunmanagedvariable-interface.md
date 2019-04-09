---
title: ISymUnmanagedVariable — Interfejs
ms.date: 03/30/2017
api_name:
- ISymUnmanagedVariable
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedVariable
helpviewer_keywords:
- ISymUnmanagedVariable interface [.NET Framework debugging]
ms.assetid: 704c69ba-77bc-40d7-8c0c-400061686321
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 712eca7f3f9fec9c81e638802f5a664ec6469d53
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59164349"
---
# <a name="isymunmanagedvariable-interface"></a><span data-ttu-id="ec66e-102">ISymUnmanagedVariable — Interfejs</span><span class="sxs-lookup"><span data-stu-id="ec66e-102">ISymUnmanagedVariable Interface</span></span>
<span data-ttu-id="ec66e-103">Reprezentuje zmienną, takie jak parametr, zmienna lokalna lub pola.</span><span class="sxs-lookup"><span data-stu-id="ec66e-103">Represents a variable, such as a parameter, a local variable, or a field.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="ec66e-104">Metody</span><span class="sxs-lookup"><span data-stu-id="ec66e-104">Methods</span></span>  
  
|<span data-ttu-id="ec66e-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="ec66e-105">Method</span></span>|<span data-ttu-id="ec66e-106">Opis</span><span class="sxs-lookup"><span data-stu-id="ec66e-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="ec66e-107">GetAddressField1, metoda</span><span class="sxs-lookup"><span data-stu-id="ec66e-107">GetAddressField1 Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedvariable-getaddressfield1-method.md)|<span data-ttu-id="ec66e-108">Pobiera pierwsze pole Adres dla tej zmiennej.</span><span class="sxs-lookup"><span data-stu-id="ec66e-108">Gets the first address field for this variable.</span></span> <span data-ttu-id="ec66e-109">Znaczenia, zależy od rodzaju adresu.</span><span class="sxs-lookup"><span data-stu-id="ec66e-109">Its meaning depends on the kind of address.</span></span>|  
|[<span data-ttu-id="ec66e-110">GetAddressField2, metoda</span><span class="sxs-lookup"><span data-stu-id="ec66e-110">GetAddressField2 Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedvariable-getaddressfield2-method.md)|<span data-ttu-id="ec66e-111">Pobiera drugie pole Adres dla tej zmiennej.</span><span class="sxs-lookup"><span data-stu-id="ec66e-111">Gets the second address field for this variable.</span></span> <span data-ttu-id="ec66e-112">Znaczenia, zależy od rodzaju adresu.</span><span class="sxs-lookup"><span data-stu-id="ec66e-112">Its meaning depends on the kind of address.</span></span>|  
|[<span data-ttu-id="ec66e-113">GetAddressField3, metoda</span><span class="sxs-lookup"><span data-stu-id="ec66e-113">GetAddressField3 Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedvariable-getaddressfield3-method.md)|<span data-ttu-id="ec66e-114">Pobiera trzecim polu adresów dla tej zmiennej.</span><span class="sxs-lookup"><span data-stu-id="ec66e-114">Gets the third address field for this variable.</span></span> <span data-ttu-id="ec66e-115">Znaczenia, zależy od rodzaju adresu.</span><span class="sxs-lookup"><span data-stu-id="ec66e-115">Its meaning depends on the kind of address.</span></span>|  
|[<span data-ttu-id="ec66e-116">GetAddressKind, metoda</span><span class="sxs-lookup"><span data-stu-id="ec66e-116">GetAddressKind Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedvariable-getaddresskind-method.md)|<span data-ttu-id="ec66e-117">Pobiera rodzaj adres tej zmiennej.</span><span class="sxs-lookup"><span data-stu-id="ec66e-117">Gets the kind of address of this variable.</span></span>|  
|[<span data-ttu-id="ec66e-118">GetAttributes, metoda</span><span class="sxs-lookup"><span data-stu-id="ec66e-118">GetAttributes Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedvariable-getattributes-method.md)|<span data-ttu-id="ec66e-119">Pobiera flagi atrybutów dla tej zmiennej.</span><span class="sxs-lookup"><span data-stu-id="ec66e-119">Gets the attribute flags for this variable.</span></span>|  
|[<span data-ttu-id="ec66e-120">GetEndOffset, metoda</span><span class="sxs-lookup"><span data-stu-id="ec66e-120">GetEndOffset Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedvariable-getendoffset-method.md)|<span data-ttu-id="ec66e-121">Pobiera końcowy przesunięcie tej zmiennej w ramach jego elementu nadrzędnego.</span><span class="sxs-lookup"><span data-stu-id="ec66e-121">Gets the end offset of this variable within its parent.</span></span>|  
|[<span data-ttu-id="ec66e-122">GetName, metoda</span><span class="sxs-lookup"><span data-stu-id="ec66e-122">GetName Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedvariable-getname-method.md)|<span data-ttu-id="ec66e-123">Pobiera nazwę tej zmiennej.</span><span class="sxs-lookup"><span data-stu-id="ec66e-123">Gets the name of this variable.</span></span>|  
|[<span data-ttu-id="ec66e-124">GetSignature, metoda</span><span class="sxs-lookup"><span data-stu-id="ec66e-124">GetSignature Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedvariable-getsignature-method.md)|<span data-ttu-id="ec66e-125">Pobiera podpis tej zmiennej.</span><span class="sxs-lookup"><span data-stu-id="ec66e-125">Gets the signature of this variable.</span></span>|  
|[<span data-ttu-id="ec66e-126">GetStartOffset, metoda</span><span class="sxs-lookup"><span data-stu-id="ec66e-126">GetStartOffset Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedvariable-getstartoffset-method.md)|<span data-ttu-id="ec66e-127">Pobiera Przesunięcie początku tej zmiennej w ramach jego elementu nadrzędnego.</span><span class="sxs-lookup"><span data-stu-id="ec66e-127">Gets the start offset of this variable within its parent.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="ec66e-128">Wymagania</span><span class="sxs-lookup"><span data-stu-id="ec66e-128">Requirements</span></span>  
 <span data-ttu-id="ec66e-129">**Nagłówek:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="ec66e-129">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ec66e-130">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="ec66e-130">See also</span></span>

- [<span data-ttu-id="ec66e-131">Interfejsy magazynu symboli diagnostycznych</span><span class="sxs-lookup"><span data-stu-id="ec66e-131">Diagnostics Symbol Store Interfaces</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/diagnostics-symbol-store-interfaces.md)
