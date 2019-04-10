---
title: ITypeNameFactory::ParseTypeName — Metoda
ms.date: 03/30/2017
api_name:
- ITypeNameFactory.ParseTypeName
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ParseTypeName
helpviewer_keywords:
- ITypeNameFactory::ParseTypeName method [.NET Framework hosting]
- ParseTypeName method [.NET Framework hosting]
ms.assetid: 13c9f063-371c-4911-a5e7-e1e0b88ae382
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: cbe5f634a5d0580c7e58b03f318da98a0112fa6b
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59208088"
---
# <a name="itypenamefactoryparsetypename-method"></a><span data-ttu-id="e85eb-102">ITypeNameFactory::ParseTypeName — Metoda</span><span class="sxs-lookup"><span data-stu-id="e85eb-102">ITypeNameFactory::ParseTypeName Method</span></span>
<span data-ttu-id="e85eb-103">Ta metoda obsługuje infrastrukturę .NET Framework i nie jest przeznaczona do użycia bezpośrednio w kodzie.</span><span class="sxs-lookup"><span data-stu-id="e85eb-103">This method supports the .NET Framework infrastructure and is not intended to be used directly from your code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e85eb-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="e85eb-104">Syntax</span></span>  
  
```  
HRESULT ParseTypeName (  
    [in]  LPCWSTR             szName,  
    [out] DWORD*              pError,  
    [out, retval] ITypeName** ppTypeName  
);  
```  
  
## <a name="requirements"></a><span data-ttu-id="e85eb-105">Wymagania</span><span class="sxs-lookup"><span data-stu-id="e85eb-105">Requirements</span></span>  
 <span data-ttu-id="e85eb-106">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e85eb-106">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e85eb-107">**Nagłówek:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="e85eb-107">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="e85eb-108">**Biblioteka:** Dołączony jako zasób w MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="e85eb-108">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 **<span data-ttu-id="e85eb-109">Wersje programu .NET framework:</span><span class="sxs-lookup"><span data-stu-id="e85eb-109">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="e85eb-110">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="e85eb-110">See also</span></span>

- [<span data-ttu-id="e85eb-111">Hosting — Interfejsy</span><span class="sxs-lookup"><span data-stu-id="e85eb-111">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
