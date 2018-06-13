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
ms.openlocfilehash: c148ee0b2c96f2a387dac54eaff690ab3f05ebf8
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33447061"
---
# <a name="imetadataimportenummemberrefs-method"></a><span data-ttu-id="d5aec-102">IMetaDataImport::EnumMemberRefs — Metoda</span><span class="sxs-lookup"><span data-stu-id="d5aec-102">IMetaDataImport::EnumMemberRefs Method</span></span>
<span data-ttu-id="d5aec-103">Wylicza tokenów elementu MemberRef reprezentujący elementy członkowskie określonego typu.</span><span class="sxs-lookup"><span data-stu-id="d5aec-103">Enumerates MemberRef tokens representing members of the specified type.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d5aec-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="d5aec-104">Syntax</span></span>  
  
```  
HRESULT EnumMemberRefs (  
   [in, out] HCORENUM    *phEnum,   
   [in]   mdToken        tkParent,   
   [out]  mdMemberRef    rMemberRefs[],   
   [in]   ULONG          cMax,   
   [out]  ULONG          *pcTokens  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="d5aec-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="d5aec-105">Parameters</span></span>  
 `phEnum`  
 <span data-ttu-id="d5aec-106">[w, out] Wskaźnik do modułu wyliczającego.</span><span class="sxs-lookup"><span data-stu-id="d5aec-106">[in, out] A pointer to the enumerator.</span></span>  
  
 `tkParent`  
 <span data-ttu-id="d5aec-107">[in] Element TypeDef, element TypeRef, MethodDef lub element ModuleRef token typu, której członkami są mają zostać wyliczone.</span><span class="sxs-lookup"><span data-stu-id="d5aec-107">[in] A TypeDef, TypeRef, MethodDef, or ModuleRef token for the type whose members are to be enumerated.</span></span>  
  
 `rMemberRefs`  
 <span data-ttu-id="d5aec-108">[out] Tablica używany do przechowywania tokenów elementu MemberRef.</span><span class="sxs-lookup"><span data-stu-id="d5aec-108">[out] The array used to store MemberRef tokens.</span></span>  
  
 `cMax`  
 <span data-ttu-id="d5aec-109">[in] Maksymalny rozmiar `rMemberRefs` tablicy.</span><span class="sxs-lookup"><span data-stu-id="d5aec-109">[in] The maximum size of the `rMemberRefs` array.</span></span>  
  
 `pcTokens`  
 <span data-ttu-id="d5aec-110">[out] Rzeczywista liczba tokenów elementu MemberRef zwracane w `rMemberRefs`.</span><span class="sxs-lookup"><span data-stu-id="d5aec-110">[out] The actual number of MemberRef tokens returned in `rMemberRefs`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="d5aec-111">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="d5aec-111">Return Value</span></span>  
  
|<span data-ttu-id="d5aec-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="d5aec-112">HRESULT</span></span>|<span data-ttu-id="d5aec-113">Opis</span><span class="sxs-lookup"><span data-stu-id="d5aec-113">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="d5aec-114">`EnumMemberRefs` zwrócona pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="d5aec-114">`EnumMemberRefs` returned successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="d5aec-115">Nie ma żadnych tokenów elementu MemberRef do wyliczenia.</span><span class="sxs-lookup"><span data-stu-id="d5aec-115">There are no MemberRef tokens to enumerate.</span></span> <span data-ttu-id="d5aec-116">W takim przypadku `pcTokens` ma wartość zero.</span><span class="sxs-lookup"><span data-stu-id="d5aec-116">In that case, `pcTokens` is to zero.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="d5aec-117">Wymagania</span><span class="sxs-lookup"><span data-stu-id="d5aec-117">Requirements</span></span>  
 <span data-ttu-id="d5aec-118">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d5aec-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d5aec-119">**Nagłówek:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="d5aec-119">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="d5aec-120">**Biblioteka:** uwzględnione jako zasób w MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="d5aec-120">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="d5aec-121">**Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d5aec-121">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d5aec-122">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="d5aec-122">See Also</span></span>  
 [<span data-ttu-id="d5aec-123">IMetaDataImport, interfejs</span><span class="sxs-lookup"><span data-stu-id="d5aec-123">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)  
 [<span data-ttu-id="d5aec-124">IMetaDataImport2, interfejs</span><span class="sxs-lookup"><span data-stu-id="d5aec-124">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
