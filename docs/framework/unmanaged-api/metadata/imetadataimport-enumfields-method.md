---
title: IMetaDataImport::EnumFields — Metoda
ms.date: 03/30/2017
api_name:
- IMetaDataImport.EnumFields
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::EnumFields
helpviewer_keywords:
- EnumFields method [.NET Framework metadata]
- IMetaDataImport::EnumFields method [.NET Framework metadata]
ms.assetid: 1d23247e-c58c-45db-afd8-83aa89cde18e
topic_type:
- apiref
ms.openlocfilehash: 2d32dc8ae59fc1a4a189d849437cc95ea3b94a4d
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/23/2019
ms.locfileid: "74449540"
---
# <a name="imetadataimportenumfields-method"></a><span data-ttu-id="8f611-102">IMetaDataImport::EnumFields — Metoda</span><span class="sxs-lookup"><span data-stu-id="8f611-102">IMetaDataImport::EnumFields Method</span></span>
<span data-ttu-id="8f611-103">Wylicza tokeny FieldDef dla typu, do którego odwołuje się określony token TypeDef.</span><span class="sxs-lookup"><span data-stu-id="8f611-103">Enumerates FieldDef tokens for the type referenced by the specified TypeDef token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8f611-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="8f611-104">Syntax</span></span>  
  
```cpp  
HRESULT EnumFields (   
   [in, out] HCORENUM    *phEnum,   
   [in]      mdTypeDef   cl,   
   [out]     mdFieldDef  rFields[],   
   [in]      ULONG       cMax,   
   [out]     ULONG       *pcTokens  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="8f611-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="8f611-105">Parameters</span></span>  
 `phEnum`  
 <span data-ttu-id="8f611-106">[in. out] Wskaźnik do modułu wyliczającego.</span><span class="sxs-lookup"><span data-stu-id="8f611-106">[in, out] A pointer to the enumerator.</span></span>  
  
 `cl`  
 <span data-ttu-id="8f611-107">podczas Token TypeDef klasy, której pola mają zostać wyliczone.</span><span class="sxs-lookup"><span data-stu-id="8f611-107">[in] The TypeDef token of the class whose fields are to be enumerated.</span></span>  
  
 `rFields`  
 <span data-ttu-id="8f611-108">określoną Lista tokenów FieldDef.</span><span class="sxs-lookup"><span data-stu-id="8f611-108">[out] The list of FieldDef tokens.</span></span>  
  
 `cMax`  
 <span data-ttu-id="8f611-109">podczas Maksymalny rozmiar tablicy `rFields`.</span><span class="sxs-lookup"><span data-stu-id="8f611-109">[in] The maximum size of the `rFields` array.</span></span>  
  
 `pcTokens`  
 <span data-ttu-id="8f611-110">określoną Rzeczywista liczba tokenów FieldDef zwróconych w `rFields`.</span><span class="sxs-lookup"><span data-stu-id="8f611-110">[out] The actual number of FieldDef tokens returned in `rFields`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="8f611-111">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="8f611-111">Return Value</span></span>  
  
|<span data-ttu-id="8f611-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="8f611-112">HRESULT</span></span>|<span data-ttu-id="8f611-113">Opis</span><span class="sxs-lookup"><span data-stu-id="8f611-113">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="8f611-114">`EnumFields` pomyślnie zwrócone.</span><span class="sxs-lookup"><span data-stu-id="8f611-114">`EnumFields` returned successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="8f611-115">Brak pól do wyliczenia.</span><span class="sxs-lookup"><span data-stu-id="8f611-115">There are no fields to enumerate.</span></span> <span data-ttu-id="8f611-116">W takim przypadku `pcTokens` wynosi zero.</span><span class="sxs-lookup"><span data-stu-id="8f611-116">In that case, `pcTokens` is zero.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="8f611-117">Wymagania</span><span class="sxs-lookup"><span data-stu-id="8f611-117">Requirements</span></span>  
 <span data-ttu-id="8f611-118">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8f611-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8f611-119">**Nagłówek:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="8f611-119">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="8f611-120">**Biblioteka:** Uwzględnione jako zasób w bibliotece MsCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="8f611-120">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="8f611-121">**Wersje .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8f611-121">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8f611-122">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="8f611-122">See also</span></span>

- [<span data-ttu-id="8f611-123">IMetaDataImport, interfejs</span><span class="sxs-lookup"><span data-stu-id="8f611-123">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [<span data-ttu-id="8f611-124">IMetaDataImport2, interfejs</span><span class="sxs-lookup"><span data-stu-id="8f611-124">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
