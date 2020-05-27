---
title: IMetaDataEmit::SetMethodProps — Metoda
ms.date: 03/30/2017
api_name:
- IMetaDataEmit.SetMethodProps
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit::SetMethodProps
helpviewer_keywords:
- SetMethodProps method [.NET Framework metadata]
- IMetaDataEmit::SetMethodProps method [.NET Framework metadata]
ms.assetid: e0c6ac12-22ea-43f5-b799-8cda0faf3336
topic_type:
- apiref
ms.openlocfilehash: 57f6de1f7edf7c75a3f96cb2bf9fb98fdbd6f65e
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/27/2020
ms.locfileid: "84007861"
---
# <a name="imetadataemitsetmethodprops-method"></a><span data-ttu-id="7edb4-102">IMetaDataEmit::SetMethodProps — Metoda</span><span class="sxs-lookup"><span data-stu-id="7edb4-102">IMetaDataEmit::SetMethodProps Method</span></span>
<span data-ttu-id="7edb4-103">Ustawia lub aktualizuje funkcję przechowywaną w określonym względnym adresie wirtualnym metody zdefiniowanej przez wcześniejsze wywołanie do [IMetaDataEmit::D efinemethod](imetadataemit-definemethod-method.md).</span><span class="sxs-lookup"><span data-stu-id="7edb4-103">Sets or updates the feature, stored at the specified relative virtual address, of a method defined by a prior call to [IMetaDataEmit::DefineMethod](imetadataemit-definemethod-method.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7edb4-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="7edb4-104">Syntax</span></span>  
  
```cpp  
HRESULT SetMethodProps (
    [in]  mdMethodDef md,
    [in]  DWORD       dwMethodFlags,  
    [in]  ULONG       ulCodeRVA,
    [in]  DWORD       dwImplFlags
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="7edb4-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="7edb4-105">Parameters</span></span>  
 `md`  
 <span data-ttu-id="7edb4-106">podczas Token dla metody, która ma zostać zmieniona.</span><span class="sxs-lookup"><span data-stu-id="7edb4-106">[in] The token for the method to be changed.</span></span>  
  
 `dwMethodFlags`  
 <span data-ttu-id="7edb4-107">podczas Atrybuty elementu członkowskiego.</span><span class="sxs-lookup"><span data-stu-id="7edb4-107">[in] The member attributes.</span></span>  
  
 `ulCodeRVA`  
 <span data-ttu-id="7edb4-108">podczas Adres kodu.</span><span class="sxs-lookup"><span data-stu-id="7edb4-108">[in] The address of the code.</span></span>  
  
 `dwImplFlags`  
 <span data-ttu-id="7edb4-109">podczas Flagi implementacji dla metody.</span><span class="sxs-lookup"><span data-stu-id="7edb4-109">[in] The implementation flags for the method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7edb4-110">Wymagania</span><span class="sxs-lookup"><span data-stu-id="7edb4-110">Requirements</span></span>  
 <span data-ttu-id="7edb4-111">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7edb4-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7edb4-112">**Nagłówek:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="7edb4-112">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="7edb4-113">**Biblioteka:** Używany jako zasób w bibliotece MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="7edb4-113">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="7edb4-114">**.NET Framework wersje:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7edb4-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7edb4-115">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="7edb4-115">See also</span></span>

- [<span data-ttu-id="7edb4-116">IMetaDataEmit — Interfejs</span><span class="sxs-lookup"><span data-stu-id="7edb4-116">IMetaDataEmit Interface</span></span>](imetadataemit-interface.md)
- [<span data-ttu-id="7edb4-117">IMetaDataEmit2, interfejs</span><span class="sxs-lookup"><span data-stu-id="7edb4-117">IMetaDataEmit2 Interface</span></span>](imetadataemit2-interface.md)
