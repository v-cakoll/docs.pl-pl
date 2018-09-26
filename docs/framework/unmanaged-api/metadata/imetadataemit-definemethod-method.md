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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 2dbc6b5ffaa3a381bdd657059a682a3d12dc4cf1
ms.sourcegitcommit: 213292dfbb0c37d83f62709959ff55c50af5560d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/25/2018
ms.locfileid: "47109670"
---
# <a name="imetadataemitdefinemethod-method"></a><span data-ttu-id="c5898-102">IMetaDataEmit::DefineMethod — Metoda</span><span class="sxs-lookup"><span data-stu-id="c5898-102">IMetaDataEmit::DefineMethod Method</span></span>
<span data-ttu-id="c5898-103">Tworzy definicję metody lub funkcja globalna o określonej sygnaturze i zwraca token do tej definicji metody.</span><span class="sxs-lookup"><span data-stu-id="c5898-103">Creates a definition for a method or global function with the specified signature, and returns a token to that method definition.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c5898-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="c5898-104">Syntax</span></span>  
  
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
  
#### <a name="parameters"></a><span data-ttu-id="c5898-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="c5898-105">Parameters</span></span>  
 `td`  
 <span data-ttu-id="c5898-106">[in] `mdTypedef` Tokenu w klasie nadrzędnej lub interfejs nadrzędny metody.</span><span class="sxs-lookup"><span data-stu-id="c5898-106">[in] The `mdTypedef` token of the parent class or parent interface of the method.</span></span> <span data-ttu-id="c5898-107">Ustaw `td` do `mdTokenNil`, jeśli zamierzasz zdefiniować funkcją globalną.</span><span class="sxs-lookup"><span data-stu-id="c5898-107">Set `td` to `mdTokenNil`, if you are defining a global function.</span></span>  
  
 `szName`  
 <span data-ttu-id="c5898-108">[in] Nazwa elementu członkowskiego w formacie Unicode.</span><span class="sxs-lookup"><span data-stu-id="c5898-108">[in] The member name in Unicode.</span></span>  
  
 `dwMethodFlags`  
 <span data-ttu-id="c5898-109">[in] Wartość [cormethodattr —](../../../../docs/framework/unmanaged-api/metadata/cormethodattr-enumeration.md) wyliczenie, które określa atrybuty, metody lub funkcji globalnych.</span><span class="sxs-lookup"><span data-stu-id="c5898-109">[in] A value of the [CorMethodAttr](../../../../docs/framework/unmanaged-api/metadata/cormethodattr-enumeration.md) enumeration that specifies the attributes of the method or global function.</span></span>  
  
 `pvSigBlob`  
 <span data-ttu-id="c5898-110">[in] Podpis metody.</span><span class="sxs-lookup"><span data-stu-id="c5898-110">[in] The method signature.</span></span> <span data-ttu-id="c5898-111">Podpis jest trwały dostarczony.</span><span class="sxs-lookup"><span data-stu-id="c5898-111">The signature is persisted as supplied.</span></span> <span data-ttu-id="c5898-112">Jeśli musisz określić dodatkowe informacje dotyczące parametrów, należy użyć [IMetaDataEmit::SetParamProps](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-setparamprops-method.md) metody.</span><span class="sxs-lookup"><span data-stu-id="c5898-112">If you need to specify additional information for any parameters, use the [IMetaDataEmit::SetParamProps](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-setparamprops-method.md) method.</span></span>  
  
 `cbSigBlob`  
 <span data-ttu-id="c5898-113">[in] Liczba bajtów w `pvSigBlob`.</span><span class="sxs-lookup"><span data-stu-id="c5898-113">[in] The count of bytes in `pvSigBlob`.</span></span>  
  
 `ulCodeRVA`  
 <span data-ttu-id="c5898-114">[in] Adres kodu.</span><span class="sxs-lookup"><span data-stu-id="c5898-114">[in] The address of the code.</span></span>  
  
 `dwImplFlags`  
 <span data-ttu-id="c5898-115">[in] Wartość [cormethodimpl —](../../../../docs/framework/unmanaged-api/metadata/cormethodimpl-enumeration.md) wyliczenie, które określa funkcje implementacji metody.</span><span class="sxs-lookup"><span data-stu-id="c5898-115">[in] A value of the [CorMethodImpl](../../../../docs/framework/unmanaged-api/metadata/cormethodimpl-enumeration.md) enumeration that specifies the implementation features of the method.</span></span>  
  
 `pmd`  
 <span data-ttu-id="c5898-116">[out] Token składowej.</span><span class="sxs-lookup"><span data-stu-id="c5898-116">[out] The member token.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="c5898-117">Uwagi</span><span class="sxs-lookup"><span data-stu-id="c5898-117">Remarks</span></span>  
 <span data-ttu-id="c5898-118">Metadane interfejsu API gwarantuje można utrwalić metod opisanych w tej samej kolejności, jak obiekt wywołujący emituje je dla danego otaczającej klasy lub interfejsu, która została określona w `td` parametru.</span><span class="sxs-lookup"><span data-stu-id="c5898-118">The metadata API guarantees to persist methods in the same order as the caller emits them for a given enclosing class or interface, which is specified in the `td` parameter.</span></span>  
  
 <span data-ttu-id="c5898-119">Dodatkowe informacje na temat użytkowania `DefineMethod` i ustawienia określonego parametru są podane poniżej.</span><span class="sxs-lookup"><span data-stu-id="c5898-119">Additional information regarding the use of `DefineMethod` and particular parameter settings is given below.</span></span>  
  
## <a name="slots-in-the-v-table"></a><span data-ttu-id="c5898-120">Gniazda w tabeli V</span><span class="sxs-lookup"><span data-stu-id="c5898-120">Slots in the V-table</span></span>  
 <span data-ttu-id="c5898-121">Środowisko wykonawcze używa definicji metody, aby skonfigurować miejsc v tabeli.</span><span class="sxs-lookup"><span data-stu-id="c5898-121">The runtime uses method definitions to set up v-table slots.</span></span> <span data-ttu-id="c5898-122">W przypadku, gdy jeden lub więcej miejsc muszą być pominięte, na przykład aby zachować parzystości z układem interfejsu COM, fikcyjnego metoda jest zdefiniowana na podjęcie miejsca lub miejsc, w tabeli v; Ustaw `dwMethodFlags` do `mdRTSpecialName` wartość [cormethodattr —](../../../../docs/framework/unmanaged-api/metadata/cormethodattr-enumeration.md) wyliczenie i określ nazwę jako:</span><span class="sxs-lookup"><span data-stu-id="c5898-122">In the case where one or more slots need to be skipped, such as to preserve parity with a COM interface layout, a dummy method is defined to take up the slot or slots in the v-table; set the `dwMethodFlags` to the `mdRTSpecialName` value of the [CorMethodAttr](../../../../docs/framework/unmanaged-api/metadata/cormethodattr-enumeration.md) enumeration and specify the name as:</span></span>  
  
 <span data-ttu-id="c5898-123">_VtblGap\<*SequenceNumber*>\<\_*CountOfSlots*></span><span class="sxs-lookup"><span data-stu-id="c5898-123">_VtblGap\<*SequenceNumber*>\<\_*CountOfSlots*></span></span>
  
 <span data-ttu-id="c5898-124">gdzie *SequenceNumber* to numer sekwencji, metody i *CountOfSlots* jest liczba miejsc, aby pominąć w tabeli v.</span><span class="sxs-lookup"><span data-stu-id="c5898-124">where *SequenceNumber* is the sequence number of the method and *CountOfSlots* is the number of slots to skip in the v-table.</span></span> <span data-ttu-id="c5898-125">Jeśli *CountOfSlots* jest pominięty, przyjmowana jest wartość 1.</span><span class="sxs-lookup"><span data-stu-id="c5898-125">If *CountOfSlots* is omitted, 1 is assumed.</span></span> <span data-ttu-id="c5898-126">Te metody fikcyjnego z rolą nie są wywoływane z poziomu kodu zarządzanego lub niezarządzanego i każda próba ich wywołania w kodzie zarządzanym lub niezarządzanym, generuje wyjątek.</span><span class="sxs-lookup"><span data-stu-id="c5898-126">These dummy methods are not callable from either managed or unmanaged code and any attempt to call them, from either managed or unmanaged code, generates an exception.</span></span> <span data-ttu-id="c5898-127">Ich służy wyłącznie do zajmują miejsce, w tabeli v generowany przez środowisko uruchomieniowe integracji modelu COM.</span><span class="sxs-lookup"><span data-stu-id="c5898-127">Their only purpose is to take up space in the v-table that the runtime generates for COM integration.</span></span>  
  
## <a name="duplicate-methods"></a><span data-ttu-id="c5898-128">Zduplikowane metody</span><span class="sxs-lookup"><span data-stu-id="c5898-128">Duplicate Methods</span></span>  
 <span data-ttu-id="c5898-129">Nie powinna definiować metody zduplikowane.</span><span class="sxs-lookup"><span data-stu-id="c5898-129">You should not define duplicate methods.</span></span> <span data-ttu-id="c5898-130">Oznacza to, nie należy wywołać `DefineMethod` z zestawem zduplikowane wartości w `td`, `wzName`, i `pvSig` parametrów.</span><span class="sxs-lookup"><span data-stu-id="c5898-130">That is, you should not call `DefineMethod` with a duplicate set of values in the `td`, `wzName`, and `pvSig` parameters.</span></span> <span data-ttu-id="c5898-131">(Te trzy parametry, razem jednoznacznie określić metody.).</span><span class="sxs-lookup"><span data-stu-id="c5898-131">(These three parameters together uniquely define the method.).</span></span> <span data-ttu-id="c5898-132">Jednak można użyć zduplikowanych triple pod warunkiem, że w przypadku jednej z definicji metody, można ustawić `mdPrivateScope` bit w `dwMethodFlags` parametru.</span><span class="sxs-lookup"><span data-stu-id="c5898-132">However, you can use a duplicate triple provided that, for one of the method definitions, you set the `mdPrivateScope` bit in the `dwMethodFlags` parameter.</span></span> <span data-ttu-id="c5898-133">( `mdPrivateScope` Bit oznacza, że kompilator nie zostanie wyemitowany przez odwołanie do tę definicję metody.)</span><span class="sxs-lookup"><span data-stu-id="c5898-133">(The `mdPrivateScope` bit means that the compiler will not emit a reference to this method definition.)</span></span>  
  
## <a name="method-implementation-information"></a><span data-ttu-id="c5898-134">Informacje o implementacji — metoda</span><span class="sxs-lookup"><span data-stu-id="c5898-134">Method Implementation Information</span></span>  
 <span data-ttu-id="c5898-135">Informacje o implementacji metody często nie jest znany w czasie, który jest zadeklarowany metody.</span><span class="sxs-lookup"><span data-stu-id="c5898-135">Information about the method implementation is often not known at the time the method is declared.</span></span> <span data-ttu-id="c5898-136">W związku z tym, nie trzeba przekazać wartości w `ulCodeRVA` i `dwImplFlags` parametrów podczas wywoływania `DefineMethod`.</span><span class="sxs-lookup"><span data-stu-id="c5898-136">Therefore, you do not need to pass values in the `ulCodeRVA` and `dwImplFlags` parameters when calling `DefineMethod`.</span></span> <span data-ttu-id="c5898-137">Wartości, które mogą być dostarczane później za pomocą [IMetaDataEmit::SetMethodImplFlags](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-setmethodimplflags-method.md) lub [IMetaDataEmit::SetRVA](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-setrva-method.md), odpowiednio.</span><span class="sxs-lookup"><span data-stu-id="c5898-137">The values can be supplied later through [IMetaDataEmit::SetMethodImplFlags](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-setmethodimplflags-method.md) or [IMetaDataEmit::SetRVA](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-setrva-method.md), as appropriate.</span></span>  
  
 <span data-ttu-id="c5898-138">W niektórych sytuacjach, takich jak wywołania platformy (funkcja PInvoke) lub scenariuszach międzyoperacyjnego modelu COM, treści metody nie zostanie podany, i `ulCodeRVA` powinna być równa zero.</span><span class="sxs-lookup"><span data-stu-id="c5898-138">In some situations, such as platform invocation (PInvoke) or COM interop scenarios, the method body will not be supplied, and `ulCodeRVA` should be set to zero.</span></span> <span data-ttu-id="c5898-139">W takich sytuacjach metody powinna nie być oznaczane jako abstrakcyjny, ponieważ środowisko uruchomieniowe lokalizuje wdrożenia.</span><span class="sxs-lookup"><span data-stu-id="c5898-139">In these situations, the method should not be tagged as abstract, because the runtime will locate the implementation.</span></span>  
  
## <a name="defining-a-method-for-pinvoke"></a><span data-ttu-id="c5898-140">Definiowanie metody dla funkcji PInvoke</span><span class="sxs-lookup"><span data-stu-id="c5898-140">Defining a Method for PInvoke</span></span>  
 <span data-ttu-id="c5898-141">Dla każdego z niezarządzanej funkcji można wywołać za pomocą usług PInvoke należy zdefiniować zarządzanych metodę, która reprezentuje funkcję docelowej niezarządzanych.</span><span class="sxs-lookup"><span data-stu-id="c5898-141">For each unmanaged function to be called through PInvoke, you must define a managed method that represents the target unmanaged function.</span></span> <span data-ttu-id="c5898-142">Aby zdefiniować zarządzaną metodą, należy użyć `DefineMethod` niektórych parametrów niektórych wartości w zależności od sposobu, w którym jest używana funkcja PInvoke:</span><span class="sxs-lookup"><span data-stu-id="c5898-142">To define the managed method, use `DefineMethod` with some of the parameters set to certain values, depending on the way in which PInvoke is used:</span></span>  
  
-   <span data-ttu-id="c5898-143">Wartość true, PInvoke — obejmuje wywołania metody niezarządzanego zewnętrznej znajdującej się w niezarządzaną biblioteką DLL.</span><span class="sxs-lookup"><span data-stu-id="c5898-143">True PInvoke - involves invocation of an external unmanaged method that resides in an unmanaged DLL.</span></span>  
  
-   <span data-ttu-id="c5898-144">Lokalne PInvoke — obejmuje wywołania metody natywnej niezarządzanych, osadzonego w bieżącym modułu zarządzanego.</span><span class="sxs-lookup"><span data-stu-id="c5898-144">Local PInvoke - involves invocation of a native unmanaged method that is embedded in the current managed module.</span></span>  
  
 <span data-ttu-id="c5898-145">Ustawienia parametru są podane w poniższej tabeli.</span><span class="sxs-lookup"><span data-stu-id="c5898-145">The parameter settings are given in the following table.</span></span>  
  
|<span data-ttu-id="c5898-146">Parametr</span><span class="sxs-lookup"><span data-stu-id="c5898-146">Parameter</span></span>|<span data-ttu-id="c5898-147">Wartości true funkcji PInvoke</span><span class="sxs-lookup"><span data-stu-id="c5898-147">Values for true PInvoke</span></span>|<span data-ttu-id="c5898-148">Wartości dla lokalnych funkcji PInvoke</span><span class="sxs-lookup"><span data-stu-id="c5898-148">Values for local PInvoke</span></span>|  
|---------------|-----------------------------|------------------------------|  
|`dwMethodFlags`||<span data-ttu-id="c5898-149">Ustaw `mdStatic`; clear `mdSynchronized` i `mdAbstract`.</span><span class="sxs-lookup"><span data-stu-id="c5898-149">Set `mdStatic`; clear `mdSynchronized` and `mdAbstract`.</span></span>|  
|`pvSigBlob`|<span data-ttu-id="c5898-150">Typy zarządzane prawidłowe wspólnego języka środowiska uruchomieniowego (języka wspólnego CLR) podpis metody z parametrami, które są prawidłowe.</span><span class="sxs-lookup"><span data-stu-id="c5898-150">A valid common language runtime (CLR) method signature with parameters that are valid managed types.</span></span>|<span data-ttu-id="c5898-151">Typy zarządzane prawidłowego podpisu metody CLR z parametrami, które są prawidłowe.</span><span class="sxs-lookup"><span data-stu-id="c5898-151">A valid CLR method signature with parameters that are valid managed types.</span></span>|  
|`ulCodeRVA`||<span data-ttu-id="c5898-152">0</span><span class="sxs-lookup"><span data-stu-id="c5898-152">0</span></span>|  
|`dwImplFlags`|<span data-ttu-id="c5898-153">Ustaw `miCil` i `miManaged`.</span><span class="sxs-lookup"><span data-stu-id="c5898-153">Set `miCil` and `miManaged`.</span></span>|<span data-ttu-id="c5898-154">Ustaw `miNative` i `miUnmanaged`.</span><span class="sxs-lookup"><span data-stu-id="c5898-154">Set `miNative` and `miUnmanaged`.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="c5898-155">Wymagania</span><span class="sxs-lookup"><span data-stu-id="c5898-155">Requirements</span></span>  
 <span data-ttu-id="c5898-156">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c5898-156">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c5898-157">**Nagłówek:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="c5898-157">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="c5898-158">**Biblioteka:** używany jako zasób w MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="c5898-158">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="c5898-159">**Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c5898-159">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c5898-160">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="c5898-160">See Also</span></span>  
 [<span data-ttu-id="c5898-161">IMetaDataEmit, interfejs</span><span class="sxs-lookup"><span data-stu-id="c5898-161">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)  
 [<span data-ttu-id="c5898-162">IMetaDataEmit2, interfejs</span><span class="sxs-lookup"><span data-stu-id="c5898-162">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
