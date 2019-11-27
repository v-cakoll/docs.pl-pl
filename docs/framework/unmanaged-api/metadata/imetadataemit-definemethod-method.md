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
ms.openlocfilehash: c46b075341742aac605537a08b762b3cf47ef35b
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/23/2019
ms.locfileid: "74431804"
---
# <a name="imetadataemitdefinemethod-method"></a><span data-ttu-id="3b826-102">IMetaDataEmit::DefineMethod — Metoda</span><span class="sxs-lookup"><span data-stu-id="3b826-102">IMetaDataEmit::DefineMethod Method</span></span>
<span data-ttu-id="3b826-103">Tworzy definicję metody lub funkcji globalnej z określoną sygnaturą i zwraca token do tej definicji metody.</span><span class="sxs-lookup"><span data-stu-id="3b826-103">Creates a definition for a method or global function with the specified signature, and returns a token to that method definition.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3b826-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="3b826-104">Syntax</span></span>  
  
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
  
## <a name="parameters"></a><span data-ttu-id="3b826-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="3b826-105">Parameters</span></span>  
 `td`  
 <span data-ttu-id="3b826-106">podczas Token `mdTypedef` klasy nadrzędnej lub interfejsu nadrzędnego metody.</span><span class="sxs-lookup"><span data-stu-id="3b826-106">[in] The `mdTypedef` token of the parent class or parent interface of the method.</span></span> <span data-ttu-id="3b826-107">Ustaw `td` na `mdTokenNil`, jeśli definiujesz funkcję globalną.</span><span class="sxs-lookup"><span data-stu-id="3b826-107">Set `td` to `mdTokenNil`, if you are defining a global function.</span></span>  
  
 `szName`  
 <span data-ttu-id="3b826-108">podczas Nazwa elementu członkowskiego w formacie Unicode.</span><span class="sxs-lookup"><span data-stu-id="3b826-108">[in] The member name in Unicode.</span></span>  
  
 `dwMethodFlags`  
 <span data-ttu-id="3b826-109">podczas Wartość wyliczenia [CorMethodAttr —](../../../../docs/framework/unmanaged-api/metadata/cormethodattr-enumeration.md) , która określa atrybuty metody lub funkcji globalnej.</span><span class="sxs-lookup"><span data-stu-id="3b826-109">[in] A value of the [CorMethodAttr](../../../../docs/framework/unmanaged-api/metadata/cormethodattr-enumeration.md) enumeration that specifies the attributes of the method or global function.</span></span>  
  
 `pvSigBlob`  
 <span data-ttu-id="3b826-110">podczas Podpis metody.</span><span class="sxs-lookup"><span data-stu-id="3b826-110">[in] The method signature.</span></span> <span data-ttu-id="3b826-111">Sygnatura jest utrwalana zgodnie z podanym opisem.</span><span class="sxs-lookup"><span data-stu-id="3b826-111">The signature is persisted as supplied.</span></span> <span data-ttu-id="3b826-112">Jeśli konieczne jest określenie dodatkowych informacji dla dowolnych parametrów, użyj metody [IMetaDataEmit:: SetParamProps —](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-setparamprops-method.md) .</span><span class="sxs-lookup"><span data-stu-id="3b826-112">If you need to specify additional information for any parameters, use the [IMetaDataEmit::SetParamProps](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-setparamprops-method.md) method.</span></span>  
  
 `cbSigBlob`  
 <span data-ttu-id="3b826-113">podczas Liczba bajtów w `pvSigBlob`.</span><span class="sxs-lookup"><span data-stu-id="3b826-113">[in] The count of bytes in `pvSigBlob`.</span></span>  
  
 `ulCodeRVA`  
 <span data-ttu-id="3b826-114">podczas Adres kodu.</span><span class="sxs-lookup"><span data-stu-id="3b826-114">[in] The address of the code.</span></span>  
  
 `dwImplFlags`  
 <span data-ttu-id="3b826-115">podczas Wartość wyliczenia [CorMethodImpl —](../../../../docs/framework/unmanaged-api/metadata/cormethodimpl-enumeration.md) , która określa funkcje implementacji metody.</span><span class="sxs-lookup"><span data-stu-id="3b826-115">[in] A value of the [CorMethodImpl](../../../../docs/framework/unmanaged-api/metadata/cormethodimpl-enumeration.md) enumeration that specifies the implementation features of the method.</span></span>  
  
 `pmd`  
 <span data-ttu-id="3b826-116">określoną Token elementu członkowskiego.</span><span class="sxs-lookup"><span data-stu-id="3b826-116">[out] The member token.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="3b826-117">Uwagi</span><span class="sxs-lookup"><span data-stu-id="3b826-117">Remarks</span></span>  
 <span data-ttu-id="3b826-118">Interfejs API metadanych gwarantuje zachowanie metod w takiej samej kolejności, w jakiej obiekt wywołujący emituje je dla danej klasy lub interfejsu, który jest określony w parametrze `td`.</span><span class="sxs-lookup"><span data-stu-id="3b826-118">The metadata API guarantees to persist methods in the same order as the caller emits them for a given enclosing class or interface, which is specified in the `td` parameter.</span></span>  
  
 <span data-ttu-id="3b826-119">Poniżej przedstawiono dodatkowe informacje dotyczące używania `DefineMethod` i określonych ustawień parametrów.</span><span class="sxs-lookup"><span data-stu-id="3b826-119">Additional information regarding the use of `DefineMethod` and particular parameter settings is given below.</span></span>  
  
## <a name="slots-in-the-v-table"></a><span data-ttu-id="3b826-120">Gniazda w tabeli V</span><span class="sxs-lookup"><span data-stu-id="3b826-120">Slots in the V-table</span></span>  
 <span data-ttu-id="3b826-121">Środowisko uruchomieniowe używa definicji metod do konfigurowania miejsc z tabelą v.</span><span class="sxs-lookup"><span data-stu-id="3b826-121">The runtime uses method definitions to set up v-table slots.</span></span> <span data-ttu-id="3b826-122">W przypadku, gdy co najmniej jeden z gniazd musi być pominięty, na przykład w celu zachowania parzystości przy użyciu układu interfejsu COM, Metoda fikcyjna jest definiowana w celu założenia gniazda lub gniazd w tabeli v. Ustaw `dwMethodFlags` na wartość `mdRTSpecialName` wyliczenia [CorMethodAttr —](../../../../docs/framework/unmanaged-api/metadata/cormethodattr-enumeration.md) i określ nazwę jako:</span><span class="sxs-lookup"><span data-stu-id="3b826-122">In the case where one or more slots need to be skipped, such as to preserve parity with a COM interface layout, a dummy method is defined to take up the slot or slots in the v-table; set the `dwMethodFlags` to the `mdRTSpecialName` value of the [CorMethodAttr](../../../../docs/framework/unmanaged-api/metadata/cormethodattr-enumeration.md) enumeration and specify the name as:</span></span>  
  
 <span data-ttu-id="3b826-123">_VtblGap\<*SequenceNumber*>\<\_*CountOfSlots*></span><span class="sxs-lookup"><span data-stu-id="3b826-123">_VtblGap\<*SequenceNumber*>\<\_*CountOfSlots*></span></span>
  
 <span data-ttu-id="3b826-124">gdzie *SequenceNumber* jest numerem sekwencji metody, a *CountOfSlots* to liczba gniazd do pominięcia w tabeli v.</span><span class="sxs-lookup"><span data-stu-id="3b826-124">where *SequenceNumber* is the sequence number of the method and *CountOfSlots* is the number of slots to skip in the v-table.</span></span> <span data-ttu-id="3b826-125">W przypadku pominięcia *CountOfSlots* przyjmuje się wartość 1.</span><span class="sxs-lookup"><span data-stu-id="3b826-125">If *CountOfSlots* is omitted, 1 is assumed.</span></span> <span data-ttu-id="3b826-126">Te metody fikcyjne nie są wywoływane z kodu zarządzanego lub niezarządzanego, a wszystkie próby wywołania ich, z kodu zarządzanego lub niezarządzanego, generują wyjątek.</span><span class="sxs-lookup"><span data-stu-id="3b826-126">These dummy methods are not callable from either managed or unmanaged code and any attempt to call them, from either managed or unmanaged code, generates an exception.</span></span> <span data-ttu-id="3b826-127">Jedynym celem jest zajęcie miejsca w tabeli v, która jest generowana przez środowisko uruchomieniowe na potrzeby integracji z modelem COM.</span><span class="sxs-lookup"><span data-stu-id="3b826-127">Their only purpose is to take up space in the v-table that the runtime generates for COM integration.</span></span>  
  
## <a name="duplicate-methods"></a><span data-ttu-id="3b826-128">Metody duplikowania</span><span class="sxs-lookup"><span data-stu-id="3b826-128">Duplicate Methods</span></span>  
 <span data-ttu-id="3b826-129">Nie należy definiować zduplikowanych metod.</span><span class="sxs-lookup"><span data-stu-id="3b826-129">You should not define duplicate methods.</span></span> <span data-ttu-id="3b826-130">Oznacza to, że nie należy wywoływać `DefineMethod` ze zduplikowanym zestawem wartości w parametrach `td`, `wzName`i `pvSig`.</span><span class="sxs-lookup"><span data-stu-id="3b826-130">That is, you should not call `DefineMethod` with a duplicate set of values in the `td`, `wzName`, and `pvSig` parameters.</span></span> <span data-ttu-id="3b826-131">(Te trzy parametry jednoznacznie definiują metodę).</span><span class="sxs-lookup"><span data-stu-id="3b826-131">(These three parameters together uniquely define the method.).</span></span> <span data-ttu-id="3b826-132">Można jednak użyć duplikatu trzykrotnie, pod warunkiem, że dla jednej z definicji metody ustawiasz bit `mdPrivateScope` w parametrze `dwMethodFlags`.</span><span class="sxs-lookup"><span data-stu-id="3b826-132">However, you can use a duplicate triple provided that, for one of the method definitions, you set the `mdPrivateScope` bit in the `dwMethodFlags` parameter.</span></span> <span data-ttu-id="3b826-133">(`mdPrivateScope` bit oznacza, że kompilator nie emituje odwołania do tej definicji metody).</span><span class="sxs-lookup"><span data-stu-id="3b826-133">(The `mdPrivateScope` bit means that the compiler will not emit a reference to this method definition.)</span></span>  
  
## <a name="method-implementation-information"></a><span data-ttu-id="3b826-134">Informacje o implementacji metody</span><span class="sxs-lookup"><span data-stu-id="3b826-134">Method Implementation Information</span></span>  
 <span data-ttu-id="3b826-135">Informacje o implementacji metody często nie są znane w momencie zadeklarowania metody.</span><span class="sxs-lookup"><span data-stu-id="3b826-135">Information about the method implementation is often not known at the time the method is declared.</span></span> <span data-ttu-id="3b826-136">W związku z tym nie trzeba przekazywać wartości w `ulCodeRVA` i `dwImplFlags` parametrów podczas wywoływania `DefineMethod`.</span><span class="sxs-lookup"><span data-stu-id="3b826-136">Therefore, you do not need to pass values in the `ulCodeRVA` and `dwImplFlags` parameters when calling `DefineMethod`.</span></span> <span data-ttu-id="3b826-137">Wartości można dostarczyć później za pomocą [IMetaDataEmit:: SetMethodImplFlags —](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-setmethodimplflags-method.md) lub [IMetaDataEmit:: SetRVA —](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-setrva-method.md), zgodnie z potrzebami.</span><span class="sxs-lookup"><span data-stu-id="3b826-137">The values can be supplied later through [IMetaDataEmit::SetMethodImplFlags](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-setmethodimplflags-method.md) or [IMetaDataEmit::SetRVA](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-setrva-method.md), as appropriate.</span></span>  
  
 <span data-ttu-id="3b826-138">W niektórych sytuacjach, takich jak scenariusze wywołania platformy (PInvoke) lub współdziałanie z modelem COM, treść metody nie zostanie podana, a `ulCodeRVA` powinna być ustawiona na zero.</span><span class="sxs-lookup"><span data-stu-id="3b826-138">In some situations, such as platform invocation (PInvoke) or COM interop scenarios, the method body will not be supplied, and `ulCodeRVA` should be set to zero.</span></span> <span data-ttu-id="3b826-139">W takich sytuacjach metoda nie powinna być oznaczona jako abstrakcyjna, ponieważ środowisko uruchomieniowe odnajdzie implementację.</span><span class="sxs-lookup"><span data-stu-id="3b826-139">In these situations, the method should not be tagged as abstract, because the runtime will locate the implementation.</span></span>  
  
## <a name="defining-a-method-for-pinvoke"></a><span data-ttu-id="3b826-140">Definiowanie metody dla funkcji PInvoke</span><span class="sxs-lookup"><span data-stu-id="3b826-140">Defining a Method for PInvoke</span></span>  
 <span data-ttu-id="3b826-141">Dla każdej funkcji niezarządzanej, która ma być wywoływana za pomocą funkcji PInvoke, należy zdefiniować metodę zarządzaną, która reprezentuje docelową funkcję niezarządzaną.</span><span class="sxs-lookup"><span data-stu-id="3b826-141">For each unmanaged function to be called through PInvoke, you must define a managed method that represents the target unmanaged function.</span></span> <span data-ttu-id="3b826-142">Aby zdefiniować metodę zarządzaną, należy użyć `DefineMethod` z pewnymi parametrami ustawionymi na określone wartości, w zależności od sposobu użycia funkcji PInvoke:</span><span class="sxs-lookup"><span data-stu-id="3b826-142">To define the managed method, use `DefineMethod` with some of the parameters set to certain values, depending on the way in which PInvoke is used:</span></span>  
  
- <span data-ttu-id="3b826-143">True PInvoke-obejmuje wywołanie zewnętrznej metody niezarządzanej, która znajduje się w niezarządzanej bibliotece DLL.</span><span class="sxs-lookup"><span data-stu-id="3b826-143">True PInvoke - involves invocation of an external unmanaged method that resides in an unmanaged DLL.</span></span>  
  
- <span data-ttu-id="3b826-144">Lokalny element PInvoke-obejmuje wywołanie natywnej metody niezarządzanej osadzonej w bieżącym module zarządzanym.</span><span class="sxs-lookup"><span data-stu-id="3b826-144">Local PInvoke - involves invocation of a native unmanaged method that is embedded in the current managed module.</span></span>  
  
 <span data-ttu-id="3b826-145">Ustawienia parametrów są podano w poniższej tabeli.</span><span class="sxs-lookup"><span data-stu-id="3b826-145">The parameter settings are given in the following table.</span></span>  
  
|<span data-ttu-id="3b826-146">Parametr</span><span class="sxs-lookup"><span data-stu-id="3b826-146">Parameter</span></span>|<span data-ttu-id="3b826-147">Wartości dla prawdy</span><span class="sxs-lookup"><span data-stu-id="3b826-147">Values for true PInvoke</span></span>|<span data-ttu-id="3b826-148">Wartości dla lokalnego elementu PInvoke</span><span class="sxs-lookup"><span data-stu-id="3b826-148">Values for local PInvoke</span></span>|  
|---------------|-----------------------------|------------------------------|  
|`dwMethodFlags`||<span data-ttu-id="3b826-149">Ustaw `mdStatic`; Wyczyść `mdSynchronized` i `mdAbstract`.</span><span class="sxs-lookup"><span data-stu-id="3b826-149">Set `mdStatic`; clear `mdSynchronized` and `mdAbstract`.</span></span>|  
|`pvSigBlob`|<span data-ttu-id="3b826-150">Prawidłowy podpis metody środowiska uruchomieniowego języka wspólnego (CLR) z parametrami, które są prawidłowymi typami zarządzanymi.</span><span class="sxs-lookup"><span data-stu-id="3b826-150">A valid common language runtime (CLR) method signature with parameters that are valid managed types.</span></span>|<span data-ttu-id="3b826-151">Prawidłowy podpis metody CLR z parametrami, które są prawidłowymi typami zarządzanymi.</span><span class="sxs-lookup"><span data-stu-id="3b826-151">A valid CLR method signature with parameters that are valid managed types.</span></span>|  
|`ulCodeRVA`||<span data-ttu-id="3b826-152">0</span><span class="sxs-lookup"><span data-stu-id="3b826-152">0</span></span>|  
|`dwImplFlags`|<span data-ttu-id="3b826-153">Ustaw `miCil` i `miManaged`.</span><span class="sxs-lookup"><span data-stu-id="3b826-153">Set `miCil` and `miManaged`.</span></span>|<span data-ttu-id="3b826-154">Ustaw `miNative` i `miUnmanaged`.</span><span class="sxs-lookup"><span data-stu-id="3b826-154">Set `miNative` and `miUnmanaged`.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="3b826-155">Wymagania</span><span class="sxs-lookup"><span data-stu-id="3b826-155">Requirements</span></span>  
 <span data-ttu-id="3b826-156">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3b826-156">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3b826-157">**Nagłówek:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="3b826-157">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="3b826-158">**Biblioteka:** Używany jako zasób w bibliotece MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="3b826-158">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="3b826-159">**Wersje .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3b826-159">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3b826-160">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="3b826-160">See also</span></span>

- [<span data-ttu-id="3b826-161">IMetaDataEmit, interfejs</span><span class="sxs-lookup"><span data-stu-id="3b826-161">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [<span data-ttu-id="3b826-162">IMetaDataEmit2, interfejs</span><span class="sxs-lookup"><span data-stu-id="3b826-162">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
