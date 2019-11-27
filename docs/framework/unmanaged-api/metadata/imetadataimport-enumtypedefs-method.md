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
ms.openlocfilehash: 3854cb4aa3d229c87466c0a35a72447ceb235624
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/23/2019
ms.locfileid: "74449992"
---
# <a name="imetadataimportenumtypedefs-method"></a><span data-ttu-id="bed46-102">IMetaDataImport::EnumTypeDefs — Metoda</span><span class="sxs-lookup"><span data-stu-id="bed46-102">IMetaDataImport::EnumTypeDefs Method</span></span>
<span data-ttu-id="bed46-103">Wylicza tokeny TypeDef reprezentujące wszystkie typy w bieżącym zakresie.</span><span class="sxs-lookup"><span data-stu-id="bed46-103">Enumerates TypeDef tokens representing all types within the current scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bed46-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="bed46-104">Syntax</span></span>  
  
```cpp  
HRESULT EnumTypeDefs (  
   [out] HCORENUM   *phEnum,   
   [in]  mdTypeDef  rTypeDefs[],  
   [in]  ULONG      cMax,   
   [out] ULONG      *pcTypeDefs  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="bed46-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="bed46-105">Parameters</span></span>  
 `phEnum`  
 <span data-ttu-id="bed46-106">określoną Wskaźnik do nowego modułu wyliczającego.</span><span class="sxs-lookup"><span data-stu-id="bed46-106">[out] A pointer to the new enumerator.</span></span> <span data-ttu-id="bed46-107">Musi ona mieć wartość NULL dla pierwszego wywołania tej metody.</span><span class="sxs-lookup"><span data-stu-id="bed46-107">This must be NULL for the first call of this method.</span></span>  
  
 `rTypeDefs`  
 <span data-ttu-id="bed46-108">podczas Tablica służąca do przechowywania tokenów TypeDef.</span><span class="sxs-lookup"><span data-stu-id="bed46-108">[in] The array used to store the TypeDef tokens.</span></span>  
  
 `cMax`  
 <span data-ttu-id="bed46-109">podczas Maksymalny rozmiar tablicy `rTypeDefs`.</span><span class="sxs-lookup"><span data-stu-id="bed46-109">[in] The maximum size of the `rTypeDefs` array.</span></span>  
  
 `pcTypeDefs`  
 <span data-ttu-id="bed46-110">określoną Liczba tokenów TypeDef zwróconych w `rTypeDefs`.</span><span class="sxs-lookup"><span data-stu-id="bed46-110">[out] The number of TypeDef tokens returned in `rTypeDefs`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="bed46-111">Wartość zwrócona</span><span class="sxs-lookup"><span data-stu-id="bed46-111">Return Value</span></span>  
  
|<span data-ttu-id="bed46-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="bed46-112">HRESULT</span></span>|<span data-ttu-id="bed46-113">Opis</span><span class="sxs-lookup"><span data-stu-id="bed46-113">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="bed46-114">`EnumTypeDefs` pomyślnie zwrócone.</span><span class="sxs-lookup"><span data-stu-id="bed46-114">`EnumTypeDefs` returned successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="bed46-115">Brak tokenów do wyliczenia.</span><span class="sxs-lookup"><span data-stu-id="bed46-115">There are no tokens to enumerate.</span></span> <span data-ttu-id="bed46-116">W takim przypadku `pcTypeDefs` wynosi zero.</span><span class="sxs-lookup"><span data-stu-id="bed46-116">In that case, `pcTypeDefs` is zero.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="bed46-117">Uwagi</span><span class="sxs-lookup"><span data-stu-id="bed46-117">Remarks</span></span>  
 <span data-ttu-id="bed46-118">Token TypeDef reprezentuje typ, taki jak Klasa lub interfejs, a także dowolny typ dodany za pomocą mechanizmu rozszerzalności.</span><span class="sxs-lookup"><span data-stu-id="bed46-118">The TypeDef token represents a type such as a class or an interface, as well as any type added via an extensibility mechanism.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="bed46-119">Wymagania</span><span class="sxs-lookup"><span data-stu-id="bed46-119">Requirements</span></span>  
 <span data-ttu-id="bed46-120">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="bed46-120">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="bed46-121">**Nagłówek:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="bed46-121">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="bed46-122">**Biblioteka:** Uwzględnione jako zasób w bibliotece MsCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="bed46-122">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="bed46-123">**Wersje .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="bed46-123">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bed46-124">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="bed46-124">See also</span></span>

- [<span data-ttu-id="bed46-125">IMetaDataImport, interfejs</span><span class="sxs-lookup"><span data-stu-id="bed46-125">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [<span data-ttu-id="bed46-126">IMetaDataImport2, interfejs</span><span class="sxs-lookup"><span data-stu-id="bed46-126">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
