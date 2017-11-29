---
title: "ITypeName::GetModifiers — Metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ITypeName.GetModifiers
api_location: mscoree.dll
api_type: COM
f1_keywords: GetModifiers
helpviewer_keywords:
- ITypeName::GetModifiers method [.NET Framework hosting]
- GetModifiers method [.NET Framework hosting]
ms.assetid: 75508c55-3e09-4135-80da-cc811003fa82
topic_type: apiref
caps.latest.revision: "7"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: a7a6bfb8a8520d390844442665e4ba5feb4dcffb
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="itypenamegetmodifiers-method"></a><span data-ttu-id="1bdaa-102">ITypeName::GetModifiers — Metoda</span><span class="sxs-lookup"><span data-stu-id="1bdaa-102">ITypeName::GetModifiers Method</span></span>
<span data-ttu-id="1bdaa-103">Ta metoda obsługuje infrastrukturę programu .NET Framework i nie jest przeznaczona do użycia bezpośrednio w kodzie.</span><span class="sxs-lookup"><span data-stu-id="1bdaa-103">This method supports the .NET Framework infrastructure and is not intended to be used directly from your code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1bdaa-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="1bdaa-104">Syntax</span></span>  
  
```  
HRESULT GetModifiers (  
    [in] DWORD           count,  
    [out] DWORD*         rgModifiers,  
    [out, retval] DWORD* pCount  
);  
```  
  
## <a name="requirements"></a><span data-ttu-id="1bdaa-105">Wymagania</span><span class="sxs-lookup"><span data-stu-id="1bdaa-105">Requirements</span></span>  
 <span data-ttu-id="1bdaa-106">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1bdaa-106">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1bdaa-107">**Nagłówek:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="1bdaa-107">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="1bdaa-108">**Biblioteka:** uwzględnione jako zasób w MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="1bdaa-108">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="1bdaa-109">**Wersje programu .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1bdaa-109">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1bdaa-110">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="1bdaa-110">See Also</span></span>  
 [<span data-ttu-id="1bdaa-111">Hosting — interfejsy</span><span class="sxs-lookup"><span data-stu-id="1bdaa-111">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
