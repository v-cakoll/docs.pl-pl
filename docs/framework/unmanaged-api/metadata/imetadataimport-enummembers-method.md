---
title: "IMetaDataImport::EnumMembers — Metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
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
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: aa7dabad0e555fe965cba4e5cbc69c10c9826b8e
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="imetadataimportenummembers-method"></a><span data-ttu-id="9bc82-102">IMetaDataImport::EnumMembers — Metoda</span><span class="sxs-lookup"><span data-stu-id="9bc82-102">IMetaDataImport::EnumMembers Method</span></span>
<span data-ttu-id="9bc82-103">Wylicza tokenów MemberDef reprezentujący elementy członkowskie określonego typu.</span><span class="sxs-lookup"><span data-stu-id="9bc82-103">Enumerates MemberDef tokens representing members of the specified type.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9bc82-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="9bc82-104">Syntax</span></span>  
  
```  
HRESULT EnumMembers (   
   [in, out]  HCORENUM    *phEnum,   
   [in]  mdTypeDef   cl,   
   [out] mdToken     rMembers[],   
   [in]  ULONG       cMax,   
   [out] ULONG       *pcTokens  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="9bc82-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="9bc82-105">Parameters</span></span>  
 `phEnum`  
 <span data-ttu-id="9bc82-106">[w, out] Wskaźnik do modułu wyliczającego.</span><span class="sxs-lookup"><span data-stu-id="9bc82-106">[in, out] A pointer to the enumerator.</span></span>  
  
 `cl`  
 <span data-ttu-id="9bc82-107">[in] Element TypeDef token reprezentujący typ, której członkami są mają zostać wyliczone.</span><span class="sxs-lookup"><span data-stu-id="9bc82-107">[in] A TypeDef token representing the type whose members are to be enumerated.</span></span>  
  
 `rMembers`  
 <span data-ttu-id="9bc82-108">[out] Tablica używanym do przechowywania tokenów MemberDef.</span><span class="sxs-lookup"><span data-stu-id="9bc82-108">[out] The array used to hold the MemberDef tokens.</span></span>  
  
 `cMax`  
 <span data-ttu-id="9bc82-109">[in] Maksymalny rozmiar `rMembers` tablicy.</span><span class="sxs-lookup"><span data-stu-id="9bc82-109">[in] The maximum size of the `rMembers` array.</span></span>  
  
 `pcTokens`  
 <span data-ttu-id="9bc82-110">[out] Rzeczywista liczba tokenów MemberDef zwracane w `rMembers`.</span><span class="sxs-lookup"><span data-stu-id="9bc82-110">[out] The actual number of MemberDef tokens returned in `rMembers`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="9bc82-111">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="9bc82-111">Return Value</span></span>  
  
|<span data-ttu-id="9bc82-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="9bc82-112">HRESULT</span></span>|<span data-ttu-id="9bc82-113">Opis</span><span class="sxs-lookup"><span data-stu-id="9bc82-113">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="9bc82-114">`EnumMembers`zwrócona pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="9bc82-114">`EnumMembers` returned successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="9bc82-115">Nie ma żadnych tokenów MemberDef do wyliczenia.</span><span class="sxs-lookup"><span data-stu-id="9bc82-115">There are no MemberDef tokens to enumerate.</span></span> <span data-ttu-id="9bc82-116">W takim przypadku `pcTokens` wynosi zero.</span><span class="sxs-lookup"><span data-stu-id="9bc82-116">In that case, `pcTokens` is zero.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="9bc82-117">Uwagi</span><span class="sxs-lookup"><span data-stu-id="9bc82-117">Remarks</span></span>  
 <span data-ttu-id="9bc82-118">Podczas wyliczania kolekcji elementów członkowskich klasy, `EnumMembers` zwraca tylko elementy członkowskie zdefiniowane bezpośrednio dla klasy.</span><span class="sxs-lookup"><span data-stu-id="9bc82-118">When enumerating collections of members for a class, `EnumMembers` returns only members defined directly on the class.</span></span> <span data-ttu-id="9bc82-119">Nie zwraca żadnych elementów członkowskich, które dziedziczy klasa, nawet jeśli ta klasa dostarcza implementacji dla tych członków dziedziczonych.</span><span class="sxs-lookup"><span data-stu-id="9bc82-119">It does not return any members that the class inherits, even if the class provides an implementation for those inherited members.</span></span> <span data-ttu-id="9bc82-120">Wyliczyć dziedziczone elementy członkowskie, wywołujący musi jawnie Przeprowadź łańcuch dziedziczenia.</span><span class="sxs-lookup"><span data-stu-id="9bc82-120">To enumerate inherited members, the caller must explicitly walk the inheritance chain.</span></span> <span data-ttu-id="9bc82-121">Należy pamiętać, że zasady łańcuch dziedziczenia może się różnić w zależności od języka i kompilatora wysyłanego oryginalnych metadanych.</span><span class="sxs-lookup"><span data-stu-id="9bc82-121">Note that the rules for the inheritance chain may vary depending on the language or compiler that emitted the original metadata.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9bc82-122">Wymagania</span><span class="sxs-lookup"><span data-stu-id="9bc82-122">Requirements</span></span>  
 <span data-ttu-id="9bc82-123">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9bc82-123">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9bc82-124">**Nagłówek:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="9bc82-124">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="9bc82-125">**Biblioteka:** uwzględnione jako zasób w MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="9bc82-125">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="9bc82-126">**Wersje programu .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9bc82-126">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9bc82-127">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="9bc82-127">See Also</span></span>  
 [<span data-ttu-id="9bc82-128">IMetaDataImport, interfejs</span><span class="sxs-lookup"><span data-stu-id="9bc82-128">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)  
 [<span data-ttu-id="9bc82-129">IMetaDataImport2, interfejs</span><span class="sxs-lookup"><span data-stu-id="9bc82-129">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
