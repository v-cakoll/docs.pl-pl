---
title: ICLRReferenceAssemblyEnum — Interfejs
ms.date: 03/30/2017
api_name:
- ICLRReferenceAssemblyEnum
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRReferenceAssemblyEnum
helpviewer_keywords:
- ICLRReferenceAssemblyEnum interface [.NET Framework hosting]
ms.assetid: 8adbf092-c3ba-4bee-b25b-0de6e43a4ce5
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 32f27d6c15a99282eee20d2563a4ca741238d846
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61638518"
---
# <a name="iclrreferenceassemblyenum-interface"></a><span data-ttu-id="52847-102">ICLRReferenceAssemblyEnum — Interfejs</span><span class="sxs-lookup"><span data-stu-id="52847-102">ICLRReferenceAssemblyEnum Interface</span></span>
<span data-ttu-id="52847-103">Udostępnia metody, które umożliwiają hosta do manipulowania zbiór zestawów, które odwołuje się do pliku lub strumienia przy użyciu danych tożsamości zestawu, które jest wewnętrznym środowisko uruchomieniowe języka wspólnego (CLR), bez konieczności tworzenia lub zrozumienie tych tożsamości.</span><span class="sxs-lookup"><span data-stu-id="52847-103">Provides methods that allow the host to manipulate the set of assemblies referenced by a file or stream using assembly identity data that is internal to the common language runtime (CLR), without needing to create or understand those identities.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="52847-104">Metody</span><span class="sxs-lookup"><span data-stu-id="52847-104">Methods</span></span>  
  
|<span data-ttu-id="52847-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="52847-105">Method</span></span>|<span data-ttu-id="52847-106">Opis</span><span class="sxs-lookup"><span data-stu-id="52847-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="52847-107">Get, metoda</span><span class="sxs-lookup"><span data-stu-id="52847-107">Get Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrreferenceassemblyenum-get-method.md)|<span data-ttu-id="52847-108">Pobiera tożsamość zestawu o podany indeks.</span><span class="sxs-lookup"><span data-stu-id="52847-108">Gets the assembly identity at the supplied index.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="52847-109">Wymagania</span><span class="sxs-lookup"><span data-stu-id="52847-109">Requirements</span></span>  
 <span data-ttu-id="52847-110">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="52847-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="52847-111">**Nagłówek:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="52847-111">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="52847-112">**Biblioteka:** Dołączony jako zasób w MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="52847-112">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="52847-113">**Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="52847-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="52847-114">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="52847-114">See also</span></span>

- [<span data-ttu-id="52847-115">ICLRAssemblyIdentityManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="52847-115">ICLRAssemblyIdentityManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyidentitymanager-interface.md)
- [<span data-ttu-id="52847-116">ICLRAssemblyReferenceList, interfejs</span><span class="sxs-lookup"><span data-stu-id="52847-116">ICLRAssemblyReferenceList Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyreferencelist-interface.md)
- [<span data-ttu-id="52847-117">Hosting, interfejsy</span><span class="sxs-lookup"><span data-stu-id="52847-117">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
