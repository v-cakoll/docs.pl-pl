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
ms.openlocfilehash: 68cdefe7ab362b26bbf060fa46766068eb0d7094
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/08/2020
ms.locfileid: "84503760"
---
# <a name="imetadataimportenummemberrefs-method"></a><span data-ttu-id="a514a-102">IMetaDataImport::EnumMemberRefs — Metoda</span><span class="sxs-lookup"><span data-stu-id="a514a-102">IMetaDataImport::EnumMemberRefs Method</span></span>
<span data-ttu-id="a514a-103">Wylicza tokeny elementu MemberRef reprezentujące elementy członkowskie określonego typu.</span><span class="sxs-lookup"><span data-stu-id="a514a-103">Enumerates MemberRef tokens representing members of the specified type.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a514a-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="a514a-104">Syntax</span></span>  
  
```cpp  
HRESULT EnumMemberRefs (  
   [in, out] HCORENUM    *phEnum,
   [in]   mdToken        tkParent,
   [out]  mdMemberRef    rMemberRefs[],
   [in]   ULONG          cMax,
   [out]  ULONG          *pcTokens  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="a514a-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="a514a-105">Parameters</span></span>  
 `phEnum`  
 <span data-ttu-id="a514a-106">[in. out] Wskaźnik do modułu wyliczającego.</span><span class="sxs-lookup"><span data-stu-id="a514a-106">[in, out] A pointer to the enumerator.</span></span>  
  
 `tkParent`  
 <span data-ttu-id="a514a-107">podczas Token TypeDef, TypeRef, MethodDef lub ModuleRef dla typu, którego składowe mają zostać wyliczone.</span><span class="sxs-lookup"><span data-stu-id="a514a-107">[in] A TypeDef, TypeRef, MethodDef, or ModuleRef token for the type whose members are to be enumerated.</span></span>  
  
 `rMemberRefs`  
 <span data-ttu-id="a514a-108">określoną Tablica służąca do przechowywania tokenów elementu MemberRef.</span><span class="sxs-lookup"><span data-stu-id="a514a-108">[out] The array used to store MemberRef tokens.</span></span>  
  
 `cMax`  
 <span data-ttu-id="a514a-109">podczas Maksymalny rozmiar `rMemberRefs` tablicy.</span><span class="sxs-lookup"><span data-stu-id="a514a-109">[in] The maximum size of the `rMemberRefs` array.</span></span>  
  
 `pcTokens`  
 <span data-ttu-id="a514a-110">określoną Rzeczywista liczba tokenów elementu MemberRef zwrócona w `rMemberRefs` .</span><span class="sxs-lookup"><span data-stu-id="a514a-110">[out] The actual number of MemberRef tokens returned in `rMemberRefs`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="a514a-111">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="a514a-111">Return Value</span></span>  
  
|<span data-ttu-id="a514a-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="a514a-112">HRESULT</span></span>|<span data-ttu-id="a514a-113">Opis</span><span class="sxs-lookup"><span data-stu-id="a514a-113">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="a514a-114">`EnumMemberRefs`pomyślnie zwrócono.</span><span class="sxs-lookup"><span data-stu-id="a514a-114">`EnumMemberRefs` returned successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="a514a-115">Brak tokenów elementu MemberRef do wyliczenia.</span><span class="sxs-lookup"><span data-stu-id="a514a-115">There are no MemberRef tokens to enumerate.</span></span> <span data-ttu-id="a514a-116">W takim przypadku `pcTokens` ma wartość zero.</span><span class="sxs-lookup"><span data-stu-id="a514a-116">In that case, `pcTokens` is to zero.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="a514a-117">Wymagania</span><span class="sxs-lookup"><span data-stu-id="a514a-117">Requirements</span></span>  
 <span data-ttu-id="a514a-118">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a514a-118">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a514a-119">**Nagłówek:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="a514a-119">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="a514a-120">**Biblioteka:** Uwzględnione jako zasób w bibliotece MsCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="a514a-120">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="a514a-121">**.NET Framework wersje:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a514a-121">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a514a-122">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="a514a-122">See also</span></span>

- [<span data-ttu-id="a514a-123">IMetaDataImport — Interfejs</span><span class="sxs-lookup"><span data-stu-id="a514a-123">IMetaDataImport Interface</span></span>](imetadataimport-interface.md)
- [<span data-ttu-id="a514a-124">IMetaDataImport2, interfejs</span><span class="sxs-lookup"><span data-stu-id="a514a-124">IMetaDataImport2 Interface</span></span>](imetadataimport2-interface.md)
