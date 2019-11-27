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
ms.openlocfilehash: ff9827174e43fd62f3a995e9f477c6fff66b227a
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/23/2019
ms.locfileid: "74449954"
---
# <a name="imetadataimportenumunresolvedmethods-method"></a><span data-ttu-id="84474-102">IMetaDataImport::EnumUnresolvedMethods — Metoda</span><span class="sxs-lookup"><span data-stu-id="84474-102">IMetaDataImport::EnumUnresolvedMethods Method</span></span>
<span data-ttu-id="84474-103">Wylicza tokeny MemberDef reprezentujące nierozpoznane metody w bieżącym zakresie metadanych.</span><span class="sxs-lookup"><span data-stu-id="84474-103">Enumerates MemberDef tokens representing the unresolved methods in the current metadata scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="84474-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="84474-104">Syntax</span></span>  
  
```cpp  
HRESULT EnumUnresolvedMethods (  
   [in, out] HCORENUM    *phEnum,  
   [out]     mdToken     rMethods[],  
   [in]      ULONG       cMax,  
   [out]     ULONG       *pcTokens  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="84474-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="84474-105">Parameters</span></span>  
 `phEnum`  
 <span data-ttu-id="84474-106">[in. out] Wskaźnik do modułu wyliczającego.</span><span class="sxs-lookup"><span data-stu-id="84474-106">[in, out] A pointer to the enumerator.</span></span> <span data-ttu-id="84474-107">Musi ona mieć wartość NULL dla pierwszego wywołania tej metody.</span><span class="sxs-lookup"><span data-stu-id="84474-107">This must be NULL for the first call of this method.</span></span>  
  
 `rMethods`  
 <span data-ttu-id="84474-108">określoną Tablica służąca do przechowywania tokenów MemberDef.</span><span class="sxs-lookup"><span data-stu-id="84474-108">[out] The array used to store the MemberDef tokens.</span></span>  
  
 `cMax`  
 <span data-ttu-id="84474-109">podczas Maksymalny rozmiar tablicy `rMethods`.</span><span class="sxs-lookup"><span data-stu-id="84474-109">[in] The maximum size of the `rMethods` array.</span></span>  
  
 `pcTokens`  
 <span data-ttu-id="84474-110">określoną Liczba tokenów MemberDef zwróconych w `rMethods`.</span><span class="sxs-lookup"><span data-stu-id="84474-110">[out] The number of MemberDef tokens returned in `rMethods`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="84474-111">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="84474-111">Return Value</span></span>  
  
|<span data-ttu-id="84474-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="84474-112">HRESULT</span></span>|<span data-ttu-id="84474-113">Opis</span><span class="sxs-lookup"><span data-stu-id="84474-113">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="84474-114">`EnumUnresolvedMethods` pomyślnie zwrócone.</span><span class="sxs-lookup"><span data-stu-id="84474-114">`EnumUnresolvedMethods` returned successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="84474-115">Brak tokenów do wyliczenia.</span><span class="sxs-lookup"><span data-stu-id="84474-115">There are no tokens to enumerate.</span></span> <span data-ttu-id="84474-116">W takim przypadku `pcTokens` wynosi zero.</span><span class="sxs-lookup"><span data-stu-id="84474-116">In that case, `pcTokens` is zero.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="84474-117">Uwagi</span><span class="sxs-lookup"><span data-stu-id="84474-117">Remarks</span></span>  
 <span data-ttu-id="84474-118">Nierozpoznana Metoda jest taka, która została zadeklarowana, ale nie została zaimplementowana.</span><span class="sxs-lookup"><span data-stu-id="84474-118">An unresolved method is one that has been declared but not implemented.</span></span> <span data-ttu-id="84474-119">Metoda jest uwzględniona w wyliczeniu, jeśli metoda jest oznaczona `miForwardRef` i `mdPinvokeImpl` albo `miRuntime` jest ustawiona na zero.</span><span class="sxs-lookup"><span data-stu-id="84474-119">A method is included in the enumeration if the method is marked `miForwardRef` and either `mdPinvokeImpl` or `miRuntime` is set to zero.</span></span> <span data-ttu-id="84474-120">Innymi słowy, Nierozpoznana Metoda jest metodą klasy, która jest oznaczona `miForwardRef`, ale która nie jest zaimplementowana w kodzie niezarządzanym (osiągane za pośrednictwem PInvoke) ani nie została zaimplementowana wewnętrznie przez samo środowisko uruchomieniowe</span><span class="sxs-lookup"><span data-stu-id="84474-120">In other words, an unresolved method is a class method that is marked `miForwardRef` but which is not implemented in unmanaged code (reached via PInvoke) nor implemented internally by the runtime itself</span></span>  
  
 <span data-ttu-id="84474-121">Wyliczenie wyklucza wszystkie metody, które są zdefiniowane w zakresie modułu (Globals) lub w klasach interfejsów lub klas abstrakcyjnych.</span><span class="sxs-lookup"><span data-stu-id="84474-121">The enumeration excludes all methods that are defined either at module scope (globals) or in interfaces or abstract classes.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="84474-122">Wymagania</span><span class="sxs-lookup"><span data-stu-id="84474-122">Requirements</span></span>  
 <span data-ttu-id="84474-123">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="84474-123">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="84474-124">**Nagłówek:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="84474-124">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="84474-125">**Biblioteka:** Uwzględnione jako zasób w bibliotece MsCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="84474-125">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="84474-126">**Wersje .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="84474-126">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="84474-127">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="84474-127">See also</span></span>

- [<span data-ttu-id="84474-128">IMetaDataImport, interfejs</span><span class="sxs-lookup"><span data-stu-id="84474-128">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [<span data-ttu-id="84474-129">IMetaDataImport2, interfejs</span><span class="sxs-lookup"><span data-stu-id="84474-129">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
