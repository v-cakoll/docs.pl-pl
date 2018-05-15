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
ms.openlocfilehash: cac9f9db0b7527a80671c825a4435e8ea2d135b8
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="iinstallreferenceenum-interface"></a><span data-ttu-id="5adef-102">IInstallReferenceEnum — Interfejs</span><span class="sxs-lookup"><span data-stu-id="5adef-102">IInstallReferenceEnum Interface</span></span>
<span data-ttu-id="5adef-103">Reprezentuje moduł wyliczający dla zestawów występujących w odwołaniach zainstalowany w globalnej pamięci podręcznej zestawów.</span><span class="sxs-lookup"><span data-stu-id="5adef-103">Represents an enumerator for the referenced assemblies installed in the global assembly cache.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5adef-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="5adef-104">Syntax</span></span>  
  
```  
interface IInstallReferenceEnum : IUnknown {  
    HRESULT GetNextInstallReferenceItem (  
        [out] IInstallReferenceItem **ppRefItem,  
        [in]  DWORD dwFlags,  
        [in]  LPVOID pvReserved  
    );  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="5adef-105">Metody</span><span class="sxs-lookup"><span data-stu-id="5adef-105">Methods</span></span>  
  
|<span data-ttu-id="5adef-106">Metoda</span><span class="sxs-lookup"><span data-stu-id="5adef-106">Method</span></span>|<span data-ttu-id="5adef-107">Opis</span><span class="sxs-lookup"><span data-stu-id="5adef-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="5adef-108">GetNextInstallReferenceItem, metoda</span><span class="sxs-lookup"><span data-stu-id="5adef-108">GetNextInstallReferenceItem Method</span></span>](../../../../docs/framework/unmanaged-api/fusion/iinstallreferenceenum-getnextinstallreferenceitem-method.md)|<span data-ttu-id="5adef-109">Pobiera wskaźnik do następnego `IInstallReferenceItem` zawarte w tym `IInstallReferenceEnum`.</span><span class="sxs-lookup"><span data-stu-id="5adef-109">Gets a pointer to the next `IInstallReferenceItem` contained in this `IInstallReferenceEnum`.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="5adef-110">Wymagania</span><span class="sxs-lookup"><span data-stu-id="5adef-110">Requirements</span></span>  
 <span data-ttu-id="5adef-111">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5adef-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5adef-112">**Nagłówek:** Fusion.h</span><span class="sxs-lookup"><span data-stu-id="5adef-112">**Header:** Fusion.h</span></span>  
  
 <span data-ttu-id="5adef-113">**Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5adef-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5adef-114">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="5adef-114">See Also</span></span>  
 [<span data-ttu-id="5adef-115">Interfejsy łączenia</span><span class="sxs-lookup"><span data-stu-id="5adef-115">Fusion Interfaces</span></span>](../../../../docs/framework/unmanaged-api/fusion/fusion-interfaces.md)  
 [<span data-ttu-id="5adef-116">IInstallReferenceItem, interfejs</span><span class="sxs-lookup"><span data-stu-id="5adef-116">IInstallReferenceItem Interface</span></span>](../../../../docs/framework/unmanaged-api/fusion/iinstallreferenceitem-interface.md)
