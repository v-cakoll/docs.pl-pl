---
title: IMetaDataImport::EnumMembers — Metoda
ms.date: 03/30/2017
api_name:
- IMetaDataImport.EnumMembers
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::EnumMembers
helpviewer_keywords:
- IMetaDataImport::EnumMembers method [.NET Framework metadata]
- EnumMembers method [.NET Framework metadata]
ms.assetid: 3fb8e178-342b-4c89-9bcf-f7f834e6cb77
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 88b8f874400d68110fa5e8fb66ca910b8e7231e1
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54645967"
---
# <a name="imetadataimportenummembers-method"></a><span data-ttu-id="21cc5-102">IMetaDataImport::EnumMembers — Metoda</span><span class="sxs-lookup"><span data-stu-id="21cc5-102">IMetaDataImport::EnumMembers Method</span></span>
<span data-ttu-id="21cc5-103">Wylicza tokenów MemberDef reprezentujących elementy określonego typu.</span><span class="sxs-lookup"><span data-stu-id="21cc5-103">Enumerates MemberDef tokens representing members of the specified type.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="21cc5-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="21cc5-104">Syntax</span></span>  
  
```  
HRESULT EnumMembers (   
   [in, out]  HCORENUM    *phEnum,   
   [in]  mdTypeDef   cl,   
   [out] mdToken     rMembers[],   
   [in]  ULONG       cMax,   
   [out] ULONG       *pcTokens  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="21cc5-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="21cc5-105">Parameters</span></span>  
 `phEnum`  
 <span data-ttu-id="21cc5-106">[out w] Wskaźnik do modułu wyliczającego.</span><span class="sxs-lookup"><span data-stu-id="21cc5-106">[in, out] A pointer to the enumerator.</span></span>  
  
 `cl`  
 <span data-ttu-id="21cc5-107">[in] TypeDef token reprezentujący typ, której członkami są do wyliczenia.</span><span class="sxs-lookup"><span data-stu-id="21cc5-107">[in] A TypeDef token representing the type whose members are to be enumerated.</span></span>  
  
 `rMembers`  
 <span data-ttu-id="21cc5-108">[out] Tablica, używane do przechowywania tokenów MemberDef.</span><span class="sxs-lookup"><span data-stu-id="21cc5-108">[out] The array used to hold the MemberDef tokens.</span></span>  
  
 `cMax`  
 <span data-ttu-id="21cc5-109">[in] Maksymalny rozmiar `rMembers` tablicy.</span><span class="sxs-lookup"><span data-stu-id="21cc5-109">[in] The maximum size of the `rMembers` array.</span></span>  
  
 `pcTokens`  
 <span data-ttu-id="21cc5-110">[out] Rzeczywista liczba tokenów MemberDef zwracane w `rMembers`.</span><span class="sxs-lookup"><span data-stu-id="21cc5-110">[out] The actual number of MemberDef tokens returned in `rMembers`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="21cc5-111">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="21cc5-111">Return Value</span></span>  
  
|<span data-ttu-id="21cc5-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="21cc5-112">HRESULT</span></span>|<span data-ttu-id="21cc5-113">Opis</span><span class="sxs-lookup"><span data-stu-id="21cc5-113">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="21cc5-114">`EnumMembers` pomyślnie zwrócił.</span><span class="sxs-lookup"><span data-stu-id="21cc5-114">`EnumMembers` returned successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="21cc5-115">Nie ma żadnych tokeny MemberDef do wyliczenia.</span><span class="sxs-lookup"><span data-stu-id="21cc5-115">There are no MemberDef tokens to enumerate.</span></span> <span data-ttu-id="21cc5-116">W takim przypadku `pcTokens` wynosi zero.</span><span class="sxs-lookup"><span data-stu-id="21cc5-116">In that case, `pcTokens` is zero.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="21cc5-117">Uwagi</span><span class="sxs-lookup"><span data-stu-id="21cc5-117">Remarks</span></span>  
 <span data-ttu-id="21cc5-118">Podczas wyliczania kolekcji elementów członkowskich dla klasy `EnumMembers` zwraca tylko elementy członkowskie zdefiniowane bezpośrednio w klasie.</span><span class="sxs-lookup"><span data-stu-id="21cc5-118">When enumerating collections of members for a class, `EnumMembers` returns only members defined directly on the class.</span></span> <span data-ttu-id="21cc5-119">Nie zwraca żadnych elementów członkowskich, które klasa dziedziczy, nawet wtedy, gdy klasa udostępnia implementację dla tych dziedziczonych elementów członkowskich.</span><span class="sxs-lookup"><span data-stu-id="21cc5-119">It does not return any members that the class inherits, even if the class provides an implementation for those inherited members.</span></span> <span data-ttu-id="21cc5-120">Aby wyliczyć dziedziczone elementy członkowskie, obiekt wywołujący jawnie prowadzą użytkownika łańcuch dziedziczenia.</span><span class="sxs-lookup"><span data-stu-id="21cc5-120">To enumerate inherited members, the caller must explicitly walk the inheritance chain.</span></span> <span data-ttu-id="21cc5-121">Należy pamiętać, że zasady łańcuch dziedziczenia, mogą się różnić w zależności od języka i kompilatora, które są emitowane odpowiednich oryginalnych metadanych.</span><span class="sxs-lookup"><span data-stu-id="21cc5-121">Note that the rules for the inheritance chain may vary depending on the language or compiler that emitted the original metadata.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="21cc5-122">Wymagania</span><span class="sxs-lookup"><span data-stu-id="21cc5-122">Requirements</span></span>  
 <span data-ttu-id="21cc5-123">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="21cc5-123">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="21cc5-124">**Nagłówek:** COR.h</span><span class="sxs-lookup"><span data-stu-id="21cc5-124">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="21cc5-125">**Biblioteka:** Dołączony jako zasób w MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="21cc5-125">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="21cc5-126">**Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="21cc5-126">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="21cc5-127">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="21cc5-127">See also</span></span>
- [<span data-ttu-id="21cc5-128">IMetaDataImport, interfejs</span><span class="sxs-lookup"><span data-stu-id="21cc5-128">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [<span data-ttu-id="21cc5-129">IMetaDataImport2, interfejs</span><span class="sxs-lookup"><span data-stu-id="21cc5-129">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
