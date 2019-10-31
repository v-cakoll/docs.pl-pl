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
ms.openlocfilehash: 0dad50f1acac38f8cdc505026e88d42882deb580
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73131722"
---
# <a name="iinstallreferenceenumgetnextinstallreferenceitem-method"></a><span data-ttu-id="877e8-102">IInstallReferenceEnum::GetNextInstallReferenceItem — Metoda</span><span class="sxs-lookup"><span data-stu-id="877e8-102">IInstallReferenceEnum::GetNextInstallReferenceItem Method</span></span>
<span data-ttu-id="877e8-103">Pobiera wskaźnik do następnego obiektu [IInstallReferenceItem](iinstallreferenceitem-interface.md) zawartego w tym obiekcie [IInstallReferenceEnum](iinstallreferenceenum-interface.md) .</span><span class="sxs-lookup"><span data-stu-id="877e8-103">Gets a pointer to the next [IInstallReferenceItem](iinstallreferenceitem-interface.md) object contained in this [IInstallReferenceEnum](iinstallreferenceenum-interface.md) object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="877e8-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="877e8-104">Syntax</span></span>  
  
```cpp  
HRESULT GetNextInstallReferenceItem (  
    [out] IInstallReferenceItem **ppRefItem,  
    [in]  DWORD dwFlags,  
    [in]  LPVOID pvReserved  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="877e8-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="877e8-105">Parameters</span></span>  
 `ppRefItem`  
 <span data-ttu-id="877e8-106">określoną Zwrócony wskaźnik `IInstallReferenceItem`.</span><span class="sxs-lookup"><span data-stu-id="877e8-106">[out] The returned `IInstallReferenceItem` pointer.</span></span>  
  
 `dwFlags`  
 <span data-ttu-id="877e8-107">podczas Zarezerwowane do użytku w przyszłości.</span><span class="sxs-lookup"><span data-stu-id="877e8-107">[in] Reserved for future extensibility.</span></span> <span data-ttu-id="877e8-108">`dwFlags` musi mieć wartość 0 (zero).</span><span class="sxs-lookup"><span data-stu-id="877e8-108">`dwFlags` must be 0 (zero).</span></span>  
  
 `pvReserved`  
 <span data-ttu-id="877e8-109">podczas Zarezerwowane do użytku w przyszłości.</span><span class="sxs-lookup"><span data-stu-id="877e8-109">[in] Reserved for future extensibility.</span></span> <span data-ttu-id="877e8-110">`pvReserved` musi być odwołaniem o wartości null.</span><span class="sxs-lookup"><span data-stu-id="877e8-110">`pvReserved` must be a null reference.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="877e8-111">Wymagania</span><span class="sxs-lookup"><span data-stu-id="877e8-111">Requirements</span></span>  
 <span data-ttu-id="877e8-112">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="877e8-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="877e8-113">**Nagłówek:** Fusion. h</span><span class="sxs-lookup"><span data-stu-id="877e8-113">**Header:** Fusion.h</span></span>  
  
 <span data-ttu-id="877e8-114">**Wersje .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="877e8-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="877e8-115">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="877e8-115">See also</span></span>

- [<span data-ttu-id="877e8-116">IInstallReferenceItem, interfejs</span><span class="sxs-lookup"><span data-stu-id="877e8-116">IInstallReferenceItem Interface</span></span>](iinstallreferenceitem-interface.md)
- [<span data-ttu-id="877e8-117">IInstallReferenceEnum, interfejs</span><span class="sxs-lookup"><span data-stu-id="877e8-117">IInstallReferenceEnum Interface</span></span>](iinstallreferenceenum-interface.md)
