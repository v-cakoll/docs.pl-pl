---
title: IGCHost2 — Interfejs
ms.date: 03/30/2017
api_name:
- IGCHost2
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IGCHost2
helpviewer_keywords:
- IGCHost2 interface [.NET Framework hosting]
ms.assetid: e5323fa4-18ac-424d-859d-a65a550d08d9
topic_type:
- apiref
ms.openlocfilehash: 976673a0caab4e041cc80e5536544c195fcf692a
ms.sourcegitcommit: d223616e7e6fe2139079052e6fcbe25413fb9900
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/22/2020
ms.locfileid: "83805179"
---
# <a name="igchost2-interface"></a><span data-ttu-id="bdd19-102">IGCHost2 — Interfejs</span><span class="sxs-lookup"><span data-stu-id="bdd19-102">IGCHost2 Interface</span></span>
<span data-ttu-id="bdd19-103">Zapewnia metody uzyskiwania informacji o systemie odzyskiwania pamięci i kontrolowania niektórych aspektów wyrzucania elementów bezużytecznych.</span><span class="sxs-lookup"><span data-stu-id="bdd19-103">Provides methods for obtaining information about the garbage collection system and for controlling some aspects of garbage collection.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="bdd19-104">W przypadku nowych rozwiązań zalecamy użycie interfejsu [ICLRGCManager2](iclrgcmanager2-interface.md) .</span><span class="sxs-lookup"><span data-stu-id="bdd19-104">For new development, we recommend that you use the [ICLRGCManager2](iclrgcmanager2-interface.md) interface instead.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="bdd19-105">Metody</span><span class="sxs-lookup"><span data-stu-id="bdd19-105">Methods</span></span>  
  
|<span data-ttu-id="bdd19-106">Metoda</span><span class="sxs-lookup"><span data-stu-id="bdd19-106">Method</span></span>|<span data-ttu-id="bdd19-107">Opis</span><span class="sxs-lookup"><span data-stu-id="bdd19-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="bdd19-108">SetGCStartupLimitsEx, metoda</span><span class="sxs-lookup"><span data-stu-id="bdd19-108">SetGCStartupLimitsEx Method</span></span>](igchost2-setgcstartuplimitsex-method.md)|<span data-ttu-id="bdd19-109">Ustawia rozmiar segmentu i maksymalny rozmiar generacji 0.</span><span class="sxs-lookup"><span data-stu-id="bdd19-109">Sets the segment size and the maximum size for generation 0.</span></span> <span data-ttu-id="bdd19-110">Włącza wartość generacji 0 i rozmiary segmentów większe niż `DWORD` .</span><span class="sxs-lookup"><span data-stu-id="bdd19-110">Enables generation 0 and segment sizes larger than `DWORD`.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="bdd19-111">Wymagania</span><span class="sxs-lookup"><span data-stu-id="bdd19-111">Requirements</span></span>  
 <span data-ttu-id="bdd19-112">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="bdd19-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="bdd19-113">**Nagłówek:** GCHost. idl, GCHost. h</span><span class="sxs-lookup"><span data-stu-id="bdd19-113">**Header:** GCHost.idl, GCHost.h</span></span>  
  
 <span data-ttu-id="bdd19-114">**Biblioteka:** Uwzględnione jako zasób w bibliotece MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="bdd19-114">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="bdd19-115">**.NET Framework wersje:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="bdd19-115">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bdd19-116">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="bdd19-116">See also</span></span>

- [<span data-ttu-id="bdd19-117">Hosting, interfejsy</span><span class="sxs-lookup"><span data-stu-id="bdd19-117">Hosting Interfaces</span></span>](hosting-interfaces.md)
- [<span data-ttu-id="bdd19-118">Interfejsy hostingu środowiska CLR</span><span class="sxs-lookup"><span data-stu-id="bdd19-118">CLR Hosting Interfaces</span></span>](clr-hosting-interfaces.md)
- [<span data-ttu-id="bdd19-119">CorRuntimeHost, klasa coclass</span><span class="sxs-lookup"><span data-stu-id="bdd19-119">CorRuntimeHost Coclass</span></span>](corruntimehost-coclass.md)
