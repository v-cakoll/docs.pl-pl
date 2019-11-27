---
title: IMetaDataImport::EnumMethods — Metoda
ms.date: 03/30/2017
api_name:
- IMetaDataImport.EnumMethods
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::EnumMethods
helpviewer_keywords:
- IMetaDataImport::EnumMethods method [.NET Framework metadata]
- EnumMethods method [.NET Framework metadata]
ms.assetid: 8cc3b0c3-d97d-4f71-9e7d-ef2a92b4959a
topic_type:
- apiref
ms.openlocfilehash: 8e9e08ac903423b2e121f22cc9e43a660ccfac7b
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/23/2019
ms.locfileid: "74450086"
---
# <a name="imetadataimportenummethods-method"></a><span data-ttu-id="3a9b6-102">IMetaDataImport::EnumMethods — Metoda</span><span class="sxs-lookup"><span data-stu-id="3a9b6-102">IMetaDataImport::EnumMethods Method</span></span>
<span data-ttu-id="3a9b6-103">Wylicza tokeny MethodDef reprezentujące metody określonego typu.</span><span class="sxs-lookup"><span data-stu-id="3a9b6-103">Enumerates MethodDef tokens representing methods of the specified type.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3a9b6-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="3a9b6-104">Syntax</span></span>  
  
```cpp  
HRESULT EnumMethods (  
   [in, out] HCORENUM   *phEnum,   
   [in]  mdTypeDef      cl,   
   [out] mdMethodDef    rMethods[],   
   [in]  ULONG          cMax,   
   [out] ULONG          *pcTokens  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="3a9b6-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="3a9b6-105">Parameters</span></span>  
 `phEnum`  
 <span data-ttu-id="3a9b6-106">[in. out] Wskaźnik do modułu wyliczającego.</span><span class="sxs-lookup"><span data-stu-id="3a9b6-106">[in, out] A pointer to the enumerator.</span></span> <span data-ttu-id="3a9b6-107">Musi ona mieć wartość NULL dla pierwszego wywołania tej metody.</span><span class="sxs-lookup"><span data-stu-id="3a9b6-107">This must be NULL for the first call of this method.</span></span>  
  
 `cl`  
 <span data-ttu-id="3a9b6-108">podczas Token TypeDef reprezentujący typ z metodami do wyliczenia.</span><span class="sxs-lookup"><span data-stu-id="3a9b6-108">[in] A TypeDef token representing the type with the methods to enumerate.</span></span>  
  
 `rMethods`  
 <span data-ttu-id="3a9b6-109">określoną Tablica do przechowywania tokenów MethodDef.</span><span class="sxs-lookup"><span data-stu-id="3a9b6-109">[out] The array to store the MethodDef tokens.</span></span>  
  
 `cMax`  
 <span data-ttu-id="3a9b6-110">podczas Maksymalny rozmiar tablicy `rMethods` MethodDef.</span><span class="sxs-lookup"><span data-stu-id="3a9b6-110">[in] The maximum size of the MethodDef `rMethods` array.</span></span>  
  
 `pcTokens`  
 <span data-ttu-id="3a9b6-111">określoną Liczba tokenów MethodDef zwróconych w `rMethods`.</span><span class="sxs-lookup"><span data-stu-id="3a9b6-111">[out] The number of MethodDef tokens returned in `rMethods`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="3a9b6-112">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="3a9b6-112">Return Value</span></span>  
  
|<span data-ttu-id="3a9b6-113">HRESULT</span><span class="sxs-lookup"><span data-stu-id="3a9b6-113">HRESULT</span></span>|<span data-ttu-id="3a9b6-114">Opis</span><span class="sxs-lookup"><span data-stu-id="3a9b6-114">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="3a9b6-115">`EnumMethods` pomyślnie zwrócone.</span><span class="sxs-lookup"><span data-stu-id="3a9b6-115">`EnumMethods` returned successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="3a9b6-116">Brak tokenów MethodDef do wyliczenia.</span><span class="sxs-lookup"><span data-stu-id="3a9b6-116">There are no MethodDef tokens to enumerate.</span></span> <span data-ttu-id="3a9b6-117">W takim przypadku `pcTokens` wynosi zero.</span><span class="sxs-lookup"><span data-stu-id="3a9b6-117">In that case, `pcTokens` is zero.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="3a9b6-118">Wymagania</span><span class="sxs-lookup"><span data-stu-id="3a9b6-118">Requirements</span></span>  
 <span data-ttu-id="3a9b6-119">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3a9b6-119">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3a9b6-120">**Nagłówek:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="3a9b6-120">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="3a9b6-121">**Biblioteka:** Uwzględnione jako zasób w bibliotece MsCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="3a9b6-121">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="3a9b6-122">**Wersje .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3a9b6-122">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3a9b6-123">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="3a9b6-123">See also</span></span>

- [<span data-ttu-id="3a9b6-124">IMetaDataImport, interfejs</span><span class="sxs-lookup"><span data-stu-id="3a9b6-124">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [<span data-ttu-id="3a9b6-125">IMetaDataImport2, interfejs</span><span class="sxs-lookup"><span data-stu-id="3a9b6-125">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
