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
ms.openlocfilehash: 5781254b508887f2e76f6ca0eca6a2830ada172b
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/10/2019
ms.locfileid: "67774017"
---
# <a name="iinstallreferenceenum-interface"></a><span data-ttu-id="bb512-102">IInstallReferenceEnum — Interfejs</span><span class="sxs-lookup"><span data-stu-id="bb512-102">IInstallReferenceEnum Interface</span></span>
<span data-ttu-id="bb512-103">Reprezentuje moduł wyliczający przywoływanych zestawach zainstalowane w globalnej pamięci podręcznej.</span><span class="sxs-lookup"><span data-stu-id="bb512-103">Represents an enumerator for the referenced assemblies installed in the global assembly cache.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bb512-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="bb512-104">Syntax</span></span>  
  
```cpp  
interface IInstallReferenceEnum : IUnknown {  
    HRESULT GetNextInstallReferenceItem (  
        [out] IInstallReferenceItem **ppRefItem,  
        [in]  DWORD dwFlags,  
        [in]  LPVOID pvReserved  
    );  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="bb512-105">Metody</span><span class="sxs-lookup"><span data-stu-id="bb512-105">Methods</span></span>  
  
|<span data-ttu-id="bb512-106">Metoda</span><span class="sxs-lookup"><span data-stu-id="bb512-106">Method</span></span>|<span data-ttu-id="bb512-107">Opis</span><span class="sxs-lookup"><span data-stu-id="bb512-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="bb512-108">GetNextInstallReferenceItem, metoda</span><span class="sxs-lookup"><span data-stu-id="bb512-108">GetNextInstallReferenceItem Method</span></span>](../../../../docs/framework/unmanaged-api/fusion/iinstallreferenceenum-getnextinstallreferenceitem-method.md)|<span data-ttu-id="bb512-109">Pobiera wskaźnik do następnego `IInstallReferenceItem` zawarte w tym `IInstallReferenceEnum`.</span><span class="sxs-lookup"><span data-stu-id="bb512-109">Gets a pointer to the next `IInstallReferenceItem` contained in this `IInstallReferenceEnum`.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="bb512-110">Wymagania</span><span class="sxs-lookup"><span data-stu-id="bb512-110">Requirements</span></span>  
 <span data-ttu-id="bb512-111">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="bb512-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="bb512-112">**Nagłówek:** Fusion.h</span><span class="sxs-lookup"><span data-stu-id="bb512-112">**Header:** Fusion.h</span></span>  
  
 <span data-ttu-id="bb512-113">**Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="bb512-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bb512-114">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="bb512-114">See also</span></span>

- [<span data-ttu-id="bb512-115">Interfejsy łączenia</span><span class="sxs-lookup"><span data-stu-id="bb512-115">Fusion Interfaces</span></span>](../../../../docs/framework/unmanaged-api/fusion/fusion-interfaces.md)
- [<span data-ttu-id="bb512-116">IInstallReferenceItem, interfejs</span><span class="sxs-lookup"><span data-stu-id="bb512-116">IInstallReferenceItem Interface</span></span>](../../../../docs/framework/unmanaged-api/fusion/iinstallreferenceitem-interface.md)
