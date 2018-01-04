---
title: "IMetaDataEmit::DefineMethod — Metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMetaDataEmit.DefineMethod
api_location: mscoree.dll
api_type: COM
f1_keywords: IMetaDataEmit::DefineMethod
helpviewer_keywords:
- DefineMethod method [.NET Framework metadata]
- IMetaDataEmit::DefineMethod method [.NET Framework metadata]
ms.assetid: 3e2102c5-48b7-4c0e-b805-7e2b5e156e3d
topic_type: apiref
caps.latest.revision: "12"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 4fa136f5e6669e58ef709db5b53f538804cfcac2
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="imetadataemitdefinemethod-method"></a><span data-ttu-id="8a671-102">IMetaDataEmit::DefineMethod — Metoda</span><span class="sxs-lookup"><span data-stu-id="8a671-102">IMetaDataEmit::DefineMethod Method</span></span>
<span data-ttu-id="8a671-103">Tworzy definicję metody lub funkcji globalnej z określoną sygnaturą i zwraca token do tej definicji metody.</span><span class="sxs-lookup"><span data-stu-id="8a671-103">Creates a definition for a method or global function with the specified signature, and returns a token to that method definition.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8a671-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="8a671-104">Syntax</span></span>  
  
```  
HRESULT DefineMethod (      
    [in]  mdTypeDef         td,   
    [in]  LPCWSTR           szName,   
    [in]  DWORD             dwMethodFlags,   
    [in]  PCCOR_SIGNATURE   pvSigBlob,   
    [in]  ULONG             cbSigBlob,   
    [in]  ULONG             ulCodeRVA,   
    [in]  DWORD             dwImplFlags,   
    [out] mdMethodDef      *pmd  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="8a671-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="8a671-105">Parameters</span></span>  
 `td`  
 <span data-ttu-id="8a671-106">[in] `mdTypedef` Token nadrzędnej klasy lub interfejsu nadrzędnego metody.</span><span class="sxs-lookup"><span data-stu-id="8a671-106">[in] The `mdTypedef` token of the parent class or parent interface of the method.</span></span> <span data-ttu-id="8a671-107">Ustaw `td` do `mdTokenNil`, jeśli definiujesz funkcją globalną.</span><span class="sxs-lookup"><span data-stu-id="8a671-107">Set `td` to `mdTokenNil`, if you are defining a global function.</span></span>  
  
 `szName`  
 <span data-ttu-id="8a671-108">[in] Nazwa elementu członkowskiego w standardzie Unicode.</span><span class="sxs-lookup"><span data-stu-id="8a671-108">[in] The member name in Unicode.</span></span>  
  
 `dwMethodFlags`  
 <span data-ttu-id="8a671-109">[in] Wartość [CorMethodAttr](../../../../docs/framework/unmanaged-api/metadata/cormethodattr-enumeration.md) wyliczenia, który określa atrybuty metody lub funkcji globalnej.</span><span class="sxs-lookup"><span data-stu-id="8a671-109">[in] A value of the [CorMethodAttr](../../../../docs/framework/unmanaged-api/metadata/cormethodattr-enumeration.md) enumeration that specifies the attributes of the method or global function.</span></span>  
  
 `pvSigBlob`  
 <span data-ttu-id="8a671-110">[in] Podpis metody.</span><span class="sxs-lookup"><span data-stu-id="8a671-110">[in] The method signature.</span></span> <span data-ttu-id="8a671-111">Podpis jest trwały dostarczony.</span><span class="sxs-lookup"><span data-stu-id="8a671-111">The signature is persisted as supplied.</span></span> <span data-ttu-id="8a671-112">Aby określić dodatkowe informacje dla wszystkich parametrów, należy użyć [IMetaDataEmit::SetParamProps](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-setparamprops-method.md) metody.</span><span class="sxs-lookup"><span data-stu-id="8a671-112">If you need to specify additional information for any parameters, use the [IMetaDataEmit::SetParamProps](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-setparamprops-method.md) method.</span></span>  
  
 `cbSigBlob`  
 <span data-ttu-id="8a671-113">[in] Liczba bajtów w `pvSigBlob`.</span><span class="sxs-lookup"><span data-stu-id="8a671-113">[in] The count of bytes in `pvSigBlob`.</span></span>  
  
 `ulCodeRVA`  
 <span data-ttu-id="8a671-114">[in] Adres kodu.</span><span class="sxs-lookup"><span data-stu-id="8a671-114">[in] The address of the code.</span></span>  
  
 `dwImplFlags`  
 <span data-ttu-id="8a671-115">[in] Wartość [CorMethodImpl](../../../../docs/framework/unmanaged-api/metadata/cormethodimpl-enumeration.md) wyliczenie określający funkcji w implementacji metody.</span><span class="sxs-lookup"><span data-stu-id="8a671-115">[in] A value of the [CorMethodImpl](../../../../docs/framework/unmanaged-api/metadata/cormethodimpl-enumeration.md) enumeration that specifies the implementation features of the method.</span></span>  
  
 `pmd`  
 <span data-ttu-id="8a671-116">[out] Token elementu członkowskiego.</span><span class="sxs-lookup"><span data-stu-id="8a671-116">[out] The member token.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="8a671-117">Uwagi</span><span class="sxs-lookup"><span data-stu-id="8a671-117">Remarks</span></span>  
 <span data-ttu-id="8a671-118">Gwarantuje metadanych interfejsu API utrwalić metod w tej samej kolejności jak wywołującego emituje je dla danego otaczającej klasy lub interfejsu, która została określona w `td` parametru.</span><span class="sxs-lookup"><span data-stu-id="8a671-118">The metadata API guarantees to persist methods in the same order as the caller emits them for a given enclosing class or interface, which is specified in the `td` parameter.</span></span>  
  
 <span data-ttu-id="8a671-119">Dodatkowe informacje na temat stosowania `DefineMethod` i poniżej podano ustawienia określonego parametru.</span><span class="sxs-lookup"><span data-stu-id="8a671-119">Additional information regarding the use of `DefineMethod` and particular parameter settings is given below.</span></span>  
  
## <a name="slots-in-the-v-table"></a><span data-ttu-id="8a671-120">Gniazda w tabeli V</span><span class="sxs-lookup"><span data-stu-id="8a671-120">Slots in the V-table</span></span>  
 <span data-ttu-id="8a671-121">Środowisko uruchomieniowe używa definicjami metod, aby skonfigurować miejsc v-table.</span><span class="sxs-lookup"><span data-stu-id="8a671-121">The runtime uses method definitions to set up v-table slots.</span></span> <span data-ttu-id="8a671-122">W przypadku, gdy co najmniej jednego gniazda muszą być zostało pominięte, na przykład aby zachować parzystości z układem interfejsu COM fikcyjny — metoda zdefiniowano do podjęcia miejsca lub miejsc, w tabeli v; Ustaw `dwMethodFlags` do `mdRTSpecialName` wartość [CorMethodAttr](../../../../docs/framework/unmanaged-api/metadata/cormethodattr-enumeration.md) wyliczenie i określ nazwę jako:</span><span class="sxs-lookup"><span data-stu-id="8a671-122">In the case where one or more slots need to be skipped, such as to preserve parity with a COM interface layout, a dummy method is defined to take up the slot or slots in the v-table; set the `dwMethodFlags` to the `mdRTSpecialName` value of the [CorMethodAttr](../../../../docs/framework/unmanaged-api/metadata/cormethodattr-enumeration.md) enumeration and specify the name as:</span></span>  
  
 <span data-ttu-id="8a671-123">_VtblGap\<*SequenceNumber*>\<\_*CountOfSlots*></span><span class="sxs-lookup"><span data-stu-id="8a671-123">_VtblGap\<*SequenceNumber*>\<\_*CountOfSlots*></span></span>  
  
 <span data-ttu-id="8a671-124">gdzie *SequenceNumber* to numer sekwencji metody i *CountOfSlots* jest numer gniazda, aby pominąć tabeli v.</span><span class="sxs-lookup"><span data-stu-id="8a671-124">where *SequenceNumber* is the sequence number of the method and *CountOfSlots* is the number of slots to skip in the v-table.</span></span> <span data-ttu-id="8a671-125">Jeśli *CountOfSlots* jest pominięty, przyjmowana jest wartość 1.</span><span class="sxs-lookup"><span data-stu-id="8a671-125">If *CountOfSlots* is omitted, 1 is assumed.</span></span> <span data-ttu-id="8a671-126">Te metody fikcyjny nie są z kodu zarządzanego lub niezarządzanego i wszelkie próby połączeń telefonicznych z nimi, z kodu zarządzane lub niezarządzane, generuje wyjątek.</span><span class="sxs-lookup"><span data-stu-id="8a671-126">These dummy methods are not callable from either managed or unmanaged code and any attempt to call them, from either managed or unmanaged code, generates an exception.</span></span> <span data-ttu-id="8a671-127">Ich jedynym celem jest miejsce w tabeli v generujący środowiska uruchomieniowego integracji COM.</span><span class="sxs-lookup"><span data-stu-id="8a671-127">Their only purpose is to take up space in the v-table that the runtime generates for COM integration.</span></span>  
  
## <a name="duplicate-methods"></a><span data-ttu-id="8a671-128">Zduplikowana metody</span><span class="sxs-lookup"><span data-stu-id="8a671-128">Duplicate Methods</span></span>  
 <span data-ttu-id="8a671-129">Nie powinna definiować metody zduplikowane.</span><span class="sxs-lookup"><span data-stu-id="8a671-129">You should not define duplicate methods.</span></span> <span data-ttu-id="8a671-130">Oznacza to, że nie należy wywołania `DefineMethod` z zestawem zduplikowanych wartości w `td`, `wzName`, i `pvSig` parametrów.</span><span class="sxs-lookup"><span data-stu-id="8a671-130">That is, you should not call `DefineMethod` with a duplicate set of values in the `td`, `wzName`, and `pvSig` parameters.</span></span> <span data-ttu-id="8a671-131">(Te trzy parametry razem jednoznacznie określić metodę.).</span><span class="sxs-lookup"><span data-stu-id="8a671-131">(These three parameters together uniquely define the method.).</span></span> <span data-ttu-id="8a671-132">Jednak można użyć zduplikowanych triple pod warunkiem, że w przypadku jednego z definicjami metod, można ustawić `mdPrivateScope` bitu w `dwMethodFlags` parametru.</span><span class="sxs-lookup"><span data-stu-id="8a671-132">However, you can use a duplicate triple provided that, for one of the method definitions, you set the `mdPrivateScope` bit in the `dwMethodFlags` parameter.</span></span> <span data-ttu-id="8a671-133">( `mdPrivateScope` Bit oznacza, że kompilator będzie Emituj odwołania do tej definicji — metoda.)</span><span class="sxs-lookup"><span data-stu-id="8a671-133">(The `mdPrivateScope` bit means that the compiler will not emit a reference to this method definition.)</span></span>  
  
## <a name="method-implementation-information"></a><span data-ttu-id="8a671-134">Informacje dotyczące implementacji metody</span><span class="sxs-lookup"><span data-stu-id="8a671-134">Method Implementation Information</span></span>  
 <span data-ttu-id="8a671-135">Informacje o implementacji metody często nie jest znany w czasie zadeklarowano metody.</span><span class="sxs-lookup"><span data-stu-id="8a671-135">Information about the method implementation is often not known at the time the method is declared.</span></span> <span data-ttu-id="8a671-136">W związku z tym nie trzeba przekazać wartości w `ulCodeRVA` i `dwImplFlags` parametrów podczas wywoływania metody `DefineMethod`.</span><span class="sxs-lookup"><span data-stu-id="8a671-136">Therefore, you do not need to pass values in the `ulCodeRVA` and `dwImplFlags` parameters when calling `DefineMethod`.</span></span> <span data-ttu-id="8a671-137">Wartości, które mogą być dostarczane później za pomocą [IMetaDataEmit::SetMethodImplFlags](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-setmethodimplflags-method.md) lub [IMetaDataEmit::SetRVA](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-setrva-method.md), gdzie to właściwe.</span><span class="sxs-lookup"><span data-stu-id="8a671-137">The values can be supplied later through [IMetaDataEmit::SetMethodImplFlags](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-setmethodimplflags-method.md) or [IMetaDataEmit::SetRVA](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-setrva-method.md), as appropriate.</span></span>  
  
 <span data-ttu-id="8a671-138">W niektórych sytuacjach, takich jak wywołania platformy (PInvoke) lub COM interop scenariuszy, treści metody nie zostanie podany, i `ulCodeRVA` powinna być równa zero.</span><span class="sxs-lookup"><span data-stu-id="8a671-138">In some situations, such as platform invocation (PInvoke) or COM interop scenarios, the method body will not be supplied, and `ulCodeRVA` should be set to zero.</span></span> <span data-ttu-id="8a671-139">W takich przypadkach metoda powinna nie oznaczone jako abstract, ponieważ środowisko uruchomieniowe zlokalizuje implementacji.</span><span class="sxs-lookup"><span data-stu-id="8a671-139">In these situations, the method should not be tagged as abstract, because the runtime will locate the implementation.</span></span>  
  
## <a name="defining-a-method-for-pinvoke"></a><span data-ttu-id="8a671-140">Definiowanie metody dla funkcji PInvoke</span><span class="sxs-lookup"><span data-stu-id="8a671-140">Defining a Method for PInvoke</span></span>  
 <span data-ttu-id="8a671-141">Dla każdej funkcji niezarządzanej ma być wywoływana za pomocą funkcji PInvoke musi definiować zarządzanego metodę, która reprezentuje funkcję docelowy niezarządzanych.</span><span class="sxs-lookup"><span data-stu-id="8a671-141">For each unmanaged function to be called through PInvoke, you must define a managed method that represents the target unmanaged function.</span></span> <span data-ttu-id="8a671-142">Aby określić metodę zarządzanych, użyj `DefineMethod` niektóre z parametrów niektórych wartości w zależności od sposobu, w którym jest używana PInvoke:</span><span class="sxs-lookup"><span data-stu-id="8a671-142">To define the managed method, use `DefineMethod` with some of the parameters set to certain values, depending on the way in which PInvoke is used:</span></span>  
  
-   <span data-ttu-id="8a671-143">Wartość true, PInvoke — wymaga wywołania metody niezarządzane zewnętrznych znajduje się w bibliotece DLL niezarządzane.</span><span class="sxs-lookup"><span data-stu-id="8a671-143">True PInvoke - involves invocation of an external unmanaged method that resides in an unmanaged DLL.</span></span>  
  
-   <span data-ttu-id="8a671-144">Lokalne PInvoke - obejmuje wywołanie metody niezarządzane natywnego osadzonym w bieżącym modułu zarządzanego.</span><span class="sxs-lookup"><span data-stu-id="8a671-144">Local PInvoke - involves invocation of a native unmanaged method that is embedded in the current managed module.</span></span>  
  
 <span data-ttu-id="8a671-145">Ustawienia parametru podano w poniższej tabeli.</span><span class="sxs-lookup"><span data-stu-id="8a671-145">The parameter settings are given in the following table.</span></span>  
  
|<span data-ttu-id="8a671-146">Parametr</span><span class="sxs-lookup"><span data-stu-id="8a671-146">Parameter</span></span>|<span data-ttu-id="8a671-147">Wartości true funkcji PInvoke</span><span class="sxs-lookup"><span data-stu-id="8a671-147">Values for true PInvoke</span></span>|<span data-ttu-id="8a671-148">Wartości dla lokalnych funkcji PInvoke</span><span class="sxs-lookup"><span data-stu-id="8a671-148">Values for local PInvoke</span></span>|  
|---------------|-----------------------------|------------------------------|  
|`dwMethodFlags`||<span data-ttu-id="8a671-149">Ustaw `mdStatic`; wyczyść `mdSynchronized` i `mdAbstract`.</span><span class="sxs-lookup"><span data-stu-id="8a671-149">Set `mdStatic`; clear `mdSynchronized` and `mdAbstract`.</span></span>|  
|`pvSigBlob`|<span data-ttu-id="8a671-150">Typy zarządzane wspólnego języka środowiska uruchomieniowego (języka wspólnego CLR) metoda podpisu z parametrami, które są prawidłowe.</span><span class="sxs-lookup"><span data-stu-id="8a671-150">A valid common language runtime (CLR) method signature with parameters that are valid managed types.</span></span>|<span data-ttu-id="8a671-151">Typy zarządzane prawidłowy podpis metody CLR z parametrami, które są prawidłowe.</span><span class="sxs-lookup"><span data-stu-id="8a671-151">A valid CLR method signature with parameters that are valid managed types.</span></span>|  
|`ulCodeRVA`||<span data-ttu-id="8a671-152">0</span><span class="sxs-lookup"><span data-stu-id="8a671-152">0</span></span>|  
|`dwImplFlags`|<span data-ttu-id="8a671-153">Ustaw `miCil` i `miManaged`.</span><span class="sxs-lookup"><span data-stu-id="8a671-153">Set `miCil` and `miManaged`.</span></span>|<span data-ttu-id="8a671-154">Ustaw `miNative` i `miUnmanaged`.</span><span class="sxs-lookup"><span data-stu-id="8a671-154">Set `miNative` and `miUnmanaged`.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="8a671-155">Wymagania</span><span class="sxs-lookup"><span data-stu-id="8a671-155">Requirements</span></span>  
 <span data-ttu-id="8a671-156">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8a671-156">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8a671-157">**Nagłówek:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="8a671-157">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="8a671-158">**Biblioteka:** używany jako zasób w MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="8a671-158">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="8a671-159">**Wersje programu .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8a671-159">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8a671-160">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="8a671-160">See Also</span></span>  
 [<span data-ttu-id="8a671-161">IMetaDataEmit, interfejs</span><span class="sxs-lookup"><span data-stu-id="8a671-161">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)  
 [<span data-ttu-id="8a671-162">IMetaDataEmit2, interfejs</span><span class="sxs-lookup"><span data-stu-id="8a671-162">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
