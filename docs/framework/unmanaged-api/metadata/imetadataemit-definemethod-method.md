---
title: IMetaDataEmit::DefineMethod — Metoda
ms.date: 03/30/2017
api_name:
- IMetaDataEmit.DefineMethod
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit::DefineMethod
helpviewer_keywords:
- DefineMethod method [.NET Framework metadata]
- IMetaDataEmit::DefineMethod method [.NET Framework metadata]
ms.assetid: 3e2102c5-48b7-4c0e-b805-7e2b5e156e3d
topic_type:
- apiref
ms.openlocfilehash: d4f3c95428d6f0f8807e284c5b54582428176511
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79177665"
---
# <a name="imetadataemitdefinemethod-method"></a><span data-ttu-id="cd553-102">IMetaDataEmit::DefineMethod — Metoda</span><span class="sxs-lookup"><span data-stu-id="cd553-102">IMetaDataEmit::DefineMethod Method</span></span>
<span data-ttu-id="cd553-103">Tworzy definicję metody lub funkcji globalnej z określonym podpisem i zwraca token do tej definicji metody.</span><span class="sxs-lookup"><span data-stu-id="cd553-103">Creates a definition for a method or global function with the specified signature, and returns a token to that method definition.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cd553-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="cd553-104">Syntax</span></span>  
  
```cpp  
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
  
## <a name="parameters"></a><span data-ttu-id="cd553-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="cd553-105">Parameters</span></span>  
 `td`  
 <span data-ttu-id="cd553-106">[w] Token `mdTypedef` klasy nadrzędnej lub nadrzędnego interfejsu metody.</span><span class="sxs-lookup"><span data-stu-id="cd553-106">[in] The `mdTypedef` token of the parent class or parent interface of the method.</span></span> <span data-ttu-id="cd553-107">Ustaw `td` `mdTokenNil`na , jeśli definiujesz funkcję globalną.</span><span class="sxs-lookup"><span data-stu-id="cd553-107">Set `td` to `mdTokenNil`, if you are defining a global function.</span></span>  
  
 `szName`  
 <span data-ttu-id="cd553-108">[w] Nazwa elementu członkowskiego w unicode.</span><span class="sxs-lookup"><span data-stu-id="cd553-108">[in] The member name in Unicode.</span></span>  
  
 `dwMethodFlags`  
 <span data-ttu-id="cd553-109">[w] Wartość wyliczenia [CorMethodAttr,](../../../../docs/framework/unmanaged-api/metadata/cormethodattr-enumeration.md) która określa atrybuty metody lub funkcji globalnej.</span><span class="sxs-lookup"><span data-stu-id="cd553-109">[in] A value of the [CorMethodAttr](../../../../docs/framework/unmanaged-api/metadata/cormethodattr-enumeration.md) enumeration that specifies the attributes of the method or global function.</span></span>  
  
 `pvSigBlob`  
 <span data-ttu-id="cd553-110">[w] Podpis metody.</span><span class="sxs-lookup"><span data-stu-id="cd553-110">[in] The method signature.</span></span> <span data-ttu-id="cd553-111">Podpis jest zachowywany zgodnie z podano.</span><span class="sxs-lookup"><span data-stu-id="cd553-111">The signature is persisted as supplied.</span></span> <span data-ttu-id="cd553-112">Jeśli chcesz określić dodatkowe informacje dla dowolnych parametrów, użyj [metody IMetaDataEmit::SetParamProps.](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-setparamprops-method.md)</span><span class="sxs-lookup"><span data-stu-id="cd553-112">If you need to specify additional information for any parameters, use the [IMetaDataEmit::SetParamProps](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-setparamprops-method.md) method.</span></span>  
  
 `cbSigBlob`  
 <span data-ttu-id="cd553-113">[w] Liczba bajtów `pvSigBlob`w pliku .</span><span class="sxs-lookup"><span data-stu-id="cd553-113">[in] The count of bytes in `pvSigBlob`.</span></span>  
  
 `ulCodeRVA`  
 <span data-ttu-id="cd553-114">[w] Adres kodu.</span><span class="sxs-lookup"><span data-stu-id="cd553-114">[in] The address of the code.</span></span>  
  
 `dwImplFlags`  
 <span data-ttu-id="cd553-115">[w] Wartość wyliczenia [CorMethodImpl,](../../../../docs/framework/unmanaged-api/metadata/cormethodimpl-enumeration.md) która określa funkcje implementacji metody.</span><span class="sxs-lookup"><span data-stu-id="cd553-115">[in] A value of the [CorMethodImpl](../../../../docs/framework/unmanaged-api/metadata/cormethodimpl-enumeration.md) enumeration that specifies the implementation features of the method.</span></span>  
  
 `pmd`  
 <span data-ttu-id="cd553-116">[na zewnątrz] Token elementu członkowskiego.</span><span class="sxs-lookup"><span data-stu-id="cd553-116">[out] The member token.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="cd553-117">Uwagi</span><span class="sxs-lookup"><span data-stu-id="cd553-117">Remarks</span></span>  
 <span data-ttu-id="cd553-118">Interfejs API metadanych gwarantuje, że metody utrwalania w tej samej kolejności, w jakiej `td` wywoływany jest, emituje je dla danej klasy lub interfejsu otaczającego, który jest określony w parametrze.</span><span class="sxs-lookup"><span data-stu-id="cd553-118">The metadata API guarantees to persist methods in the same order as the caller emits them for a given enclosing class or interface, which is specified in the `td` parameter.</span></span>  
  
 <span data-ttu-id="cd553-119">Dodatkowe informacje dotyczące `DefineMethod` korzystania z poszczególnych ustawień parametrów znajdują się poniżej.</span><span class="sxs-lookup"><span data-stu-id="cd553-119">Additional information regarding the use of `DefineMethod` and particular parameter settings is given below.</span></span>  
  
## <a name="slots-in-the-v-table"></a><span data-ttu-id="cd553-120">Szczeliny w tabeli V</span><span class="sxs-lookup"><span data-stu-id="cd553-120">Slots in the V-table</span></span>  
 <span data-ttu-id="cd553-121">Środowisko wykonawcze używa definicji metod do konfigurowania gniazd v-table.</span><span class="sxs-lookup"><span data-stu-id="cd553-121">The runtime uses method definitions to set up v-table slots.</span></span> <span data-ttu-id="cd553-122">W przypadku, gdy należy pominąć jedno lub więcej gniazd, na przykład w celu zachowania parytetu z układem interfejsu COM, metoda manekina jest definiowana w celu uwzględnienia gniazda lub gniazd w tabeli v; ustawić `dwMethodFlags` wartość `mdRTSpecialName` wyliczenia [CorMethodAttr](../../../../docs/framework/unmanaged-api/metadata/cormethodattr-enumeration.md) i określić nazwę jako:</span><span class="sxs-lookup"><span data-stu-id="cd553-122">In the case where one or more slots need to be skipped, such as to preserve parity with a COM interface layout, a dummy method is defined to take up the slot or slots in the v-table; set the `dwMethodFlags` to the `mdRTSpecialName` value of the [CorMethodAttr](../../../../docs/framework/unmanaged-api/metadata/cormethodattr-enumeration.md) enumeration and specify the name as:</span></span>  
  
 <span data-ttu-id="cd553-123">\<_VtblGap*SequenceNumber*>\<\_*CountOfSlots*></span><span class="sxs-lookup"><span data-stu-id="cd553-123">_VtblGap\<*SequenceNumber*>\<\_*CountOfSlots*></span></span>
  
 <span data-ttu-id="cd553-124">gdzie *SequenceNumber* jest numerem sekwencyjnym metody i *CountOfSlots* jest liczba gniazd do pominięcia w tabeli v.</span><span class="sxs-lookup"><span data-stu-id="cd553-124">where *SequenceNumber* is the sequence number of the method and *CountOfSlots* is the number of slots to skip in the v-table.</span></span> <span data-ttu-id="cd553-125">Jeśli *CountOfSlots zostanie pominięty,* zakłada się 1.</span><span class="sxs-lookup"><span data-stu-id="cd553-125">If *CountOfSlots* is omitted, 1 is assumed.</span></span> <span data-ttu-id="cd553-126">Te metody fikcyjne nie są wywoływane z kodu zarządzanego lub niezarządzanego i każda próba wywołania ich, z kodu zarządzanego lub niezarządzanego, generuje wyjątek.</span><span class="sxs-lookup"><span data-stu-id="cd553-126">These dummy methods are not callable from either managed or unmanaged code and any attempt to call them, from either managed or unmanaged code, generates an exception.</span></span> <span data-ttu-id="cd553-127">Ich jedynym celem jest zajmie miejsce w tabeli v, który generuje środowisko wykonawcze dla integracji com.</span><span class="sxs-lookup"><span data-stu-id="cd553-127">Their only purpose is to take up space in the v-table that the runtime generates for COM integration.</span></span>  
  
## <a name="duplicate-methods"></a><span data-ttu-id="cd553-128">Zduplikowane metody</span><span class="sxs-lookup"><span data-stu-id="cd553-128">Duplicate Methods</span></span>  
 <span data-ttu-id="cd553-129">Nie należy definiować zduplikowanych metod.</span><span class="sxs-lookup"><span data-stu-id="cd553-129">You should not define duplicate methods.</span></span> <span data-ttu-id="cd553-130">Oznacza to, że `DefineMethod` nie należy wywoływać z `td` `wzName`duplikatem zestawu wartości w , i `pvSig` parametrów.</span><span class="sxs-lookup"><span data-stu-id="cd553-130">That is, you should not call `DefineMethod` with a duplicate set of values in the `td`, `wzName`, and `pvSig` parameters.</span></span> <span data-ttu-id="cd553-131">(Te trzy parametry razem jednoznacznie definiują metodę.).</span><span class="sxs-lookup"><span data-stu-id="cd553-131">(These three parameters together uniquely define the method.).</span></span> <span data-ttu-id="cd553-132">Można jednak użyć zduplikowanej potrójnej, pod warunkiem, że `mdPrivateScope` dla `dwMethodFlags` jednej z definicji metody można ustawić bit w parametrze.</span><span class="sxs-lookup"><span data-stu-id="cd553-132">However, you can use a duplicate triple provided that, for one of the method definitions, you set the `mdPrivateScope` bit in the `dwMethodFlags` parameter.</span></span> <span data-ttu-id="cd553-133">(Bit `mdPrivateScope` oznacza, że kompilator nie będzie emitować odwołanie do tej definicji metody.)</span><span class="sxs-lookup"><span data-stu-id="cd553-133">(The `mdPrivateScope` bit means that the compiler will not emit a reference to this method definition.)</span></span>  
  
## <a name="method-implementation-information"></a><span data-ttu-id="cd553-134">Informacje o implementacji metody</span><span class="sxs-lookup"><span data-stu-id="cd553-134">Method Implementation Information</span></span>  
 <span data-ttu-id="cd553-135">Informacje o implementacji metody często nie jest znany w momencie zadeklarowania metody.</span><span class="sxs-lookup"><span data-stu-id="cd553-135">Information about the method implementation is often not known at the time the method is declared.</span></span> <span data-ttu-id="cd553-136">W związku z tym nie trzeba `ulCodeRVA` przekazywać wartości w i `dwImplFlags` parametry podczas wywoływania `DefineMethod`.</span><span class="sxs-lookup"><span data-stu-id="cd553-136">Therefore, you do not need to pass values in the `ulCodeRVA` and `dwImplFlags` parameters when calling `DefineMethod`.</span></span> <span data-ttu-id="cd553-137">Wartości mogą być dostarczane później za pośrednictwem [IMetaDataEmit::SetMethodImplFlags](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-setmethodimplflags-method.md) lub [IMetaDataEmit::SetRVA](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-setrva-method.md), odpowiednio.</span><span class="sxs-lookup"><span data-stu-id="cd553-137">The values can be supplied later through [IMetaDataEmit::SetMethodImplFlags](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-setmethodimplflags-method.md) or [IMetaDataEmit::SetRVA](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-setrva-method.md), as appropriate.</span></span>  
  
 <span data-ttu-id="cd553-138">W niektórych sytuacjach, takich jak wywołanie platformy (PInvoke) lub współdziałania COM `ulCodeRVA` scenariusze, treść metody nie zostaną dostarczone i powinny być ustawione na zero.</span><span class="sxs-lookup"><span data-stu-id="cd553-138">In some situations, such as platform invocation (PInvoke) or COM interop scenarios, the method body will not be supplied, and `ulCodeRVA` should be set to zero.</span></span> <span data-ttu-id="cd553-139">W takich sytuacjach metoda nie powinna być oznaczana jako abstrakcyjna, ponieważ środowisko wykonawcze zlokalizuje implementację.</span><span class="sxs-lookup"><span data-stu-id="cd553-139">In these situations, the method should not be tagged as abstract, because the runtime will locate the implementation.</span></span>  
  
## <a name="defining-a-method-for-pinvoke"></a><span data-ttu-id="cd553-140">Definiowanie metody pinvoke</span><span class="sxs-lookup"><span data-stu-id="cd553-140">Defining a Method for PInvoke</span></span>  
 <span data-ttu-id="cd553-141">Dla każdej funkcji niezarządzanej, która ma być wywoływana za pośrednictwem PInvoke, należy zdefiniować metodę zarządzaną, która reprezentuje docelową funkcję niezarządzaną.</span><span class="sxs-lookup"><span data-stu-id="cd553-141">For each unmanaged function to be called through PInvoke, you must define a managed method that represents the target unmanaged function.</span></span> <span data-ttu-id="cd553-142">Aby zdefiniować metodę `DefineMethod` zarządzaną, należy użyć z niektórymi parametrami ustawionymi na określone wartości, w zależności od sposobu, w jaki jest używany PInvoke:</span><span class="sxs-lookup"><span data-stu-id="cd553-142">To define the managed method, use `DefineMethod` with some of the parameters set to certain values, depending on the way in which PInvoke is used:</span></span>  
  
- <span data-ttu-id="cd553-143">True PInvoke - obejmuje wywołanie zewnętrznej metody niezarządzanej, która znajduje się w niezarządzanej biblioteki DLL.</span><span class="sxs-lookup"><span data-stu-id="cd553-143">True PInvoke - involves invocation of an external unmanaged method that resides in an unmanaged DLL.</span></span>  
  
- <span data-ttu-id="cd553-144">Local PInvoke - obejmuje wywołanie macierzystej metody niezarządzanej, która jest osadzona w bieżącym module zarządzanym.</span><span class="sxs-lookup"><span data-stu-id="cd553-144">Local PInvoke - involves invocation of a native unmanaged method that is embedded in the current managed module.</span></span>  
  
 <span data-ttu-id="cd553-145">Ustawienia parametrów podano w poniższej tabeli.</span><span class="sxs-lookup"><span data-stu-id="cd553-145">The parameter settings are given in the following table.</span></span>  
  
|<span data-ttu-id="cd553-146">Parametr</span><span class="sxs-lookup"><span data-stu-id="cd553-146">Parameter</span></span>|<span data-ttu-id="cd553-147">Wartości dla prawdziwego PInvoke</span><span class="sxs-lookup"><span data-stu-id="cd553-147">Values for true PInvoke</span></span>|<span data-ttu-id="cd553-148">Wartości dla lokalnego PInvoke</span><span class="sxs-lookup"><span data-stu-id="cd553-148">Values for local PInvoke</span></span>|  
|---------------|-----------------------------|------------------------------|  
|`dwMethodFlags`||<span data-ttu-id="cd553-149">Zestaw `mdStatic`; jasne `mdSynchronized` `mdAbstract`i .</span><span class="sxs-lookup"><span data-stu-id="cd553-149">Set `mdStatic`; clear `mdSynchronized` and `mdAbstract`.</span></span>|  
|`pvSigBlob`|<span data-ttu-id="cd553-150">Podpis metody prawidłowego wspólnego środowiska wykonawczego języka (CLR) z parametrami, które są prawidłowymi typami zarządzanymi.</span><span class="sxs-lookup"><span data-stu-id="cd553-150">A valid common language runtime (CLR) method signature with parameters that are valid managed types.</span></span>|<span data-ttu-id="cd553-151">Prawidłowy podpis metody CLR z parametrami, które są prawidłowymi typami zarządzanymi.</span><span class="sxs-lookup"><span data-stu-id="cd553-151">A valid CLR method signature with parameters that are valid managed types.</span></span>|  
|`ulCodeRVA`||<span data-ttu-id="cd553-152">0</span><span class="sxs-lookup"><span data-stu-id="cd553-152">0</span></span>|  
|`dwImplFlags`|<span data-ttu-id="cd553-153">Zestaw `miCil` `miManaged`i .</span><span class="sxs-lookup"><span data-stu-id="cd553-153">Set `miCil` and `miManaged`.</span></span>|<span data-ttu-id="cd553-154">Zestaw `miNative` `miUnmanaged`i .</span><span class="sxs-lookup"><span data-stu-id="cd553-154">Set `miNative` and `miUnmanaged`.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="cd553-155">Wymagania</span><span class="sxs-lookup"><span data-stu-id="cd553-155">Requirements</span></span>  
 <span data-ttu-id="cd553-156">**Platformy:** Zobacz [Wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="cd553-156">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="cd553-157">**Nagłówek:** Okręg wyborczy Cor.h</span><span class="sxs-lookup"><span data-stu-id="cd553-157">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="cd553-158">**Biblioteka:** Używany jako zasób w pliku MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="cd553-158">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="cd553-159">**Wersje programu .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="cd553-159">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cd553-160">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="cd553-160">See also</span></span>

- [<span data-ttu-id="cd553-161">IMetaDataEmit — Interfejs</span><span class="sxs-lookup"><span data-stu-id="cd553-161">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [<span data-ttu-id="cd553-162">IMetaDataEmit2, interfejs</span><span class="sxs-lookup"><span data-stu-id="cd553-162">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
