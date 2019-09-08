---
title: IInstallReferenceEnum::GetNextInstallReferenceItem — Metoda
ms.date: 03/30/2017
api_name:
- IInstallReferenceEnum.GetNextInstallReferenceItem
api_location:
- fusion.dll
api_type:
- COM
f1_keywords:
- IInstallReferenceEnum::GetNextInstallReferenceItem
helpviewer_keywords:
- IInstallReferenceEnum::GetNextInstallReferenceItem method [.NET Framework fusion]
- GetNextInstallReferenceItem method [.NET Framework fusion]
ms.assetid: ce969c9d-6538-4c34-8784-148ffd99fe7a
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 20e2bff4257df64f761fd8fff880643d4e786748
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/07/2019
ms.locfileid: "70796447"
---
# <a name="iinstallreferenceenumgetnextinstallreferenceitem-method"></a><span data-ttu-id="87aa4-102">IInstallReferenceEnum::GetNextInstallReferenceItem — Metoda</span><span class="sxs-lookup"><span data-stu-id="87aa4-102">IInstallReferenceEnum::GetNextInstallReferenceItem Method</span></span>
<span data-ttu-id="87aa4-103">Pobiera wskaźnik do następnego obiektu [IInstallReferenceItem](iinstallreferenceitem-interface.md) zawartego w tym obiekcie [IInstallReferenceEnum](iinstallreferenceenum-interface.md) .</span><span class="sxs-lookup"><span data-stu-id="87aa4-103">Gets a pointer to the next [IInstallReferenceItem](iinstallreferenceitem-interface.md) object contained in this [IInstallReferenceEnum](iinstallreferenceenum-interface.md) object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="87aa4-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="87aa4-104">Syntax</span></span>  
  
```cpp  
HRESULT GetNextInstallReferenceItem (  
    [out] IInstallReferenceItem **ppRefItem,  
    [in]  DWORD dwFlags,  
    [in]  LPVOID pvReserved  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="87aa4-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="87aa4-105">Parameters</span></span>  
 `ppRefItem`  
 <span data-ttu-id="87aa4-106">określoną Zwrócony `IInstallReferenceItem` wskaźnik.</span><span class="sxs-lookup"><span data-stu-id="87aa4-106">[out] The returned `IInstallReferenceItem` pointer.</span></span>  
  
 `dwFlags`  
 <span data-ttu-id="87aa4-107">podczas Zarezerwowane do użytku w przyszłości.</span><span class="sxs-lookup"><span data-stu-id="87aa4-107">[in] Reserved for future extensibility.</span></span> <span data-ttu-id="87aa4-108">`dwFlags`musi mieć wartość 0 (zero).</span><span class="sxs-lookup"><span data-stu-id="87aa4-108">`dwFlags` must be 0 (zero).</span></span>  
  
 `pvReserved`  
 <span data-ttu-id="87aa4-109">podczas Zarezerwowane do użytku w przyszłości.</span><span class="sxs-lookup"><span data-stu-id="87aa4-109">[in] Reserved for future extensibility.</span></span> <span data-ttu-id="87aa4-110">`pvReserved`musi być odwołaniem o wartości null.</span><span class="sxs-lookup"><span data-stu-id="87aa4-110">`pvReserved` must be a null reference.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="87aa4-111">Wymagania</span><span class="sxs-lookup"><span data-stu-id="87aa4-111">Requirements</span></span>  
 <span data-ttu-id="87aa4-112">**Poszczególnych** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="87aa4-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="87aa4-113">**Nagłówki** Fusion. h</span><span class="sxs-lookup"><span data-stu-id="87aa4-113">**Header:** Fusion.h</span></span>  
  
 <span data-ttu-id="87aa4-114">**.NET Framework wersje:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="87aa4-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="87aa4-115">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="87aa4-115">See also</span></span>

- [<span data-ttu-id="87aa4-116">IInstallReferenceItem, interfejs</span><span class="sxs-lookup"><span data-stu-id="87aa4-116">IInstallReferenceItem Interface</span></span>](iinstallreferenceitem-interface.md)
- [<span data-ttu-id="87aa4-117">IInstallReferenceEnum, interfejs</span><span class="sxs-lookup"><span data-stu-id="87aa4-117">IInstallReferenceEnum Interface</span></span>](iinstallreferenceenum-interface.md)
