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
ms.openlocfilehash: 1d00d150f98e44fb5c6484378266b7d9b238f4a9
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/27/2020
ms.locfileid: "84008589"
---
# <a name="itypenamefactoryparsetypename-method"></a><span data-ttu-id="ef563-102">ITypeNameFactory::ParseTypeName — Metoda</span><span class="sxs-lookup"><span data-stu-id="ef563-102">ITypeNameFactory::ParseTypeName Method</span></span>
<span data-ttu-id="ef563-103">Ta metoda obsługuje infrastrukturę .NET Framework i nie jest przeznaczona do użycia bezpośrednio w kodzie.</span><span class="sxs-lookup"><span data-stu-id="ef563-103">This method supports the .NET Framework infrastructure and is not intended to be used directly from your code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ef563-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="ef563-104">Syntax</span></span>  
  
```cpp  
HRESULT ParseTypeName (  
    [in]  LPCWSTR             szName,  
    [out] DWORD*              pError,  
    [out, retval] ITypeName** ppTypeName  
);  
```  
  
## <a name="requirements"></a><span data-ttu-id="ef563-105">Wymagania</span><span class="sxs-lookup"><span data-stu-id="ef563-105">Requirements</span></span>  
 <span data-ttu-id="ef563-106">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ef563-106">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ef563-107">**Nagłówek:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="ef563-107">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="ef563-108">**Biblioteka:** Uwzględnione jako zasób w bibliotece MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="ef563-108">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="ef563-109">**.NET Framework wersje:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ef563-109">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ef563-110">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="ef563-110">See also</span></span>

- [<span data-ttu-id="ef563-111">Hosting, interfejsy</span><span class="sxs-lookup"><span data-stu-id="ef563-111">Hosting Interfaces</span></span>](hosting-interfaces.md)
