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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: a08577f15a6fab0e630d40032a23c273ee935faa
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61992332"
---
# <a name="imetadataimportenummemberrefs-method"></a><span data-ttu-id="0fd90-102">IMetaDataImport::EnumMemberRefs — Metoda</span><span class="sxs-lookup"><span data-stu-id="0fd90-102">IMetaDataImport::EnumMemberRefs Method</span></span>
<span data-ttu-id="0fd90-103">Wylicza tokenów MemberRef reprezentujących elementy określonego typu.</span><span class="sxs-lookup"><span data-stu-id="0fd90-103">Enumerates MemberRef tokens representing members of the specified type.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0fd90-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="0fd90-104">Syntax</span></span>  
  
```  
HRESULT EnumMemberRefs (  
   [in, out] HCORENUM    *phEnum,   
   [in]   mdToken        tkParent,   
   [out]  mdMemberRef    rMemberRefs[],   
   [in]   ULONG          cMax,   
   [out]  ULONG          *pcTokens  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="0fd90-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="0fd90-105">Parameters</span></span>  
 `phEnum`  
 <span data-ttu-id="0fd90-106">[out w] Wskaźnik do modułu wyliczającego.</span><span class="sxs-lookup"><span data-stu-id="0fd90-106">[in, out] A pointer to the enumerator.</span></span>  
  
 `tkParent`  
 <span data-ttu-id="0fd90-107">[in] Element TypeDef, TypeRef, MethodDef lub element ModuleRef token dla typu, której członkami są do wyliczenia.</span><span class="sxs-lookup"><span data-stu-id="0fd90-107">[in] A TypeDef, TypeRef, MethodDef, or ModuleRef token for the type whose members are to be enumerated.</span></span>  
  
 `rMemberRefs`  
 <span data-ttu-id="0fd90-108">[out] Tablica do przechowywania tokenów MemberRef.</span><span class="sxs-lookup"><span data-stu-id="0fd90-108">[out] The array used to store MemberRef tokens.</span></span>  
  
 `cMax`  
 <span data-ttu-id="0fd90-109">[in] Maksymalny rozmiar `rMemberRefs` tablicy.</span><span class="sxs-lookup"><span data-stu-id="0fd90-109">[in] The maximum size of the `rMemberRefs` array.</span></span>  
  
 `pcTokens`  
 <span data-ttu-id="0fd90-110">[out] Rzeczywista liczba tokenów MemberRef zwracane w `rMemberRefs`.</span><span class="sxs-lookup"><span data-stu-id="0fd90-110">[out] The actual number of MemberRef tokens returned in `rMemberRefs`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="0fd90-111">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="0fd90-111">Return Value</span></span>  
  
|<span data-ttu-id="0fd90-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="0fd90-112">HRESULT</span></span>|<span data-ttu-id="0fd90-113">Opis</span><span class="sxs-lookup"><span data-stu-id="0fd90-113">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="0fd90-114">`EnumMemberRefs` pomyślnie zwrócił.</span><span class="sxs-lookup"><span data-stu-id="0fd90-114">`EnumMemberRefs` returned successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="0fd90-115">Nie ma żadnych tokeny MemberRef do wyliczenia.</span><span class="sxs-lookup"><span data-stu-id="0fd90-115">There are no MemberRef tokens to enumerate.</span></span> <span data-ttu-id="0fd90-116">W takim przypadku `pcTokens` ma wartość zero.</span><span class="sxs-lookup"><span data-stu-id="0fd90-116">In that case, `pcTokens` is to zero.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="0fd90-117">Wymagania</span><span class="sxs-lookup"><span data-stu-id="0fd90-117">Requirements</span></span>  
 <span data-ttu-id="0fd90-118">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0fd90-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0fd90-119">**Nagłówek:** COR.h</span><span class="sxs-lookup"><span data-stu-id="0fd90-119">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="0fd90-120">**Biblioteka:** Dołączony jako zasób w MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="0fd90-120">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="0fd90-121">**Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0fd90-121">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0fd90-122">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="0fd90-122">See also</span></span>

- [<span data-ttu-id="0fd90-123">IMetaDataImport, interfejs</span><span class="sxs-lookup"><span data-stu-id="0fd90-123">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [<span data-ttu-id="0fd90-124">IMetaDataImport2, interfejs</span><span class="sxs-lookup"><span data-stu-id="0fd90-124">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
