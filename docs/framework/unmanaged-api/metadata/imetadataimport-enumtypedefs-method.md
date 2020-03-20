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
ms.openlocfilehash: 2d6e86a7f5a93b900e79907f8ee0762869d7f737
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79177296"
---
# <a name="imetadataimportenumtypedefs-method"></a><span data-ttu-id="7e476-102">IMetaDataImport::EnumTypeDefs — Metoda</span><span class="sxs-lookup"><span data-stu-id="7e476-102">IMetaDataImport::EnumTypeDefs Method</span></span>
<span data-ttu-id="7e476-103">Wylicza tokeny TypeDef reprezentujące wszystkie typy w bieżącym zakresie.</span><span class="sxs-lookup"><span data-stu-id="7e476-103">Enumerates TypeDef tokens representing all types within the current scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7e476-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="7e476-104">Syntax</span></span>  
  
```cpp  
HRESULT EnumTypeDefs (  
   [out] HCORENUM   *phEnum,
   [in]  mdTypeDef  rTypeDefs[],  
   [in]  ULONG      cMax,
   [out] ULONG      *pcTypeDefs  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="7e476-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="7e476-105">Parameters</span></span>  
 `phEnum`  
 <span data-ttu-id="7e476-106">[na zewnątrz] Wskaźnik do nowego wyliczacza.</span><span class="sxs-lookup"><span data-stu-id="7e476-106">[out] A pointer to the new enumerator.</span></span> <span data-ttu-id="7e476-107">Musi to być null dla pierwszego wywołania tej metody.</span><span class="sxs-lookup"><span data-stu-id="7e476-107">This must be NULL for the first call of this method.</span></span>  
  
 `rTypeDefs`  
 <span data-ttu-id="7e476-108">[w] Tablica używana do przechowywania tokenów TypeDef.</span><span class="sxs-lookup"><span data-stu-id="7e476-108">[in] The array used to store the TypeDef tokens.</span></span>  
  
 `cMax`  
 <span data-ttu-id="7e476-109">[w] Maksymalny rozmiar `rTypeDefs` tablicy.</span><span class="sxs-lookup"><span data-stu-id="7e476-109">[in] The maximum size of the `rTypeDefs` array.</span></span>  
  
 `pcTypeDefs`  
 <span data-ttu-id="7e476-110">[na zewnątrz] Liczba tokenów TypeDef zwrócona w `rTypeDefs`.</span><span class="sxs-lookup"><span data-stu-id="7e476-110">[out] The number of TypeDef tokens returned in `rTypeDefs`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="7e476-111">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="7e476-111">Return Value</span></span>  
  
|<span data-ttu-id="7e476-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="7e476-112">HRESULT</span></span>|<span data-ttu-id="7e476-113">Opis</span><span class="sxs-lookup"><span data-stu-id="7e476-113">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="7e476-114">`EnumTypeDefs`zwrócono pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="7e476-114">`EnumTypeDefs` returned successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="7e476-115">Nie ma żadnych tokenów do wyliczenia.</span><span class="sxs-lookup"><span data-stu-id="7e476-115">There are no tokens to enumerate.</span></span> <span data-ttu-id="7e476-116">W takim `pcTypeDefs` przypadku wynosi zero.</span><span class="sxs-lookup"><span data-stu-id="7e476-116">In that case, `pcTypeDefs` is zero.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="7e476-117">Uwagi</span><span class="sxs-lookup"><span data-stu-id="7e476-117">Remarks</span></span>  
 <span data-ttu-id="7e476-118">TypeDef token reprezentuje typ, takich jak klasa lub interfejs, a także dowolny typ dodany za pośrednictwem mechanizmu rozszerzalności.</span><span class="sxs-lookup"><span data-stu-id="7e476-118">The TypeDef token represents a type such as a class or an interface, as well as any type added via an extensibility mechanism.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7e476-119">Wymagania</span><span class="sxs-lookup"><span data-stu-id="7e476-119">Requirements</span></span>  
 <span data-ttu-id="7e476-120">**Platformy:** Zobacz [Wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7e476-120">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7e476-121">**Nagłówek:** Okręg wyborczy Cor.h</span><span class="sxs-lookup"><span data-stu-id="7e476-121">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="7e476-122">**Biblioteka:** Uwzględnione jako zasób w pliku MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="7e476-122">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="7e476-123">**Wersje programu .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7e476-123">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7e476-124">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="7e476-124">See also</span></span>

- [<span data-ttu-id="7e476-125">IMetaDataImport — Interfejs</span><span class="sxs-lookup"><span data-stu-id="7e476-125">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [<span data-ttu-id="7e476-126">IMetaDataImport2, interfejs</span><span class="sxs-lookup"><span data-stu-id="7e476-126">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
