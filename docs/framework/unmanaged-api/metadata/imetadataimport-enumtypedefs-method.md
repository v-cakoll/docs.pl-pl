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
ms.openlocfilehash: 53ed486a885514d02bf2be9c473e102c2c5f0e15
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33446846"
---
# <a name="imetadataimportenumtypedefs-method"></a><span data-ttu-id="cfceb-102">IMetaDataImport::EnumTypeDefs — Metoda</span><span class="sxs-lookup"><span data-stu-id="cfceb-102">IMetaDataImport::EnumTypeDefs Method</span></span>
<span data-ttu-id="cfceb-103">Wylicza tokeny TypeDef reprezentujący wszystkie typy w bieżącym zakresie.</span><span class="sxs-lookup"><span data-stu-id="cfceb-103">Enumerates TypeDef tokens representing all types within the current scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cfceb-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="cfceb-104">Syntax</span></span>  
  
```  
HRESULT EnumTypeDefs (  
   [out] HCORENUM   *phEnum,   
   [in]  mdTypeDef  rTypeDefs[],  
   [in]  ULONG      cMax,   
   [out] ULONG      *pcTypeDefs  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="cfceb-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="cfceb-105">Parameters</span></span>  
 `phEnum`  
 <span data-ttu-id="cfceb-106">[out] Wskaźnik do nowego modułu wyliczającego.</span><span class="sxs-lookup"><span data-stu-id="cfceb-106">[out] A pointer to the new enumerator.</span></span> <span data-ttu-id="cfceb-107">Musi to być wartość NULL dla pierwsze wywołanie tej metody.</span><span class="sxs-lookup"><span data-stu-id="cfceb-107">This must be NULL for the first call of this method.</span></span>  
  
 `rTypeDefs`  
 <span data-ttu-id="cfceb-108">[in] Tablica używany do przechowywania tokenów TypeDef.</span><span class="sxs-lookup"><span data-stu-id="cfceb-108">[in] The array used to store the TypeDef tokens.</span></span>  
  
 `cMax`  
 <span data-ttu-id="cfceb-109">[in] Maksymalny rozmiar `rTypeDefs` tablicy.</span><span class="sxs-lookup"><span data-stu-id="cfceb-109">[in] The maximum size of the `rTypeDefs` array.</span></span>  
  
 `pcTypeDefs`  
 <span data-ttu-id="cfceb-110">[out] Liczba tokenów TypeDef zwracane w `rTypeDefs`.</span><span class="sxs-lookup"><span data-stu-id="cfceb-110">[out] The number of TypeDef tokens returned in `rTypeDefs`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="cfceb-111">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="cfceb-111">Return Value</span></span>  
  
|<span data-ttu-id="cfceb-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="cfceb-112">HRESULT</span></span>|<span data-ttu-id="cfceb-113">Opis</span><span class="sxs-lookup"><span data-stu-id="cfceb-113">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="cfceb-114">`EnumTypeDefs` zwrócona pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="cfceb-114">`EnumTypeDefs` returned successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="cfceb-115">Nie ma żadnych tokenów do wyliczenia.</span><span class="sxs-lookup"><span data-stu-id="cfceb-115">There are no tokens to enumerate.</span></span> <span data-ttu-id="cfceb-116">W takim przypadku `pcTypeDefs` wynosi zero.</span><span class="sxs-lookup"><span data-stu-id="cfceb-116">In that case, `pcTypeDefs` is zero.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="cfceb-117">Uwagi</span><span class="sxs-lookup"><span data-stu-id="cfceb-117">Remarks</span></span>  
 <span data-ttu-id="cfceb-118">TypeDef token reprezentuje typ, takich jak klasy lub interfejsu, jak również żadnego typu dodane za pośrednictwem mechanizm rozszerzalności.</span><span class="sxs-lookup"><span data-stu-id="cfceb-118">The TypeDef token represents a type such as a class or an interface, as well as any type added via an extensibility mechanism.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="cfceb-119">Wymagania</span><span class="sxs-lookup"><span data-stu-id="cfceb-119">Requirements</span></span>  
 <span data-ttu-id="cfceb-120">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="cfceb-120">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="cfceb-121">**Nagłówek:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="cfceb-121">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="cfceb-122">**Biblioteka:** uwzględnione jako zasób w MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="cfceb-122">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="cfceb-123">**Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="cfceb-123">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cfceb-124">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="cfceb-124">See Also</span></span>  
 [<span data-ttu-id="cfceb-125">IMetaDataImport, interfejs</span><span class="sxs-lookup"><span data-stu-id="cfceb-125">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)  
 [<span data-ttu-id="cfceb-126">IMetaDataImport2, interfejs</span><span class="sxs-lookup"><span data-stu-id="cfceb-126">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
