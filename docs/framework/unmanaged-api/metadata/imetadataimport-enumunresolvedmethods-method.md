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
ms.openlocfilehash: 2009104d31723b9fed383b7bbb41146127d89bd0
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54611959"
---
# <a name="imetadataimportenumunresolvedmethods-method"></a><span data-ttu-id="68ae1-102">IMetaDataImport::EnumUnresolvedMethods — Metoda</span><span class="sxs-lookup"><span data-stu-id="68ae1-102">IMetaDataImport::EnumUnresolvedMethods Method</span></span>
<span data-ttu-id="68ae1-103">Wylicza tokenów MemberDef reprezentujący nierozwiązane metod w bieżącym zakresie metadanych.</span><span class="sxs-lookup"><span data-stu-id="68ae1-103">Enumerates MemberDef tokens representing the unresolved methods in the current metadata scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="68ae1-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="68ae1-104">Syntax</span></span>  
  
```  
HRESULT EnumUnresolvedMethods (  
   [in, out] HCORENUM    *phEnum,  
   [out]     mdToken     rMethods[],  
   [in]      ULONG       cMax,  
   [out]     ULONG       *pcTokens  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="68ae1-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="68ae1-105">Parameters</span></span>  
 `phEnum`  
 <span data-ttu-id="68ae1-106">[out w] Wskaźnik do modułu wyliczającego.</span><span class="sxs-lookup"><span data-stu-id="68ae1-106">[in, out] A pointer to the enumerator.</span></span> <span data-ttu-id="68ae1-107">Musi to być wartość NULL dla pierwszego wywołania tej metody.</span><span class="sxs-lookup"><span data-stu-id="68ae1-107">This must be NULL for the first call of this method.</span></span>  
  
 `rMethods`  
 <span data-ttu-id="68ae1-108">[out] Tablica do przechowywania tokenów MemberDef.</span><span class="sxs-lookup"><span data-stu-id="68ae1-108">[out] The array used to store the MemberDef tokens.</span></span>  
  
 `cMax`  
 <span data-ttu-id="68ae1-109">[in] Maksymalny rozmiar `rMethods` tablicy.</span><span class="sxs-lookup"><span data-stu-id="68ae1-109">[in] The maximum size of the `rMethods` array.</span></span>  
  
 `pcTokens`  
 <span data-ttu-id="68ae1-110">[out] Liczba tokenów MemberDef zwracane w `rMethods`.</span><span class="sxs-lookup"><span data-stu-id="68ae1-110">[out] The number of MemberDef tokens returned in `rMethods`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="68ae1-111">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="68ae1-111">Return Value</span></span>  
  
|<span data-ttu-id="68ae1-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="68ae1-112">HRESULT</span></span>|<span data-ttu-id="68ae1-113">Opis</span><span class="sxs-lookup"><span data-stu-id="68ae1-113">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="68ae1-114">`EnumUnresolvedMethods` pomyślnie zwrócił.</span><span class="sxs-lookup"><span data-stu-id="68ae1-114">`EnumUnresolvedMethods` returned successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="68ae1-115">Nie ma żadnych tokeny do wyliczenia.</span><span class="sxs-lookup"><span data-stu-id="68ae1-115">There are no tokens to enumerate.</span></span> <span data-ttu-id="68ae1-116">W takim przypadku `pcTokens` wynosi zero.</span><span class="sxs-lookup"><span data-stu-id="68ae1-116">In that case, `pcTokens` is zero.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="68ae1-117">Uwagi</span><span class="sxs-lookup"><span data-stu-id="68ae1-117">Remarks</span></span>  
 <span data-ttu-id="68ae1-118">Nierozpoznana metoda to taki, który został zadeklarowany, ale nie zaimplementowana.</span><span class="sxs-lookup"><span data-stu-id="68ae1-118">An unresolved method is one that has been declared but not implemented.</span></span> <span data-ttu-id="68ae1-119">Jeśli metoda jest oznaczona jako metoda znajduje się w wyliczeniu `miForwardRef` i `mdPinvokeImpl` lub `miRuntime` jest równa zero.</span><span class="sxs-lookup"><span data-stu-id="68ae1-119">A method is included in the enumeration if the method is marked `miForwardRef` and either `mdPinvokeImpl` or `miRuntime` is set to zero.</span></span> <span data-ttu-id="68ae1-120">Innymi słowy, Nierozpoznana metoda to metoda klasy, która jest oznaczona `miForwardRef` , ale który nie jest zaimplementowany w kodzie niezarządzanym (skontaktować za pośrednictwem funkcji PInvoke) ani implementowane wewnętrznie przez środowisko uruchomieniowe</span><span class="sxs-lookup"><span data-stu-id="68ae1-120">In other words, an unresolved method is a class method that is marked `miForwardRef` but which is not implemented in unmanaged code (reached via PInvoke) nor implemented internally by the runtime itself</span></span>  
  
 <span data-ttu-id="68ae1-121">Wyliczenia nie obejmuje wszystkich metod, które są zdefiniowane w zakresie modułu (globalne) lub interfejsy lub abstrakcyjne klasy.</span><span class="sxs-lookup"><span data-stu-id="68ae1-121">The enumeration excludes all methods that are defined either at module scope (globals) or in interfaces or abstract classes.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="68ae1-122">Wymagania</span><span class="sxs-lookup"><span data-stu-id="68ae1-122">Requirements</span></span>  
 <span data-ttu-id="68ae1-123">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="68ae1-123">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="68ae1-124">**Nagłówek:** COR.h</span><span class="sxs-lookup"><span data-stu-id="68ae1-124">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="68ae1-125">**Biblioteka:** Dołączony jako zasób w MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="68ae1-125">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="68ae1-126">**Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="68ae1-126">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="68ae1-127">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="68ae1-127">See also</span></span>
- [<span data-ttu-id="68ae1-128">IMetaDataImport, interfejs</span><span class="sxs-lookup"><span data-stu-id="68ae1-128">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [<span data-ttu-id="68ae1-129">IMetaDataImport2, interfejs</span><span class="sxs-lookup"><span data-stu-id="68ae1-129">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
