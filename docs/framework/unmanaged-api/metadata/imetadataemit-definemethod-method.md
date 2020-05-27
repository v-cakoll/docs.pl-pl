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
ms.openlocfilehash: 514f227e3c0c385f61090079d2f5214dac9b3924
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/27/2020
ms.locfileid: "84004533"
---
# <a name="imetadataemitdefinemethod-method"></a><span data-ttu-id="3fe45-102">IMetaDataEmit::DefineMethod — Metoda</span><span class="sxs-lookup"><span data-stu-id="3fe45-102">IMetaDataEmit::DefineMethod Method</span></span>
<span data-ttu-id="3fe45-103">Tworzy definicję metody lub funkcji globalnej z określoną sygnaturą i zwraca token do tej definicji metody.</span><span class="sxs-lookup"><span data-stu-id="3fe45-103">Creates a definition for a method or global function with the specified signature, and returns a token to that method definition.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3fe45-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="3fe45-104">Syntax</span></span>  
  
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
  
## <a name="parameters"></a><span data-ttu-id="3fe45-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="3fe45-105">Parameters</span></span>  
 `td`  
 <span data-ttu-id="3fe45-106">podczas `mdTypedef`Token klasy nadrzędnej lub interfejsu nadrzędnego metody.</span><span class="sxs-lookup"><span data-stu-id="3fe45-106">[in] The `mdTypedef` token of the parent class or parent interface of the method.</span></span> <span data-ttu-id="3fe45-107">Ustaw `td` na `mdTokenNil` , jeśli definiujesz funkcję globalną.</span><span class="sxs-lookup"><span data-stu-id="3fe45-107">Set `td` to `mdTokenNil`, if you are defining a global function.</span></span>  
  
 `szName`  
 <span data-ttu-id="3fe45-108">podczas Nazwa elementu członkowskiego w formacie Unicode.</span><span class="sxs-lookup"><span data-stu-id="3fe45-108">[in] The member name in Unicode.</span></span>  
  
 `dwMethodFlags`  
 <span data-ttu-id="3fe45-109">podczas Wartość wyliczenia [CorMethodAttr —](cormethodattr-enumeration.md) , która określa atrybuty metody lub funkcji globalnej.</span><span class="sxs-lookup"><span data-stu-id="3fe45-109">[in] A value of the [CorMethodAttr](cormethodattr-enumeration.md) enumeration that specifies the attributes of the method or global function.</span></span>  
  
 `pvSigBlob`  
 <span data-ttu-id="3fe45-110">podczas Podpis metody.</span><span class="sxs-lookup"><span data-stu-id="3fe45-110">[in] The method signature.</span></span> <span data-ttu-id="3fe45-111">Sygnatura jest utrwalana zgodnie z podanym opisem.</span><span class="sxs-lookup"><span data-stu-id="3fe45-111">The signature is persisted as supplied.</span></span> <span data-ttu-id="3fe45-112">Jeśli konieczne jest określenie dodatkowych informacji dla dowolnych parametrów, użyj metody [IMetaDataEmit:: SetParamProps —](imetadataemit-setparamprops-method.md) .</span><span class="sxs-lookup"><span data-stu-id="3fe45-112">If you need to specify additional information for any parameters, use the [IMetaDataEmit::SetParamProps](imetadataemit-setparamprops-method.md) method.</span></span>  
  
 `cbSigBlob`  
 <span data-ttu-id="3fe45-113">podczas Liczba bajtów w `pvSigBlob` .</span><span class="sxs-lookup"><span data-stu-id="3fe45-113">[in] The count of bytes in `pvSigBlob`.</span></span>  
  
 `ulCodeRVA`  
 <span data-ttu-id="3fe45-114">podczas Adres kodu.</span><span class="sxs-lookup"><span data-stu-id="3fe45-114">[in] The address of the code.</span></span>  
  
 `dwImplFlags`  
 <span data-ttu-id="3fe45-115">podczas Wartość wyliczenia [CorMethodImpl —](cormethodimpl-enumeration.md) , która określa funkcje implementacji metody.</span><span class="sxs-lookup"><span data-stu-id="3fe45-115">[in] A value of the [CorMethodImpl](cormethodimpl-enumeration.md) enumeration that specifies the implementation features of the method.</span></span>  
  
 `pmd`  
 <span data-ttu-id="3fe45-116">określoną Token elementu członkowskiego.</span><span class="sxs-lookup"><span data-stu-id="3fe45-116">[out] The member token.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="3fe45-117">Uwagi</span><span class="sxs-lookup"><span data-stu-id="3fe45-117">Remarks</span></span>  
 <span data-ttu-id="3fe45-118">Interfejs API metadanych gwarantuje zachowanie metod w takiej samej kolejności, w jakiej obiekt wywołujący emituje je dla danej klasy lub interfejsu, który jest określony w `td` parametrze.</span><span class="sxs-lookup"><span data-stu-id="3fe45-118">The metadata API guarantees to persist methods in the same order as the caller emits them for a given enclosing class or interface, which is specified in the `td` parameter.</span></span>  
  
 <span data-ttu-id="3fe45-119">Poniżej przedstawiono dodatkowe informacje dotyczące używania `DefineMethod` i określonych ustawień parametrów.</span><span class="sxs-lookup"><span data-stu-id="3fe45-119">Additional information regarding the use of `DefineMethod` and particular parameter settings is given below.</span></span>  
  
## <a name="slots-in-the-v-table"></a><span data-ttu-id="3fe45-120">Gniazda w tabeli V</span><span class="sxs-lookup"><span data-stu-id="3fe45-120">Slots in the V-table</span></span>  
 <span data-ttu-id="3fe45-121">Środowisko uruchomieniowe używa definicji metod do konfigurowania miejsc z tabelą v.</span><span class="sxs-lookup"><span data-stu-id="3fe45-121">The runtime uses method definitions to set up v-table slots.</span></span> <span data-ttu-id="3fe45-122">W przypadku, gdy co najmniej jeden z gniazd musi być pominięty, na przykład w celu zachowania parzystości przy użyciu układu interfejsu COM, Metoda fikcyjna jest definiowana w celu założenia gniazda lub gniazd w tabeli v. Ustaw `dwMethodFlags` na `mdRTSpecialName` wartość wyliczenia [CorMethodAttr —](cormethodattr-enumeration.md) i określ nazwę jako:</span><span class="sxs-lookup"><span data-stu-id="3fe45-122">In the case where one or more slots need to be skipped, such as to preserve parity with a COM interface layout, a dummy method is defined to take up the slot or slots in the v-table; set the `dwMethodFlags` to the `mdRTSpecialName` value of the [CorMethodAttr](cormethodattr-enumeration.md) enumeration and specify the name as:</span></span>  
  
 <span data-ttu-id="3fe45-123">_VtblGap\<*SequenceNumber*>\<\_*CountOfSlots*></span><span class="sxs-lookup"><span data-stu-id="3fe45-123">_VtblGap\<*SequenceNumber*>\<\_*CountOfSlots*></span></span>
  
 <span data-ttu-id="3fe45-124">gdzie *SequenceNumber* jest numerem sekwencji metody, a *CountOfSlots* to liczba gniazd do pominięcia w tabeli v.</span><span class="sxs-lookup"><span data-stu-id="3fe45-124">where *SequenceNumber* is the sequence number of the method and *CountOfSlots* is the number of slots to skip in the v-table.</span></span> <span data-ttu-id="3fe45-125">W przypadku pominięcia *CountOfSlots* przyjmuje się wartość 1.</span><span class="sxs-lookup"><span data-stu-id="3fe45-125">If *CountOfSlots* is omitted, 1 is assumed.</span></span> <span data-ttu-id="3fe45-126">Te metody fikcyjne nie są wywoływane z kodu zarządzanego lub niezarządzanego, a wszystkie próby wywołania ich, z kodu zarządzanego lub niezarządzanego, generują wyjątek.</span><span class="sxs-lookup"><span data-stu-id="3fe45-126">These dummy methods are not callable from either managed or unmanaged code and any attempt to call them, from either managed or unmanaged code, generates an exception.</span></span> <span data-ttu-id="3fe45-127">Jedynym celem jest zajęcie miejsca w tabeli v, która jest generowana przez środowisko uruchomieniowe na potrzeby integracji z modelem COM.</span><span class="sxs-lookup"><span data-stu-id="3fe45-127">Their only purpose is to take up space in the v-table that the runtime generates for COM integration.</span></span>  
  
## <a name="duplicate-methods"></a><span data-ttu-id="3fe45-128">Metody duplikowania</span><span class="sxs-lookup"><span data-stu-id="3fe45-128">Duplicate Methods</span></span>  
 <span data-ttu-id="3fe45-129">Nie należy definiować zduplikowanych metod.</span><span class="sxs-lookup"><span data-stu-id="3fe45-129">You should not define duplicate methods.</span></span> <span data-ttu-id="3fe45-130">Oznacza to, że nie należy wywoływać `DefineMethod` zduplikowanego zestawu wartości w `td` `wzName` `pvSig` parametrach, i.</span><span class="sxs-lookup"><span data-stu-id="3fe45-130">That is, you should not call `DefineMethod` with a duplicate set of values in the `td`, `wzName`, and `pvSig` parameters.</span></span> <span data-ttu-id="3fe45-131">(Te trzy parametry jednoznacznie definiują metodę).</span><span class="sxs-lookup"><span data-stu-id="3fe45-131">(These three parameters together uniquely define the method.).</span></span> <span data-ttu-id="3fe45-132">Można jednak użyć duplikatu trzykrotnie, pod warunkiem, że dla jednej z definicji metody ustawia się `mdPrivateScope` bit w `dwMethodFlags` parametrze.</span><span class="sxs-lookup"><span data-stu-id="3fe45-132">However, you can use a duplicate triple provided that, for one of the method definitions, you set the `mdPrivateScope` bit in the `dwMethodFlags` parameter.</span></span> <span data-ttu-id="3fe45-133">( `mdPrivateScope` Bit oznacza, że kompilator nie emituje odwołania do tej definicji metody).</span><span class="sxs-lookup"><span data-stu-id="3fe45-133">(The `mdPrivateScope` bit means that the compiler will not emit a reference to this method definition.)</span></span>  
  
## <a name="method-implementation-information"></a><span data-ttu-id="3fe45-134">Informacje o implementacji metody</span><span class="sxs-lookup"><span data-stu-id="3fe45-134">Method Implementation Information</span></span>  
 <span data-ttu-id="3fe45-135">Informacje o implementacji metody często nie są znane w momencie zadeklarowania metody.</span><span class="sxs-lookup"><span data-stu-id="3fe45-135">Information about the method implementation is often not known at the time the method is declared.</span></span> <span data-ttu-id="3fe45-136">W związku z tym nie trzeba przekazywać wartości w `ulCodeRVA` `dwImplFlags` parametrach i podczas wywoływania `DefineMethod` .</span><span class="sxs-lookup"><span data-stu-id="3fe45-136">Therefore, you do not need to pass values in the `ulCodeRVA` and `dwImplFlags` parameters when calling `DefineMethod`.</span></span> <span data-ttu-id="3fe45-137">Wartości można dostarczyć później za pomocą [IMetaDataEmit:: SetMethodImplFlags —](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-setmethodimplflags-method.md) lub [IMetaDataEmit:: SetRVA —](imetadataemit-setrva-method.md), zgodnie z potrzebami.</span><span class="sxs-lookup"><span data-stu-id="3fe45-137">The values can be supplied later through [IMetaDataEmit::SetMethodImplFlags](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-setmethodimplflags-method.md) or [IMetaDataEmit::SetRVA](imetadataemit-setrva-method.md), as appropriate.</span></span>  
  
 <span data-ttu-id="3fe45-138">W niektórych sytuacjach, takich jak scenariusze wywołania platformy (PInvoke) lub współdziałanie z modelem COM, treść metody nie zostanie podana i `ulCodeRVA` powinna być ustawiona na wartość zero.</span><span class="sxs-lookup"><span data-stu-id="3fe45-138">In some situations, such as platform invocation (PInvoke) or COM interop scenarios, the method body will not be supplied, and `ulCodeRVA` should be set to zero.</span></span> <span data-ttu-id="3fe45-139">W takich sytuacjach metoda nie powinna być oznaczona jako abstrakcyjna, ponieważ środowisko uruchomieniowe odnajdzie implementację.</span><span class="sxs-lookup"><span data-stu-id="3fe45-139">In these situations, the method should not be tagged as abstract, because the runtime will locate the implementation.</span></span>  
  
## <a name="defining-a-method-for-pinvoke"></a><span data-ttu-id="3fe45-140">Definiowanie metody dla funkcji PInvoke</span><span class="sxs-lookup"><span data-stu-id="3fe45-140">Defining a Method for PInvoke</span></span>  
 <span data-ttu-id="3fe45-141">Dla każdej funkcji niezarządzanej, która ma być wywoływana za pomocą funkcji PInvoke, należy zdefiniować metodę zarządzaną, która reprezentuje docelową funkcję niezarządzaną.</span><span class="sxs-lookup"><span data-stu-id="3fe45-141">For each unmanaged function to be called through PInvoke, you must define a managed method that represents the target unmanaged function.</span></span> <span data-ttu-id="3fe45-142">Aby zdefiniować zarządzaną metodę, użyj z niektórymi `DefineMethod` parametrami ustawionymi na określone wartości, w zależności od sposobu użycia funkcji PInvoke:</span><span class="sxs-lookup"><span data-stu-id="3fe45-142">To define the managed method, use `DefineMethod` with some of the parameters set to certain values, depending on the way in which PInvoke is used:</span></span>  
  
- <span data-ttu-id="3fe45-143">True PInvoke-obejmuje wywołanie zewnętrznej metody niezarządzanej, która znajduje się w niezarządzanej bibliotece DLL.</span><span class="sxs-lookup"><span data-stu-id="3fe45-143">True PInvoke - involves invocation of an external unmanaged method that resides in an unmanaged DLL.</span></span>  
  
- <span data-ttu-id="3fe45-144">Lokalny element PInvoke-obejmuje wywołanie natywnej metody niezarządzanej osadzonej w bieżącym module zarządzanym.</span><span class="sxs-lookup"><span data-stu-id="3fe45-144">Local PInvoke - involves invocation of a native unmanaged method that is embedded in the current managed module.</span></span>  
  
 <span data-ttu-id="3fe45-145">Ustawienia parametrów są podano w poniższej tabeli.</span><span class="sxs-lookup"><span data-stu-id="3fe45-145">The parameter settings are given in the following table.</span></span>  
  
|<span data-ttu-id="3fe45-146">Parametr</span><span class="sxs-lookup"><span data-stu-id="3fe45-146">Parameter</span></span>|<span data-ttu-id="3fe45-147">Wartości dla prawdy</span><span class="sxs-lookup"><span data-stu-id="3fe45-147">Values for true PInvoke</span></span>|<span data-ttu-id="3fe45-148">Wartości dla lokalnego elementu PInvoke</span><span class="sxs-lookup"><span data-stu-id="3fe45-148">Values for local PInvoke</span></span>|  
|---------------|-----------------------------|------------------------------|  
|`dwMethodFlags`||<span data-ttu-id="3fe45-149">Ustaw `mdStatic` ; Wyczyść `mdSynchronized` i `mdAbstract` .</span><span class="sxs-lookup"><span data-stu-id="3fe45-149">Set `mdStatic`; clear `mdSynchronized` and `mdAbstract`.</span></span>|  
|`pvSigBlob`|<span data-ttu-id="3fe45-150">Prawidłowy podpis metody środowiska uruchomieniowego języka wspólnego (CLR) z parametrami, które są prawidłowymi typami zarządzanymi.</span><span class="sxs-lookup"><span data-stu-id="3fe45-150">A valid common language runtime (CLR) method signature with parameters that are valid managed types.</span></span>|<span data-ttu-id="3fe45-151">Prawidłowy podpis metody CLR z parametrami, które są prawidłowymi typami zarządzanymi.</span><span class="sxs-lookup"><span data-stu-id="3fe45-151">A valid CLR method signature with parameters that are valid managed types.</span></span>|  
|`ulCodeRVA`||<span data-ttu-id="3fe45-152">0</span><span class="sxs-lookup"><span data-stu-id="3fe45-152">0</span></span>|  
|`dwImplFlags`|<span data-ttu-id="3fe45-153">Ustaw `miCil` i `miManaged` .</span><span class="sxs-lookup"><span data-stu-id="3fe45-153">Set `miCil` and `miManaged`.</span></span>|<span data-ttu-id="3fe45-154">Ustaw `miNative` i `miUnmanaged` .</span><span class="sxs-lookup"><span data-stu-id="3fe45-154">Set `miNative` and `miUnmanaged`.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="3fe45-155">Wymagania</span><span class="sxs-lookup"><span data-stu-id="3fe45-155">Requirements</span></span>  
 <span data-ttu-id="3fe45-156">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3fe45-156">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3fe45-157">**Nagłówek:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="3fe45-157">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="3fe45-158">**Biblioteka:** Używany jako zasób w bibliotece MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="3fe45-158">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="3fe45-159">**.NET Framework wersje:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3fe45-159">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3fe45-160">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="3fe45-160">See also</span></span>

- [<span data-ttu-id="3fe45-161">IMetaDataEmit — Interfejs</span><span class="sxs-lookup"><span data-stu-id="3fe45-161">IMetaDataEmit Interface</span></span>](imetadataemit-interface.md)
- [<span data-ttu-id="3fe45-162">IMetaDataEmit2, interfejs</span><span class="sxs-lookup"><span data-stu-id="3fe45-162">IMetaDataEmit2 Interface</span></span>](imetadataemit2-interface.md)
