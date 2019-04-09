---
title: ITypeName::GetAssemblyName — Metoda
ms.date: 03/30/2017
api_name:
- ITypeName.GetAssemblyName
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- GetAssemblyName
helpviewer_keywords:
- ITypeName::GetAssemblyName method [.NET Framework hosting]
- GetAssemblyName method [.NET Framework hosting]
ms.assetid: 97801d99-f5f1-4a30-882f-959827093fac
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: a02d4c157c78dfb10aa491d5b1329c7cbaa6d8c6
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59112622"
---
# <a name="itypenamegetassemblyname-method"></a><span data-ttu-id="0126c-102">ITypeName::GetAssemblyName — Metoda</span><span class="sxs-lookup"><span data-stu-id="0126c-102">ITypeName::GetAssemblyName Method</span></span>
<span data-ttu-id="0126c-103">Ta metoda obsługuje infrastrukturę .NET Framework i nie jest przeznaczona do użycia bezpośrednio w kodzie.</span><span class="sxs-lookup"><span data-stu-id="0126c-103">This method supports the .NET Framework infrastructure and is not intended to be used directly from your code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0126c-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="0126c-104">Syntax</span></span>  
  
```  
HRESULT GetAssemblyName (  
    [out, retval] BSTR* rgbszAssemblyNames  
);  
```  
  
## <a name="requirements"></a><span data-ttu-id="0126c-105">Wymagania</span><span class="sxs-lookup"><span data-stu-id="0126c-105">Requirements</span></span>  
 <span data-ttu-id="0126c-106">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0126c-106">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0126c-107">**Nagłówek:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="0126c-107">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="0126c-108">**Biblioteka:** Dołączony jako zasób w MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="0126c-108">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 **<span data-ttu-id="0126c-109">Wersje programu .NET framework:</span><span class="sxs-lookup"><span data-stu-id="0126c-109">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="0126c-110">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="0126c-110">See also</span></span>

- [<span data-ttu-id="0126c-111">Hosting — Interfejsy</span><span class="sxs-lookup"><span data-stu-id="0126c-111">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
