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
ms.openlocfilehash: 2aed89008dd2fa86b38f243c8e7cca1bdda901e1
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54497777"
---
# <a name="iinstallreferenceenum-interface"></a><span data-ttu-id="f4de1-102">IInstallReferenceEnum — Interfejs</span><span class="sxs-lookup"><span data-stu-id="f4de1-102">IInstallReferenceEnum Interface</span></span>
<span data-ttu-id="f4de1-103">Reprezentuje moduł wyliczający przywoływanych zestawach zainstalowane w globalnej pamięci podręcznej.</span><span class="sxs-lookup"><span data-stu-id="f4de1-103">Represents an enumerator for the referenced assemblies installed in the global assembly cache.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f4de1-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="f4de1-104">Syntax</span></span>  
  
```  
interface IInstallReferenceEnum : IUnknown {  
    HRESULT GetNextInstallReferenceItem (  
        [out] IInstallReferenceItem **ppRefItem,  
        [in]  DWORD dwFlags,  
        [in]  LPVOID pvReserved  
    );  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="f4de1-105">Metody</span><span class="sxs-lookup"><span data-stu-id="f4de1-105">Methods</span></span>  
  
|<span data-ttu-id="f4de1-106">Metoda</span><span class="sxs-lookup"><span data-stu-id="f4de1-106">Method</span></span>|<span data-ttu-id="f4de1-107">Opis</span><span class="sxs-lookup"><span data-stu-id="f4de1-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="f4de1-108">GetNextInstallReferenceItem, metoda</span><span class="sxs-lookup"><span data-stu-id="f4de1-108">GetNextInstallReferenceItem Method</span></span>](../../../../docs/framework/unmanaged-api/fusion/iinstallreferenceenum-getnextinstallreferenceitem-method.md)|<span data-ttu-id="f4de1-109">Pobiera wskaźnik do następnego `IInstallReferenceItem` zawarte w tym `IInstallReferenceEnum`.</span><span class="sxs-lookup"><span data-stu-id="f4de1-109">Gets a pointer to the next `IInstallReferenceItem` contained in this `IInstallReferenceEnum`.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="f4de1-110">Wymagania</span><span class="sxs-lookup"><span data-stu-id="f4de1-110">Requirements</span></span>  
 <span data-ttu-id="f4de1-111">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f4de1-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f4de1-112">**Nagłówek:** Fusion.h</span><span class="sxs-lookup"><span data-stu-id="f4de1-112">**Header:** Fusion.h</span></span>  
  
 <span data-ttu-id="f4de1-113">**Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f4de1-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f4de1-114">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="f4de1-114">See also</span></span>
- [<span data-ttu-id="f4de1-115">Interfejsy łączenia</span><span class="sxs-lookup"><span data-stu-id="f4de1-115">Fusion Interfaces</span></span>](../../../../docs/framework/unmanaged-api/fusion/fusion-interfaces.md)
- [<span data-ttu-id="f4de1-116">IInstallReferenceItem, interfejs</span><span class="sxs-lookup"><span data-stu-id="f4de1-116">IInstallReferenceItem Interface</span></span>](../../../../docs/framework/unmanaged-api/fusion/iinstallreferenceitem-interface.md)
