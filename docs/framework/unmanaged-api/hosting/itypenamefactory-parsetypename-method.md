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
ms.openlocfilehash: 3442c61fd6aea23dfcb66fe63ece0b90b61f5580
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54741746"
---
# <a name="itypenamefactoryparsetypename-method"></a><span data-ttu-id="449d4-102">ITypeNameFactory::ParseTypeName — Metoda</span><span class="sxs-lookup"><span data-stu-id="449d4-102">ITypeNameFactory::ParseTypeName Method</span></span>
<span data-ttu-id="449d4-103">Ta metoda obsługuje infrastrukturę .NET Framework i nie jest przeznaczona do użycia bezpośrednio w kodzie.</span><span class="sxs-lookup"><span data-stu-id="449d4-103">This method supports the .NET Framework infrastructure and is not intended to be used directly from your code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="449d4-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="449d4-104">Syntax</span></span>  
  
```  
HRESULT ParseTypeName (  
    [in]  LPCWSTR             szName,  
    [out] DWORD*              pError,  
    [out, retval] ITypeName** ppTypeName  
);  
```  
  
## <a name="requirements"></a><span data-ttu-id="449d4-105">Wymagania</span><span class="sxs-lookup"><span data-stu-id="449d4-105">Requirements</span></span>  
 <span data-ttu-id="449d4-106">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="449d4-106">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="449d4-107">**Nagłówek:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="449d4-107">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="449d4-108">**Biblioteka:** Dołączony jako zasób w MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="449d4-108">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="449d4-109">**Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="449d4-109">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="449d4-110">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="449d4-110">See also</span></span>
- [<span data-ttu-id="449d4-111">Hosting, interfejsy</span><span class="sxs-lookup"><span data-stu-id="449d4-111">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
