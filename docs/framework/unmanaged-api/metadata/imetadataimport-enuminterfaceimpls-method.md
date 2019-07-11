---
title: IMetaDataImport::EnumInterfaceImpls — Metoda
ms.date: 03/30/2017
api_name:
- IMetaDataImport.EnumInterfaceImpls
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::EnumInterfaceImpls
helpviewer_keywords:
- IMetaDataImport::EnumInterfaceImpls method [.NET Framework metadata]
- EnumInterfaceImpls method [.NET Framework metadata]
ms.assetid: ba6e178f-128b-4e47-a13c-b4be73eb106c
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 0d0f94949cdc82cdecd52f003f3400c43014fabf
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/10/2019
ms.locfileid: "67780463"
---
# <a name="imetadataimportenuminterfaceimpls-method"></a><span data-ttu-id="bc409-102">IMetaDataImport::EnumInterfaceImpls — Metoda</span><span class="sxs-lookup"><span data-stu-id="bc409-102">IMetaDataImport::EnumInterfaceImpls Method</span></span>
<span data-ttu-id="bc409-103">Wylicza wszystkie interfejsy implementowane przez określony `TypeDef`.</span><span class="sxs-lookup"><span data-stu-id="bc409-103">Enumerates all interfaces implemented by the specified `TypeDef`.</span></span> 
  
## <a name="syntax"></a><span data-ttu-id="bc409-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="bc409-104">Syntax</span></span>  
  
```cpp  
HRESULT EnumInterfaceImpls (  
   [in, out]  HCORENUM       *phEnum,   
   [in]   mdTypeDef          td,  
   [out]  mdInterfaceImpl    rImpls[],   
   [in]   ULONG              cMax,  
   [out]  ULONG*             pcImpls  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="bc409-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="bc409-105">Parameters</span></span>  
 `phEnum`  
 <span data-ttu-id="bc409-106">[out w] Wskaźnik do modułu wyliczającego.</span><span class="sxs-lookup"><span data-stu-id="bc409-106">[in, out] A pointer to the enumerator.</span></span>  
  
 `td`  
 <span data-ttu-id="bc409-107">[in] Token TypeDef, w których tokeny MethodDef reprezentujący implementacje interfejsu są do wyliczenia.</span><span class="sxs-lookup"><span data-stu-id="bc409-107">[in] The token of the TypeDef whose MethodDef tokens representing interface implementations are to be enumerated.</span></span>  
  
 `rImpls`  
 <span data-ttu-id="bc409-108">[out] Tablica do przechowywania tokenów MethodDef.</span><span class="sxs-lookup"><span data-stu-id="bc409-108">[out] The array used to store the MethodDef tokens.</span></span>  
  
 `cMax`  
 <span data-ttu-id="bc409-109">[in] Maksymalny rozmiar `rImpls` tablicy.</span><span class="sxs-lookup"><span data-stu-id="bc409-109">[in] The maximum size of the `rImpls` array.</span></span>  
  
 `pcImpls`  
 <span data-ttu-id="bc409-110">[out] Rzeczywista liczba zwracane w tokenach `rImpls`.</span><span class="sxs-lookup"><span data-stu-id="bc409-110">[out] The actual number of tokens returned in `rImpls`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="bc409-111">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="bc409-111">Return Value</span></span>  
  
|<span data-ttu-id="bc409-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="bc409-112">HRESULT</span></span>|<span data-ttu-id="bc409-113">Opis</span><span class="sxs-lookup"><span data-stu-id="bc409-113">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="bc409-114">`EnumInterfaceImpls` pomyślnie zwrócił.</span><span class="sxs-lookup"><span data-stu-id="bc409-114">`EnumInterfaceImpls` returned successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="bc409-115">Nie ma żadnych tokeny MethodDef do wyliczenia.</span><span class="sxs-lookup"><span data-stu-id="bc409-115">There are no MethodDef tokens to enumerate.</span></span> <span data-ttu-id="bc409-116">W takim przypadku `pcImpls` jest równa zero.</span><span class="sxs-lookup"><span data-stu-id="bc409-116">In that case, `pcImpls` is set to zero.</span></span>|  

## <a name="remarks"></a><span data-ttu-id="bc409-117">Uwagi</span><span class="sxs-lookup"><span data-stu-id="bc409-117">Remarks</span></span>

<span data-ttu-id="bc409-118">Wyliczanie zwraca kolekcję `mdInterfaceImpl` tokenów dla każdego interfejsu implementowany przez określony `TypeDef`.</span><span class="sxs-lookup"><span data-stu-id="bc409-118">The enumeration returns a collection of `mdInterfaceImpl` tokens for each interface implemented by the specified `TypeDef`.</span></span> <span data-ttu-id="bc409-119">Tokeny interfejsu są zwracane w porządku, o których określono interfejsy (za pośrednictwem `DefineTypeDef` lub `SetTypeDefProps`).</span><span class="sxs-lookup"><span data-stu-id="bc409-119">Interface tokens are returned in the order the interfaces were specified (through `DefineTypeDef` or `SetTypeDefProps`).</span></span> <span data-ttu-id="bc409-120">Właściwości zwracanego `mdInterfaceImpl` tokeny mogą być przeszukiwane przy użyciu [GetInterfaceImplProps](imetadataimport-getinterfaceimplprops-method.md).</span><span class="sxs-lookup"><span data-stu-id="bc409-120">Properties of the returned `mdInterfaceImpl` tokens can be queried using [GetInterfaceImplProps](imetadataimport-getinterfaceimplprops-method.md).</span></span>
  
## <a name="requirements"></a><span data-ttu-id="bc409-121">Wymagania</span><span class="sxs-lookup"><span data-stu-id="bc409-121">Requirements</span></span>  
 <span data-ttu-id="bc409-122">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="bc409-122">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="bc409-123">**Nagłówek:** COR.h</span><span class="sxs-lookup"><span data-stu-id="bc409-123">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="bc409-124">**Biblioteka:** Dołączony jako zasób w MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="bc409-124">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="bc409-125">**Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="bc409-125">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bc409-126">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="bc409-126">See also</span></span>

- [<span data-ttu-id="bc409-127">IMetaDataImport, interfejs</span><span class="sxs-lookup"><span data-stu-id="bc409-127">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [<span data-ttu-id="bc409-128">IMetaDataImport2, interfejs</span><span class="sxs-lookup"><span data-stu-id="bc409-128">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
