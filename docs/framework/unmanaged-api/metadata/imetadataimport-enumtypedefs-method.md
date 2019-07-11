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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 621582536c07b269dd723c9014e23c50e561957a
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/10/2019
ms.locfileid: "67774615"
---
# <a name="imetadataimportenumtypedefs-method"></a><span data-ttu-id="1c782-102">IMetaDataImport::EnumTypeDefs — Metoda</span><span class="sxs-lookup"><span data-stu-id="1c782-102">IMetaDataImport::EnumTypeDefs Method</span></span>
<span data-ttu-id="1c782-103">Wylicza tokenów TypeDef reprezentujący wszystkie typy w bieżącym zakresie.</span><span class="sxs-lookup"><span data-stu-id="1c782-103">Enumerates TypeDef tokens representing all types within the current scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1c782-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="1c782-104">Syntax</span></span>  
  
```cpp  
HRESULT EnumTypeDefs (  
   [out] HCORENUM   *phEnum,   
   [in]  mdTypeDef  rTypeDefs[],  
   [in]  ULONG      cMax,   
   [out] ULONG      *pcTypeDefs  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="1c782-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="1c782-105">Parameters</span></span>  
 `phEnum`  
 <span data-ttu-id="1c782-106">[out] Wskaźnik do nowego modułu wyliczającego.</span><span class="sxs-lookup"><span data-stu-id="1c782-106">[out] A pointer to the new enumerator.</span></span> <span data-ttu-id="1c782-107">Musi to być wartość NULL dla pierwszego wywołania tej metody.</span><span class="sxs-lookup"><span data-stu-id="1c782-107">This must be NULL for the first call of this method.</span></span>  
  
 `rTypeDefs`  
 <span data-ttu-id="1c782-108">[in] Tablica do przechowywania tokenów — TypeDef.</span><span class="sxs-lookup"><span data-stu-id="1c782-108">[in] The array used to store the TypeDef tokens.</span></span>  
  
 `cMax`  
 <span data-ttu-id="1c782-109">[in] Maksymalny rozmiar `rTypeDefs` tablicy.</span><span class="sxs-lookup"><span data-stu-id="1c782-109">[in] The maximum size of the `rTypeDefs` array.</span></span>  
  
 `pcTypeDefs`  
 <span data-ttu-id="1c782-110">[out] Liczba tokenów TypeDef zwracane w `rTypeDefs`.</span><span class="sxs-lookup"><span data-stu-id="1c782-110">[out] The number of TypeDef tokens returned in `rTypeDefs`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="1c782-111">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="1c782-111">Return Value</span></span>  
  
|<span data-ttu-id="1c782-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="1c782-112">HRESULT</span></span>|<span data-ttu-id="1c782-113">Opis</span><span class="sxs-lookup"><span data-stu-id="1c782-113">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="1c782-114">`EnumTypeDefs` pomyślnie zwrócił.</span><span class="sxs-lookup"><span data-stu-id="1c782-114">`EnumTypeDefs` returned successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="1c782-115">Nie ma żadnych tokeny do wyliczenia.</span><span class="sxs-lookup"><span data-stu-id="1c782-115">There are no tokens to enumerate.</span></span> <span data-ttu-id="1c782-116">W takim przypadku `pcTypeDefs` wynosi zero.</span><span class="sxs-lookup"><span data-stu-id="1c782-116">In that case, `pcTypeDefs` is zero.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="1c782-117">Uwagi</span><span class="sxs-lookup"><span data-stu-id="1c782-117">Remarks</span></span>  
 <span data-ttu-id="1c782-118">TypeDef token reprezentuje typ, takich jak klasy lub interfejsu, a także dowolnego typu dodane za pośrednictwem mechanizmu rozszerzalności.</span><span class="sxs-lookup"><span data-stu-id="1c782-118">The TypeDef token represents a type such as a class or an interface, as well as any type added via an extensibility mechanism.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1c782-119">Wymagania</span><span class="sxs-lookup"><span data-stu-id="1c782-119">Requirements</span></span>  
 <span data-ttu-id="1c782-120">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1c782-120">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1c782-121">**Nagłówek:** COR.h</span><span class="sxs-lookup"><span data-stu-id="1c782-121">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="1c782-122">**Biblioteka:** Dołączony jako zasób w MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="1c782-122">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="1c782-123">**Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1c782-123">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1c782-124">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="1c782-124">See also</span></span>

- [<span data-ttu-id="1c782-125">IMetaDataImport, interfejs</span><span class="sxs-lookup"><span data-stu-id="1c782-125">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [<span data-ttu-id="1c782-126">IMetaDataImport2, interfejs</span><span class="sxs-lookup"><span data-stu-id="1c782-126">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
