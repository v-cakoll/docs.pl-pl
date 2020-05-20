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
ms.openlocfilehash: d05d4451e8fb75829b22e0a1b9c9afcb0607eb8b
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/19/2020
ms.locfileid: "83610174"
---
# <a name="isymunmanagedvariable-interface"></a><span data-ttu-id="c71dd-102">ISymUnmanagedVariable — Interfejs</span><span class="sxs-lookup"><span data-stu-id="c71dd-102">ISymUnmanagedVariable Interface</span></span>
<span data-ttu-id="c71dd-103">Reprezentuje zmienną, taką jak parametr, zmienna lokalna lub pole.</span><span class="sxs-lookup"><span data-stu-id="c71dd-103">Represents a variable, such as a parameter, a local variable, or a field.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="c71dd-104">Metody</span><span class="sxs-lookup"><span data-stu-id="c71dd-104">Methods</span></span>  
  
|<span data-ttu-id="c71dd-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="c71dd-105">Method</span></span>|<span data-ttu-id="c71dd-106">Opis</span><span class="sxs-lookup"><span data-stu-id="c71dd-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="c71dd-107">GetAddressField1, metoda</span><span class="sxs-lookup"><span data-stu-id="c71dd-107">GetAddressField1 Method</span></span>](isymunmanagedvariable-getaddressfield1-method.md)|<span data-ttu-id="c71dd-108">Pobiera pierwsze pole adresu dla tej zmiennej.</span><span class="sxs-lookup"><span data-stu-id="c71dd-108">Gets the first address field for this variable.</span></span> <span data-ttu-id="c71dd-109">Jego znaczenie zależy od rodzaju adresu.</span><span class="sxs-lookup"><span data-stu-id="c71dd-109">Its meaning depends on the kind of address.</span></span>|  
|[<span data-ttu-id="c71dd-110">GetAddressField2, metoda</span><span class="sxs-lookup"><span data-stu-id="c71dd-110">GetAddressField2 Method</span></span>](isymunmanagedvariable-getaddressfield2-method.md)|<span data-ttu-id="c71dd-111">Pobiera drugie pole adresu dla tej zmiennej.</span><span class="sxs-lookup"><span data-stu-id="c71dd-111">Gets the second address field for this variable.</span></span> <span data-ttu-id="c71dd-112">Jego znaczenie zależy od rodzaju adresu.</span><span class="sxs-lookup"><span data-stu-id="c71dd-112">Its meaning depends on the kind of address.</span></span>|  
|[<span data-ttu-id="c71dd-113">GetAddressField3, metoda</span><span class="sxs-lookup"><span data-stu-id="c71dd-113">GetAddressField3 Method</span></span>](isymunmanagedvariable-getaddressfield3-method.md)|<span data-ttu-id="c71dd-114">Pobiera trzecie pole adresu dla tej zmiennej.</span><span class="sxs-lookup"><span data-stu-id="c71dd-114">Gets the third address field for this variable.</span></span> <span data-ttu-id="c71dd-115">Jego znaczenie zależy od rodzaju adresu.</span><span class="sxs-lookup"><span data-stu-id="c71dd-115">Its meaning depends on the kind of address.</span></span>|  
|[<span data-ttu-id="c71dd-116">GetAddressKind, metoda</span><span class="sxs-lookup"><span data-stu-id="c71dd-116">GetAddressKind Method</span></span>](isymunmanagedvariable-getaddresskind-method.md)|<span data-ttu-id="c71dd-117">Pobiera rodzaj adresu tej zmiennej.</span><span class="sxs-lookup"><span data-stu-id="c71dd-117">Gets the kind of address of this variable.</span></span>|  
|[<span data-ttu-id="c71dd-118">GetAttributes, metoda</span><span class="sxs-lookup"><span data-stu-id="c71dd-118">GetAttributes Method</span></span>](isymunmanagedvariable-getattributes-method.md)|<span data-ttu-id="c71dd-119">Pobiera flagi atrybutu dla tej zmiennej.</span><span class="sxs-lookup"><span data-stu-id="c71dd-119">Gets the attribute flags for this variable.</span></span>|  
|[<span data-ttu-id="c71dd-120">GetEndOffset, metoda</span><span class="sxs-lookup"><span data-stu-id="c71dd-120">GetEndOffset Method</span></span>](isymunmanagedvariable-getendoffset-method.md)|<span data-ttu-id="c71dd-121">Pobiera przesunięcie końca tej zmiennej w elemencie nadrzędnym.</span><span class="sxs-lookup"><span data-stu-id="c71dd-121">Gets the end offset of this variable within its parent.</span></span>|  
|[<span data-ttu-id="c71dd-122">GetName — Metoda</span><span class="sxs-lookup"><span data-stu-id="c71dd-122">GetName Method</span></span>](isymunmanagedvariable-getname-method.md)|<span data-ttu-id="c71dd-123">Pobiera nazwę tej zmiennej.</span><span class="sxs-lookup"><span data-stu-id="c71dd-123">Gets the name of this variable.</span></span>|  
|[<span data-ttu-id="c71dd-124">GetSignature, metoda</span><span class="sxs-lookup"><span data-stu-id="c71dd-124">GetSignature Method</span></span>](isymunmanagedvariable-getsignature-method.md)|<span data-ttu-id="c71dd-125">Pobiera sygnaturę tej zmiennej.</span><span class="sxs-lookup"><span data-stu-id="c71dd-125">Gets the signature of this variable.</span></span>|  
|[<span data-ttu-id="c71dd-126">GetStartOffset, metoda</span><span class="sxs-lookup"><span data-stu-id="c71dd-126">GetStartOffset Method</span></span>](isymunmanagedvariable-getstartoffset-method.md)|<span data-ttu-id="c71dd-127">Pobiera przesunięcie początku tej zmiennej w elemencie nadrzędnym.</span><span class="sxs-lookup"><span data-stu-id="c71dd-127">Gets the start offset of this variable within its parent.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="c71dd-128">Wymagania</span><span class="sxs-lookup"><span data-stu-id="c71dd-128">Requirements</span></span>  
 <span data-ttu-id="c71dd-129">**Nagłówek:** CorSym. idl, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="c71dd-129">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c71dd-130">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="c71dd-130">See also</span></span>

- [<span data-ttu-id="c71dd-131">Interfejsy magazynu symboli diagnostycznych</span><span class="sxs-lookup"><span data-stu-id="c71dd-131">Diagnostics Symbol Store Interfaces</span></span>](diagnostics-symbol-store-interfaces.md)
