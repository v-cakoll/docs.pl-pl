---
title: IMetaDataImport::EnumTypeDefs — Metoda
ms.date: 03/30/2017
api_name:
- IMetaDataImport.EnumTypeDefs
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::EnumTypeDefs
helpviewer_keywords:
- EnumTypeDefs method [.NET Framework metadata]
- IMetaDataImport::EnumTypeDefs method [.NET Framework metadata]
ms.assetid: 4e508711-da92-4381-aaf8-6803075cdaa2
topic_type:
- apiref
ms.openlocfilehash: cdfd4e10236d546af2555b125d44233172849a21
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/08/2020
ms.locfileid: "84503734"
---
# <a name="imetadataimportenumtypedefs-method"></a><span data-ttu-id="5b2c8-102">IMetaDataImport::EnumTypeDefs — Metoda</span><span class="sxs-lookup"><span data-stu-id="5b2c8-102">IMetaDataImport::EnumTypeDefs Method</span></span>
<span data-ttu-id="5b2c8-103">Wylicza tokeny TypeDef reprezentujące wszystkie typy w bieżącym zakresie.</span><span class="sxs-lookup"><span data-stu-id="5b2c8-103">Enumerates TypeDef tokens representing all types within the current scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5b2c8-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="5b2c8-104">Syntax</span></span>  
  
```cpp  
HRESULT EnumTypeDefs (  
   [out] HCORENUM   *phEnum,
   [in]  mdTypeDef  rTypeDefs[],  
   [in]  ULONG      cMax,
   [out] ULONG      *pcTypeDefs  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="5b2c8-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="5b2c8-105">Parameters</span></span>  
 `phEnum`  
 <span data-ttu-id="5b2c8-106">określoną Wskaźnik do nowego modułu wyliczającego.</span><span class="sxs-lookup"><span data-stu-id="5b2c8-106">[out] A pointer to the new enumerator.</span></span> <span data-ttu-id="5b2c8-107">Musi ona mieć wartość NULL dla pierwszego wywołania tej metody.</span><span class="sxs-lookup"><span data-stu-id="5b2c8-107">This must be NULL for the first call of this method.</span></span>  
  
 `rTypeDefs`  
 <span data-ttu-id="5b2c8-108">podczas Tablica służąca do przechowywania tokenów TypeDef.</span><span class="sxs-lookup"><span data-stu-id="5b2c8-108">[in] The array used to store the TypeDef tokens.</span></span>  
  
 `cMax`  
 <span data-ttu-id="5b2c8-109">podczas Maksymalny rozmiar `rTypeDefs` tablicy.</span><span class="sxs-lookup"><span data-stu-id="5b2c8-109">[in] The maximum size of the `rTypeDefs` array.</span></span>  
  
 `pcTypeDefs`  
 <span data-ttu-id="5b2c8-110">określoną Liczba tokenów TypeDef zwróconych w `rTypeDefs` .</span><span class="sxs-lookup"><span data-stu-id="5b2c8-110">[out] The number of TypeDef tokens returned in `rTypeDefs`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="5b2c8-111">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="5b2c8-111">Return Value</span></span>  
  
|<span data-ttu-id="5b2c8-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="5b2c8-112">HRESULT</span></span>|<span data-ttu-id="5b2c8-113">Opis</span><span class="sxs-lookup"><span data-stu-id="5b2c8-113">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="5b2c8-114">`EnumTypeDefs`pomyślnie zwrócono.</span><span class="sxs-lookup"><span data-stu-id="5b2c8-114">`EnumTypeDefs` returned successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="5b2c8-115">Brak tokenów do wyliczenia.</span><span class="sxs-lookup"><span data-stu-id="5b2c8-115">There are no tokens to enumerate.</span></span> <span data-ttu-id="5b2c8-116">W takim przypadku `pcTypeDefs` jest równa zero.</span><span class="sxs-lookup"><span data-stu-id="5b2c8-116">In that case, `pcTypeDefs` is zero.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="5b2c8-117">Uwagi</span><span class="sxs-lookup"><span data-stu-id="5b2c8-117">Remarks</span></span>  
 <span data-ttu-id="5b2c8-118">Token TypeDef reprezentuje typ, taki jak Klasa lub interfejs, a także dowolny typ dodany za pomocą mechanizmu rozszerzalności.</span><span class="sxs-lookup"><span data-stu-id="5b2c8-118">The TypeDef token represents a type such as a class or an interface, as well as any type added via an extensibility mechanism.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5b2c8-119">Wymagania</span><span class="sxs-lookup"><span data-stu-id="5b2c8-119">Requirements</span></span>  
 <span data-ttu-id="5b2c8-120">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5b2c8-120">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5b2c8-121">**Nagłówek:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="5b2c8-121">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="5b2c8-122">**Biblioteka:** Uwzględnione jako zasób w bibliotece MsCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="5b2c8-122">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="5b2c8-123">**.NET Framework wersje:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5b2c8-123">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5b2c8-124">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="5b2c8-124">See also</span></span>

- [<span data-ttu-id="5b2c8-125">IMetaDataImport — Interfejs</span><span class="sxs-lookup"><span data-stu-id="5b2c8-125">IMetaDataImport Interface</span></span>](imetadataimport-interface.md)
- [<span data-ttu-id="5b2c8-126">IMetaDataImport2, interfejs</span><span class="sxs-lookup"><span data-stu-id="5b2c8-126">IMetaDataImport2 Interface</span></span>](imetadataimport2-interface.md)
