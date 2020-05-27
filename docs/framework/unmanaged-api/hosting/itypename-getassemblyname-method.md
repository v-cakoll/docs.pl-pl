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
ms.openlocfilehash: 0c8f540e5d835b4874cc55b789804d0ce30f208d
ms.sourcegitcommit: e5772b3ddcc114c80b4c9767ffdb3f6c7fad8f05
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/26/2020
ms.locfileid: "83842208"
---
# <a name="itypenamegetassemblyname-method"></a><span data-ttu-id="a22c9-102">ITypeName::GetAssemblyName — Metoda</span><span class="sxs-lookup"><span data-stu-id="a22c9-102">ITypeName::GetAssemblyName Method</span></span>
<span data-ttu-id="a22c9-103">Ta metoda obsługuje infrastrukturę .NET Framework i nie jest przeznaczona do użycia bezpośrednio w kodzie.</span><span class="sxs-lookup"><span data-stu-id="a22c9-103">This method supports the .NET Framework infrastructure and is not intended to be used directly from your code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a22c9-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="a22c9-104">Syntax</span></span>  
  
```cpp  
HRESULT GetAssemblyName (  
    [out, retval] BSTR* rgbszAssemblyNames  
);  
```  
  
## <a name="requirements"></a><span data-ttu-id="a22c9-105">Wymagania</span><span class="sxs-lookup"><span data-stu-id="a22c9-105">Requirements</span></span>  
 <span data-ttu-id="a22c9-106">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a22c9-106">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a22c9-107">**Nagłówek:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="a22c9-107">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="a22c9-108">**Biblioteka:** Uwzględnione jako zasób w bibliotece MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="a22c9-108">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="a22c9-109">**.NET Framework wersje:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a22c9-109">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a22c9-110">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="a22c9-110">See also</span></span>

- [<span data-ttu-id="a22c9-111">Hosting, interfejsy</span><span class="sxs-lookup"><span data-stu-id="a22c9-111">Hosting Interfaces</span></span>](hosting-interfaces.md)
