---
title: IInstallReferenceEnum — Interfejs
ms.date: 03/30/2017
api_name:
- IInstallReferenceEnum
api_location:
- fusion.dll
api_type:
- COM
f1_keywords:
- IInstallReferenceEnum
helpviewer_keywords:
- IInstallReferenceEnum interface [.NET Framework fusion]
ms.assetid: 2863b33b-a541-462c-bbe8-702a2832898e
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 0d29b9e2a9b9022f682065816a62734d6c5b2d62
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/07/2019
ms.locfileid: "70796408"
---
# <a name="iinstallreferenceenum-interface"></a><span data-ttu-id="4d72f-102">IInstallReferenceEnum — Interfejs</span><span class="sxs-lookup"><span data-stu-id="4d72f-102">IInstallReferenceEnum Interface</span></span>
<span data-ttu-id="4d72f-103">Reprezentuje moduł wyliczający dla zestawów, do których istnieją odwołania zainstalowane w globalnej pamięci podręcznej zestawów.</span><span class="sxs-lookup"><span data-stu-id="4d72f-103">Represents an enumerator for the referenced assemblies installed in the global assembly cache.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4d72f-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="4d72f-104">Syntax</span></span>  
  
```cpp  
interface IInstallReferenceEnum : IUnknown {  
    HRESULT GetNextInstallReferenceItem (  
        [out] IInstallReferenceItem **ppRefItem,  
        [in]  DWORD dwFlags,  
        [in]  LPVOID pvReserved  
    );  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="4d72f-105">Metody</span><span class="sxs-lookup"><span data-stu-id="4d72f-105">Methods</span></span>  
  
|<span data-ttu-id="4d72f-106">Metoda</span><span class="sxs-lookup"><span data-stu-id="4d72f-106">Method</span></span>|<span data-ttu-id="4d72f-107">Opis</span><span class="sxs-lookup"><span data-stu-id="4d72f-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="4d72f-108">GetNextInstallReferenceItem, metoda</span><span class="sxs-lookup"><span data-stu-id="4d72f-108">GetNextInstallReferenceItem Method</span></span>](iinstallreferenceenum-getnextinstallreferenceitem-method.md)|<span data-ttu-id="4d72f-109">Pobiera wskaźnik do następnego `IInstallReferenceItem` elementu zawartego w tym `IInstallReferenceEnum`elemencie.</span><span class="sxs-lookup"><span data-stu-id="4d72f-109">Gets a pointer to the next `IInstallReferenceItem` contained in this `IInstallReferenceEnum`.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="4d72f-110">Wymagania</span><span class="sxs-lookup"><span data-stu-id="4d72f-110">Requirements</span></span>  
 <span data-ttu-id="4d72f-111">**Poszczególnych** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4d72f-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4d72f-112">**Nagłówki** Fusion. h</span><span class="sxs-lookup"><span data-stu-id="4d72f-112">**Header:** Fusion.h</span></span>  
  
 <span data-ttu-id="4d72f-113">**.NET Framework wersje:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4d72f-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4d72f-114">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="4d72f-114">See also</span></span>

- [<span data-ttu-id="4d72f-115">Interfejsy łączenia</span><span class="sxs-lookup"><span data-stu-id="4d72f-115">Fusion Interfaces</span></span>](fusion-interfaces.md)
- [<span data-ttu-id="4d72f-116">IInstallReferenceItem, interfejs</span><span class="sxs-lookup"><span data-stu-id="4d72f-116">IInstallReferenceItem Interface</span></span>](iinstallreferenceitem-interface.md)
