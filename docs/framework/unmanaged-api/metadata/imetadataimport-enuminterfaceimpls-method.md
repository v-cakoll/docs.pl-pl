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
ms.openlocfilehash: 910c40413075131765a37e00703ac892e3f39641
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/08/2020
ms.locfileid: "84492229"
---
# <a name="imetadataimportenuminterfaceimpls-method"></a><span data-ttu-id="f4356-102">IMetaDataImport::EnumInterfaceImpls — Metoda</span><span class="sxs-lookup"><span data-stu-id="f4356-102">IMetaDataImport::EnumInterfaceImpls Method</span></span>
<span data-ttu-id="f4356-103">Wylicza wszystkie interfejsy zaimplementowane przez określony `TypeDef` .</span><span class="sxs-lookup"><span data-stu-id="f4356-103">Enumerates all interfaces implemented by the specified `TypeDef`.</span></span>
  
## <a name="syntax"></a><span data-ttu-id="f4356-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="f4356-104">Syntax</span></span>  
  
```cpp  
HRESULT EnumInterfaceImpls (  
   [in, out]  HCORENUM       *phEnum,
   [in]   mdTypeDef          td,  
   [out]  mdInterfaceImpl    rImpls[],
   [in]   ULONG              cMax,  
   [out]  ULONG*             pcImpls  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="f4356-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="f4356-105">Parameters</span></span>  
 `phEnum`  
 <span data-ttu-id="f4356-106">[in. out] Wskaźnik do modułu wyliczającego.</span><span class="sxs-lookup"><span data-stu-id="f4356-106">[in, out] A pointer to the enumerator.</span></span>  
  
 `td`  
 <span data-ttu-id="f4356-107">podczas Token elementu TypeDef, którego tokeny MethodDef reprezentują implementacje interfejsów, mają zostać wyliczone.</span><span class="sxs-lookup"><span data-stu-id="f4356-107">[in] The token of the TypeDef whose MethodDef tokens representing interface implementations are to be enumerated.</span></span>  
  
 `rImpls`  
 <span data-ttu-id="f4356-108">określoną Tablica służąca do przechowywania tokenów MethodDef.</span><span class="sxs-lookup"><span data-stu-id="f4356-108">[out] The array used to store the MethodDef tokens.</span></span>  
  
 `cMax`  
 <span data-ttu-id="f4356-109">podczas Maksymalna długość `rImpls` tablicy.</span><span class="sxs-lookup"><span data-stu-id="f4356-109">[in] The maximum length of the `rImpls` array.</span></span>  
  
 `pcImpls`  
 <span data-ttu-id="f4356-110">określoną Rzeczywista liczba tokenów zwrócona w `rImpls` .</span><span class="sxs-lookup"><span data-stu-id="f4356-110">[out] The actual number of tokens returned in `rImpls`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="f4356-111">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="f4356-111">Return Value</span></span>  
  
|<span data-ttu-id="f4356-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="f4356-112">HRESULT</span></span>|<span data-ttu-id="f4356-113">Opis</span><span class="sxs-lookup"><span data-stu-id="f4356-113">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="f4356-114">`EnumInterfaceImpls`pomyślnie zwrócono.</span><span class="sxs-lookup"><span data-stu-id="f4356-114">`EnumInterfaceImpls` returned successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="f4356-115">Brak tokenów MethodDef do wyliczenia.</span><span class="sxs-lookup"><span data-stu-id="f4356-115">There are no MethodDef tokens to enumerate.</span></span> <span data-ttu-id="f4356-116">W takim przypadku `pcImpls` jest ustawiona na zero.</span><span class="sxs-lookup"><span data-stu-id="f4356-116">In that case, `pcImpls` is set to zero.</span></span>|  

## <a name="remarks"></a><span data-ttu-id="f4356-117">Uwagi</span><span class="sxs-lookup"><span data-stu-id="f4356-117">Remarks</span></span>

<span data-ttu-id="f4356-118">Wyliczenie zwraca kolekcję `mdInterfaceImpl` tokenów dla każdego interfejsu zaimplementowanego przez określony `TypeDef` .</span><span class="sxs-lookup"><span data-stu-id="f4356-118">The enumeration returns a collection of `mdInterfaceImpl` tokens for each interface implemented by the specified `TypeDef`.</span></span> <span data-ttu-id="f4356-119">Tokeny interfejsu są zwracane w kolejności, w jakiej interfejsy zostały określone (za pomocą `DefineTypeDef` lub `SetTypeDefProps` ).</span><span class="sxs-lookup"><span data-stu-id="f4356-119">Interface tokens are returned in the order the interfaces were specified (through `DefineTypeDef` or `SetTypeDefProps`).</span></span> <span data-ttu-id="f4356-120">Do właściwości zwracanych `mdInterfaceImpl` tokenów można wykonywać zapytania przy użyciu [GetInterfaceImplProps —](imetadataimport-getinterfaceimplprops-method.md).</span><span class="sxs-lookup"><span data-stu-id="f4356-120">Properties of the returned `mdInterfaceImpl` tokens can be queried using [GetInterfaceImplProps](imetadataimport-getinterfaceimplprops-method.md).</span></span>
  
## <a name="requirements"></a><span data-ttu-id="f4356-121">Wymagania</span><span class="sxs-lookup"><span data-stu-id="f4356-121">Requirements</span></span>  
 <span data-ttu-id="f4356-122">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f4356-122">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f4356-123">**Nagłówek:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="f4356-123">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="f4356-124">**Biblioteka:** Uwzględnione jako zasób w bibliotece MsCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="f4356-124">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="f4356-125">**.NET Framework wersje:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f4356-125">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f4356-126">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="f4356-126">See also</span></span>

- [<span data-ttu-id="f4356-127">IMetaDataImport — Interfejs</span><span class="sxs-lookup"><span data-stu-id="f4356-127">IMetaDataImport Interface</span></span>](imetadataimport-interface.md)
- [<span data-ttu-id="f4356-128">IMetaDataImport2, interfejs</span><span class="sxs-lookup"><span data-stu-id="f4356-128">IMetaDataImport2 Interface</span></span>](imetadataimport2-interface.md)
