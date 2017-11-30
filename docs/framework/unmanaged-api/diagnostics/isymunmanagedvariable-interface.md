---
title: "ISymUnmanagedVariable — Interfejs"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ISymUnmanagedVariable
api_location: diasymreader.dll
api_type: COM
f1_keywords: ISymUnmanagedVariable
helpviewer_keywords: ISymUnmanagedVariable interface [.NET Framework debugging]
ms.assetid: 704c69ba-77bc-40d7-8c0c-400061686321
topic_type: apiref
caps.latest.revision: "6"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: c32d5b66c575a21b4d390cff560b71f93aa31927
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="isymunmanagedvariable-interface"></a><span data-ttu-id="59b88-102">ISymUnmanagedVariable — Interfejs</span><span class="sxs-lookup"><span data-stu-id="59b88-102">ISymUnmanagedVariable Interface</span></span>
<span data-ttu-id="59b88-103">Reprezentuje zmienną, np. parametr, lokalnej zmiennej lub pola.</span><span class="sxs-lookup"><span data-stu-id="59b88-103">Represents a variable, such as a parameter, a local variable, or a field.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="59b88-104">Metody</span><span class="sxs-lookup"><span data-stu-id="59b88-104">Methods</span></span>  
  
|<span data-ttu-id="59b88-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="59b88-105">Method</span></span>|<span data-ttu-id="59b88-106">Opis</span><span class="sxs-lookup"><span data-stu-id="59b88-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="59b88-107">GetAddressField1 — metoda</span><span class="sxs-lookup"><span data-stu-id="59b88-107">GetAddressField1 Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedvariable-getaddressfield1-method.md)|<span data-ttu-id="59b88-108">Pobiera pierwsze pole adresu dla tej zmiennej.</span><span class="sxs-lookup"><span data-stu-id="59b88-108">Gets the first address field for this variable.</span></span> <span data-ttu-id="59b88-109">Znaczenia zależy od rodzaju adres.</span><span class="sxs-lookup"><span data-stu-id="59b88-109">Its meaning depends on the kind of address.</span></span>|  
|[<span data-ttu-id="59b88-110">GetAddressField2 — metoda</span><span class="sxs-lookup"><span data-stu-id="59b88-110">GetAddressField2 Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedvariable-getaddressfield2-method.md)|<span data-ttu-id="59b88-111">Pobiera drugie pole adresu dla tej zmiennej.</span><span class="sxs-lookup"><span data-stu-id="59b88-111">Gets the second address field for this variable.</span></span> <span data-ttu-id="59b88-112">Znaczenia zależy od rodzaju adres.</span><span class="sxs-lookup"><span data-stu-id="59b88-112">Its meaning depends on the kind of address.</span></span>|  
|[<span data-ttu-id="59b88-113">GetAddressField3 — metoda</span><span class="sxs-lookup"><span data-stu-id="59b88-113">GetAddressField3 Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedvariable-getaddressfield3-method.md)|<span data-ttu-id="59b88-114">Pobiera trzecie pole adresu dla tej zmiennej.</span><span class="sxs-lookup"><span data-stu-id="59b88-114">Gets the third address field for this variable.</span></span> <span data-ttu-id="59b88-115">Znaczenia zależy od rodzaju adres.</span><span class="sxs-lookup"><span data-stu-id="59b88-115">Its meaning depends on the kind of address.</span></span>|  
|[<span data-ttu-id="59b88-116">GetAddressKind — metoda</span><span class="sxs-lookup"><span data-stu-id="59b88-116">GetAddressKind Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedvariable-getaddresskind-method.md)|<span data-ttu-id="59b88-117">Pobiera rodzaj adresu tej zmiennej.</span><span class="sxs-lookup"><span data-stu-id="59b88-117">Gets the kind of address of this variable.</span></span>|  
|[<span data-ttu-id="59b88-118">GetAttributes — metoda</span><span class="sxs-lookup"><span data-stu-id="59b88-118">GetAttributes Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedvariable-getattributes-method.md)|<span data-ttu-id="59b88-119">Pobiera atrybut Flagi dla tej zmiennej.</span><span class="sxs-lookup"><span data-stu-id="59b88-119">Gets the attribute flags for this variable.</span></span>|  
|[<span data-ttu-id="59b88-120">GetEndOffset — metoda</span><span class="sxs-lookup"><span data-stu-id="59b88-120">GetEndOffset Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedvariable-getendoffset-method.md)|<span data-ttu-id="59b88-121">Pobiera przesunięcia końcowego tej zmiennej w ramach jego elementu nadrzędnego.</span><span class="sxs-lookup"><span data-stu-id="59b88-121">Gets the end offset of this variable within its parent.</span></span>|  
|[<span data-ttu-id="59b88-122">GetName — metoda</span><span class="sxs-lookup"><span data-stu-id="59b88-122">GetName Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedvariable-getname-method.md)|<span data-ttu-id="59b88-123">Pobiera nazwę zmiennej.</span><span class="sxs-lookup"><span data-stu-id="59b88-123">Gets the name of this variable.</span></span>|  
|[<span data-ttu-id="59b88-124">GetSignature — metoda</span><span class="sxs-lookup"><span data-stu-id="59b88-124">GetSignature Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedvariable-getsignature-method.md)|<span data-ttu-id="59b88-125">Pobiera podpis tej zmiennej.</span><span class="sxs-lookup"><span data-stu-id="59b88-125">Gets the signature of this variable.</span></span>|  
|[<span data-ttu-id="59b88-126">GetStartOffset — metoda</span><span class="sxs-lookup"><span data-stu-id="59b88-126">GetStartOffset Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedvariable-getstartoffset-method.md)|<span data-ttu-id="59b88-127">Pobiera Przesunięcie początku tej zmiennej w ramach jego elementu nadrzędnego.</span><span class="sxs-lookup"><span data-stu-id="59b88-127">Gets the start offset of this variable within its parent.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="59b88-128">Wymagania</span><span class="sxs-lookup"><span data-stu-id="59b88-128">Requirements</span></span>  
 <span data-ttu-id="59b88-129">**Nagłówek:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="59b88-129">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="59b88-130">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="59b88-130">See Also</span></span>  
 [<span data-ttu-id="59b88-131">Interfejsy magazynu symboli diagnostycznych</span><span class="sxs-lookup"><span data-stu-id="59b88-131">Diagnostics Symbol Store Interfaces</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/diagnostics-symbol-store-interfaces.md)
