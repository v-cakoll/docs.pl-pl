---
title: IMetaDataImport::EnumMethodsWithName — Metoda
ms.date: 03/30/2017
api_name:
- IMetaDataImport.EnumMethodsWithName
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::EnumMethodsWithName
helpviewer_keywords:
- IMetaDataImport::EnumMethodsWithName method [.NET Framework metadata]
- EnumMethodsWithName method [.NET Framework metadata]
ms.assetid: a8624913-2e23-46ad-a0c1-bb8eccbbf20f
topic_type:
- apiref
ms.openlocfilehash: 66a09baea1df2e2de418bdce8821672802f1f51f
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/08/2020
ms.locfileid: "84491736"
---
# <a name="imetadataimportenummethodswithname-method"></a><span data-ttu-id="89c9b-102">IMetaDataImport::EnumMethodsWithName — Metoda</span><span class="sxs-lookup"><span data-stu-id="89c9b-102">IMetaDataImport::EnumMethodsWithName Method</span></span>
<span data-ttu-id="89c9b-103">Wylicza metody, które mają określoną nazwę i które są definiowane przez typ, do którego odwołuje się określony token TypeDef.</span><span class="sxs-lookup"><span data-stu-id="89c9b-103">Enumerates methods that have the specified name and that are defined by the type referenced by the specified TypeDef token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="89c9b-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="89c9b-104">Syntax</span></span>  
  
```cpp  
HRESULT EnumMethodsWithName (  
   [in, out] HCORENUM    *phEnum,  
   [in]  mdTypeDef       cl,  
   [in]  LPCWSTR         szName,  
   [out] mdMethodDef     rMethods[],  
   [in]  ULONG           cMax,  
   [out] ULONG           *pcTokens  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="89c9b-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="89c9b-105">Parameters</span></span>  
 `phEnum`  
 <span data-ttu-id="89c9b-106">[in. out] Wskaźnik do modułu wyliczającego.</span><span class="sxs-lookup"><span data-stu-id="89c9b-106">[in, out] A pointer to the enumerator.</span></span> <span data-ttu-id="89c9b-107">Musi ona mieć wartość NULL dla pierwszego wywołania tej metody.</span><span class="sxs-lookup"><span data-stu-id="89c9b-107">This must be NULL for the first call of this method.</span></span>  
  
 `cl`  
 <span data-ttu-id="89c9b-108">podczas Token TypeDef reprezentujący typ, którego metody mają zostać wyliczone.</span><span class="sxs-lookup"><span data-stu-id="89c9b-108">[in] A TypeDef token representing the type whose methods to enumerate.</span></span>  
  
 `szName`  
 <span data-ttu-id="89c9b-109">podczas Nazwa, która ogranicza zakres wyliczania.</span><span class="sxs-lookup"><span data-stu-id="89c9b-109">[in] The name that limits the scope of the enumeration.</span></span>  
  
 `rMethods`  
 <span data-ttu-id="89c9b-110">określoną Tablica służąca do przechowywania tokenów MethodDef.</span><span class="sxs-lookup"><span data-stu-id="89c9b-110">[out] The array used to store the MethodDef tokens.</span></span>  
  
 `cMax`  
 <span data-ttu-id="89c9b-111">podczas Maksymalny rozmiar `rMethods` tablicy.</span><span class="sxs-lookup"><span data-stu-id="89c9b-111">[in] The maximum size of the `rMethods` array.</span></span>  
  
 `pcTokens`  
 <span data-ttu-id="89c9b-112">określoną Liczba tokenów MethodDef zwróconych w `rMethods` .</span><span class="sxs-lookup"><span data-stu-id="89c9b-112">[out] The number of MethodDef tokens returned in `rMethods`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="89c9b-113">Uwagi</span><span class="sxs-lookup"><span data-stu-id="89c9b-113">Remarks</span></span>  
 <span data-ttu-id="89c9b-114">Ta metoda wylicza pola i metody, ale nie właściwości ani zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="89c9b-114">This method enumerates fields and methods, but not properties or events.</span></span> <span data-ttu-id="89c9b-115">W przeciwieństwie do [IMetaDataImport:: EnumMethods —](imetadataimport-enummethods-method.md), `EnumMethodsWithName` odrzuca wszystkie tokeny metody, które nie mają określonej nazwy.</span><span class="sxs-lookup"><span data-stu-id="89c9b-115">Unlike [IMetaDataImport::EnumMethods](imetadataimport-enummethods-method.md), `EnumMethodsWithName` discards all method tokens that do not have the specified name.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="89c9b-116">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="89c9b-116">Return Value</span></span>  
  
|<span data-ttu-id="89c9b-117">HRESULT</span><span class="sxs-lookup"><span data-stu-id="89c9b-117">HRESULT</span></span>|<span data-ttu-id="89c9b-118">Opis</span><span class="sxs-lookup"><span data-stu-id="89c9b-118">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="89c9b-119">`EnumMethodsWithName`pomyślnie zwrócono.</span><span class="sxs-lookup"><span data-stu-id="89c9b-119">`EnumMethodsWithName` returned successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="89c9b-120">Brak tokenów do wyliczenia.</span><span class="sxs-lookup"><span data-stu-id="89c9b-120">There are no tokens to enumerate.</span></span> <span data-ttu-id="89c9b-121">W takim przypadku `pcTokens` jest równa zero.</span><span class="sxs-lookup"><span data-stu-id="89c9b-121">In that case, `pcTokens` is zero.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="89c9b-122">Wymagania</span><span class="sxs-lookup"><span data-stu-id="89c9b-122">Requirements</span></span>  
 <span data-ttu-id="89c9b-123">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="89c9b-123">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="89c9b-124">**Nagłówek:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="89c9b-124">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="89c9b-125">**Biblioteka:** Uwzględnione jako zasób w bibliotece MsCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="89c9b-125">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="89c9b-126">**.NET Framework wersje:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="89c9b-126">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="89c9b-127">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="89c9b-127">See also</span></span>

- [<span data-ttu-id="89c9b-128">IMetaDataImport — Interfejs</span><span class="sxs-lookup"><span data-stu-id="89c9b-128">IMetaDataImport Interface</span></span>](imetadataimport-interface.md)
- [<span data-ttu-id="89c9b-129">IMetaDataImport2, interfejs</span><span class="sxs-lookup"><span data-stu-id="89c9b-129">IMetaDataImport2 Interface</span></span>](imetadataimport2-interface.md)
