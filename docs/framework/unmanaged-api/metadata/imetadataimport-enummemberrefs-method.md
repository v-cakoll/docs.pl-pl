---
title: IMetaDataImport::EnumMemberRefs — Metoda
ms.date: 03/30/2017
api_name:
- IMetaDataImport.EnumMemberRefs
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::EnumMemberRefs
helpviewer_keywords:
- EnumMemberRefs method [.NET Framework metadata]
- IMetaDataImport::EnumMemberRefs method [.NET Framework metadata]
ms.assetid: e97c97a6-6e4f-41f5-9af1-9b3cf3bdbd6b
topic_type:
- apiref
ms.openlocfilehash: b8a65b0748fec0e474d8b3b5dc03473fbd716108
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79177332"
---
# <a name="imetadataimportenummemberrefs-method"></a><span data-ttu-id="220ae-102">IMetaDataImport::EnumMemberRefs — Metoda</span><span class="sxs-lookup"><span data-stu-id="220ae-102">IMetaDataImport::EnumMemberRefs Method</span></span>
<span data-ttu-id="220ae-103">Wylicza tokeny MemberRef reprezentujące członków określonego typu.</span><span class="sxs-lookup"><span data-stu-id="220ae-103">Enumerates MemberRef tokens representing members of the specified type.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="220ae-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="220ae-104">Syntax</span></span>  
  
```cpp  
HRESULT EnumMemberRefs (  
   [in, out] HCORENUM    *phEnum,
   [in]   mdToken        tkParent,
   [out]  mdMemberRef    rMemberRefs[],
   [in]   ULONG          cMax,
   [out]  ULONG          *pcTokens  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="220ae-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="220ae-105">Parameters</span></span>  
 `phEnum`  
 <span data-ttu-id="220ae-106">[w, na zewnątrz] Wskaźnik do wyliczacza.</span><span class="sxs-lookup"><span data-stu-id="220ae-106">[in, out] A pointer to the enumerator.</span></span>  
  
 `tkParent`  
 <span data-ttu-id="220ae-107">[w] A TypeDef, TypeRef, MethodDef lub ModuleRef token dla typu, którego elementy członkowskie mają być wyliczone.</span><span class="sxs-lookup"><span data-stu-id="220ae-107">[in] A TypeDef, TypeRef, MethodDef, or ModuleRef token for the type whose members are to be enumerated.</span></span>  
  
 `rMemberRefs`  
 <span data-ttu-id="220ae-108">[na zewnątrz] Tablica używana do przechowywania tokenów MemberRef.</span><span class="sxs-lookup"><span data-stu-id="220ae-108">[out] The array used to store MemberRef tokens.</span></span>  
  
 `cMax`  
 <span data-ttu-id="220ae-109">[w] Maksymalny rozmiar `rMemberRefs` tablicy.</span><span class="sxs-lookup"><span data-stu-id="220ae-109">[in] The maximum size of the `rMemberRefs` array.</span></span>  
  
 `pcTokens`  
 <span data-ttu-id="220ae-110">[na zewnątrz] Rzeczywista liczba tokenów MemberRef `rMemberRefs`zwrócona w .</span><span class="sxs-lookup"><span data-stu-id="220ae-110">[out] The actual number of MemberRef tokens returned in `rMemberRefs`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="220ae-111">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="220ae-111">Return Value</span></span>  
  
|<span data-ttu-id="220ae-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="220ae-112">HRESULT</span></span>|<span data-ttu-id="220ae-113">Opis</span><span class="sxs-lookup"><span data-stu-id="220ae-113">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="220ae-114">`EnumMemberRefs`zwrócono pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="220ae-114">`EnumMemberRefs` returned successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="220ae-115">Nie ma żadnych tokenów MemberRef do wyliczenia.</span><span class="sxs-lookup"><span data-stu-id="220ae-115">There are no MemberRef tokens to enumerate.</span></span> <span data-ttu-id="220ae-116">W takim `pcTokens` przypadku jest do zera.</span><span class="sxs-lookup"><span data-stu-id="220ae-116">In that case, `pcTokens` is to zero.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="220ae-117">Wymagania</span><span class="sxs-lookup"><span data-stu-id="220ae-117">Requirements</span></span>  
 <span data-ttu-id="220ae-118">**Platformy:** Zobacz [Wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="220ae-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="220ae-119">**Nagłówek:** Okręg wyborczy Cor.h</span><span class="sxs-lookup"><span data-stu-id="220ae-119">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="220ae-120">**Biblioteka:** Uwzględnione jako zasób w pliku MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="220ae-120">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="220ae-121">**Wersje programu .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="220ae-121">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="220ae-122">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="220ae-122">See also</span></span>

- [<span data-ttu-id="220ae-123">IMetaDataImport — Interfejs</span><span class="sxs-lookup"><span data-stu-id="220ae-123">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [<span data-ttu-id="220ae-124">IMetaDataImport2, interfejs</span><span class="sxs-lookup"><span data-stu-id="220ae-124">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
