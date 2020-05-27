---
title: IMetaDataEmit::DefineMemberRef — Metoda
ms.date: 03/30/2017
api_name:
- IMetaDataEmit.DefineMemberRef
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit::DefineMemberRef
helpviewer_keywords:
- DefineMemberRef method [.NET Framework metadata]
- IMetaDataEmit::DefineMemberRef method [.NET Framework metadata]
ms.assetid: 21b5bcb8-ea75-4962-8acc-ad17584061e5
topic_type:
- apiref
ms.openlocfilehash: 576f4561ed782f091840ac378831110a1bfef9c6
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/27/2020
ms.locfileid: "84004699"
---
# <a name="imetadataemitdefinememberref-method"></a><span data-ttu-id="d16e0-102">IMetaDataEmit::DefineMemberRef — Metoda</span><span class="sxs-lookup"><span data-stu-id="d16e0-102">IMetaDataEmit::DefineMemberRef Method</span></span>
<span data-ttu-id="d16e0-103">Definiuje odwołanie do elementu członkowskiego modułu poza bieżącym zakresem i pobiera token do tej definicji odwołania.</span><span class="sxs-lookup"><span data-stu-id="d16e0-103">Defines a reference to a member of a module outside the current scope, and gets a token to that reference definition.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d16e0-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="d16e0-104">Syntax</span></span>  
  
```cpp  
HRESULT DefineMemberRef (
    [in]  mdToken           tkImport,
    [in]  LPCWSTR           szName,
    [in]  PCCOR_SIGNATURE   pvSigBlob,
    [in]  ULONG             cbSigBlob,
    [out] mdMemberRef       *pmr
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d16e0-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="d16e0-105">Parameters</span></span>  
 `tkImport`  
 <span data-ttu-id="d16e0-106">podczas Token klasy lub interfejsu docelowej składowej, jeśli element członkowski nie jest globalny; Jeśli element członkowski jest globalny, `mdModuleRef` token dla tego innego pliku.</span><span class="sxs-lookup"><span data-stu-id="d16e0-106">[in] Token for the target member's class or interface, if the member is not global; if the member is global, the `mdModuleRef` token for that other file.</span></span>  
  
 `szName`  
 <span data-ttu-id="d16e0-107">podczas Nazwa docelowego elementu członkowskiego.</span><span class="sxs-lookup"><span data-stu-id="d16e0-107">[in] The name of the target member.</span></span>  
  
 `pvSigBlob`  
 <span data-ttu-id="d16e0-108">podczas Sygnatura docelowego elementu członkowskiego.</span><span class="sxs-lookup"><span data-stu-id="d16e0-108">[in] The signature of the target member.</span></span>  
  
 `cbSigBlob`  
 <span data-ttu-id="d16e0-109">podczas Liczba bajtów w `pvSigBlob` .</span><span class="sxs-lookup"><span data-stu-id="d16e0-109">[in] The count of bytes in `pvSigBlob`.</span></span>  
  
 `pmr`  
 <span data-ttu-id="d16e0-110">określoną `mdMemberRef`Przypisany token.</span><span class="sxs-lookup"><span data-stu-id="d16e0-110">[out] The `mdMemberRef` token assigned.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d16e0-111">Wymagania</span><span class="sxs-lookup"><span data-stu-id="d16e0-111">Requirements</span></span>  
 <span data-ttu-id="d16e0-112">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d16e0-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d16e0-113">**Nagłówek:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="d16e0-113">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="d16e0-114">**Biblioteka:** Używany jako zasób w bibliotece MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="d16e0-114">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="d16e0-115">**.NET Framework wersje:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d16e0-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d16e0-116">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="d16e0-116">See also</span></span>

- [<span data-ttu-id="d16e0-117">IMetaDataEmit — Interfejs</span><span class="sxs-lookup"><span data-stu-id="d16e0-117">IMetaDataEmit Interface</span></span>](imetadataemit-interface.md)
- [<span data-ttu-id="d16e0-118">IMetaDataEmit2, interfejs</span><span class="sxs-lookup"><span data-stu-id="d16e0-118">IMetaDataEmit2 Interface</span></span>](imetadataemit2-interface.md)
