---
title: IMetaDataImport::EnumUnresolvedMethods — Metoda
ms.date: 03/30/2017
api_name:
- IMetaDataImport.EnumUnresolvedMethods
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::EnumUnresolvedMethods
helpviewer_keywords:
- EnumUnresolvedMethods method [.NET Framework metadata]
- IMetaDataImport::EnumUnresolvedMethods method [.NET Framework metadata]
ms.assetid: eb3187d7-74cf-44b1-aeeb-7a8d2b60e3b7
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: cfd53309b2b5e96e28e9e063a8adfda430864115
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="imetadataimportenumunresolvedmethods-method"></a><span data-ttu-id="48b9e-102">IMetaDataImport::EnumUnresolvedMethods — Metoda</span><span class="sxs-lookup"><span data-stu-id="48b9e-102">IMetaDataImport::EnumUnresolvedMethods Method</span></span>
<span data-ttu-id="48b9e-103">Wylicza tokenów MemberDef reprezentujący nierozwiązane metod w bieżącym zakresie metadanych.</span><span class="sxs-lookup"><span data-stu-id="48b9e-103">Enumerates MemberDef tokens representing the unresolved methods in the current metadata scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="48b9e-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="48b9e-104">Syntax</span></span>  
  
```  
HRESULT EnumUnresolvedMethods (  
   [in, out] HCORENUM    *phEnum,  
   [out]     mdToken     rMethods[],  
   [in]      ULONG       cMax,  
   [out]     ULONG       *pcTokens  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="48b9e-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="48b9e-105">Parameters</span></span>  
 `phEnum`  
 <span data-ttu-id="48b9e-106">[w, out] Wskaźnik do modułu wyliczającego.</span><span class="sxs-lookup"><span data-stu-id="48b9e-106">[in, out] A pointer to the enumerator.</span></span> <span data-ttu-id="48b9e-107">Musi to być wartość NULL dla pierwsze wywołanie tej metody.</span><span class="sxs-lookup"><span data-stu-id="48b9e-107">This must be NULL for the first call of this method.</span></span>  
  
 `rMethods`  
 <span data-ttu-id="48b9e-108">[out] Tablica używany do przechowywania tokenów MemberDef.</span><span class="sxs-lookup"><span data-stu-id="48b9e-108">[out] The array used to store the MemberDef tokens.</span></span>  
  
 `cMax`  
 <span data-ttu-id="48b9e-109">[in] Maksymalny rozmiar `rMethods` tablicy.</span><span class="sxs-lookup"><span data-stu-id="48b9e-109">[in] The maximum size of the `rMethods` array.</span></span>  
  
 `pcTokens`  
 <span data-ttu-id="48b9e-110">[out] Liczba tokenów MemberDef zwracane w `rMethods`.</span><span class="sxs-lookup"><span data-stu-id="48b9e-110">[out] The number of MemberDef tokens returned in `rMethods`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="48b9e-111">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="48b9e-111">Return Value</span></span>  
  
|<span data-ttu-id="48b9e-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="48b9e-112">HRESULT</span></span>|<span data-ttu-id="48b9e-113">Opis</span><span class="sxs-lookup"><span data-stu-id="48b9e-113">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="48b9e-114">`EnumUnresolvedMethods` zwrócona pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="48b9e-114">`EnumUnresolvedMethods` returned successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="48b9e-115">Nie ma żadnych tokenów do wyliczenia.</span><span class="sxs-lookup"><span data-stu-id="48b9e-115">There are no tokens to enumerate.</span></span> <span data-ttu-id="48b9e-116">W takim przypadku `pcTokens` wynosi zero.</span><span class="sxs-lookup"><span data-stu-id="48b9e-116">In that case, `pcTokens` is zero.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="48b9e-117">Uwagi</span><span class="sxs-lookup"><span data-stu-id="48b9e-117">Remarks</span></span>  
 <span data-ttu-id="48b9e-118">Nierozpoznane metody to taki, który został zadeklarowany, ale nie jest zaimplementowana.</span><span class="sxs-lookup"><span data-stu-id="48b9e-118">An unresolved method is one that has been declared but not implemented.</span></span> <span data-ttu-id="48b9e-119">Jeśli metoda jest oznaczona jako metoda znajduje się w wyliczeniu `miForwardRef` i `mdPinvokeImpl` lub `miRuntime` jest ustawiony na zero.</span><span class="sxs-lookup"><span data-stu-id="48b9e-119">A method is included in the enumeration if the method is marked `miForwardRef` and either `mdPinvokeImpl` or `miRuntime` is set to zero.</span></span> <span data-ttu-id="48b9e-120">Innymi słowy, nierozpoznane metoda jest metodą klasy oznaczonej jako `miForwardRef` , ale które nie jest zaimplementowana w niezarządzanym kodzie (Osiągnięto za pomocą funkcji PInvoke) ani nie zaimplementowana wewnętrznie przez środowisko wykonawcze</span><span class="sxs-lookup"><span data-stu-id="48b9e-120">In other words, an unresolved method is a class method that is marked `miForwardRef` but which is not implemented in unmanaged code (reached via PInvoke) nor implemented internally by the runtime itself</span></span>  
  
 <span data-ttu-id="48b9e-121">Wyliczanie nie obejmuje wszystkie metody, które są zdefiniowane w zakresie modułu (globalne) lub interfejsy lub klasy abstrakcyjne.</span><span class="sxs-lookup"><span data-stu-id="48b9e-121">The enumeration excludes all methods that are defined either at module scope (globals) or in interfaces or abstract classes.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="48b9e-122">Wymagania</span><span class="sxs-lookup"><span data-stu-id="48b9e-122">Requirements</span></span>  
 <span data-ttu-id="48b9e-123">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="48b9e-123">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="48b9e-124">**Nagłówek:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="48b9e-124">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="48b9e-125">**Biblioteka:** uwzględnione jako zasób w MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="48b9e-125">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="48b9e-126">**Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="48b9e-126">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="48b9e-127">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="48b9e-127">See Also</span></span>  
 [<span data-ttu-id="48b9e-128">IMetaDataImport, interfejs</span><span class="sxs-lookup"><span data-stu-id="48b9e-128">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)  
 [<span data-ttu-id="48b9e-129">IMetaDataImport2, interfejs</span><span class="sxs-lookup"><span data-stu-id="48b9e-129">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
