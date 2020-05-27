---
title: ITypeName::GetModifiers — Metoda
ms.date: 03/30/2017
api_name:
- ITypeName.GetModifiers
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- GetModifiers
helpviewer_keywords:
- ITypeName::GetModifiers method [.NET Framework hosting]
- GetModifiers method [.NET Framework hosting]
ms.assetid: 75508c55-3e09-4135-80da-cc811003fa82
topic_type:
- apiref
ms.openlocfilehash: 8544b8d7b1f23853465bbb2aea697dfe021d77f2
ms.sourcegitcommit: e5772b3ddcc114c80b4c9767ffdb3f6c7fad8f05
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/26/2020
ms.locfileid: "83842182"
---
# <a name="itypenamegetmodifiers-method"></a><span data-ttu-id="45489-102">ITypeName::GetModifiers — Metoda</span><span class="sxs-lookup"><span data-stu-id="45489-102">ITypeName::GetModifiers Method</span></span>
<span data-ttu-id="45489-103">Ta metoda obsługuje infrastrukturę .NET Framework i nie jest przeznaczona do użycia bezpośrednio w kodzie.</span><span class="sxs-lookup"><span data-stu-id="45489-103">This method supports the .NET Framework infrastructure and is not intended to be used directly from your code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="45489-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="45489-104">Syntax</span></span>  
  
```cpp  
HRESULT GetModifiers (  
    [in] DWORD           count,  
    [out] DWORD*         rgModifiers,  
    [out, retval] DWORD* pCount  
);  
```  
  
## <a name="requirements"></a><span data-ttu-id="45489-105">Wymagania</span><span class="sxs-lookup"><span data-stu-id="45489-105">Requirements</span></span>  
 <span data-ttu-id="45489-106">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="45489-106">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="45489-107">**Nagłówek:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="45489-107">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="45489-108">**Biblioteka:** Uwzględnione jako zasób w bibliotece MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="45489-108">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="45489-109">**.NET Framework wersje:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="45489-109">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="45489-110">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="45489-110">See also</span></span>

- [<span data-ttu-id="45489-111">Hosting, interfejsy</span><span class="sxs-lookup"><span data-stu-id="45489-111">Hosting Interfaces</span></span>](hosting-interfaces.md)
