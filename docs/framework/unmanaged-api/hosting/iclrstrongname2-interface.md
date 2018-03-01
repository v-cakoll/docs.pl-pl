---
title: "ICLRStrongName2 — Interfejs"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- ICLRStrongName2
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRStrongName2
helpviewer_keywords:
- ICLRStrongName2 interface [.NET Framework hosting]
ms.assetid: 9f098a74-201e-4628-a468-8dee9ab99b4a
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: d4e1274f675ae9289faa6c530d34cd61d033aa07
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="iclrstrongname2-interface"></a><span data-ttu-id="1f6b9-102">ICLRStrongName2 — Interfejs</span><span class="sxs-lookup"><span data-stu-id="1f6b9-102">ICLRStrongName2 Interface</span></span>
<span data-ttu-id="1f6b9-103">Zapewnia możliwość tworzenia silnych nazw za pomocą grupy SHA-2 algorytmów wyznaczania wartości skrótu Secure (SHA-256, SHA-384 i SHA-512).</span><span class="sxs-lookup"><span data-stu-id="1f6b9-103">Provides the ability to create strong names using the SHA-2 group of Secure Hash Algorithms (SHA-256, SHA-384, and SHA-512).</span></span>  
  
## <a name="methods"></a><span data-ttu-id="1f6b9-104">Metody</span><span class="sxs-lookup"><span data-stu-id="1f6b9-104">Methods</span></span>  
  
|<span data-ttu-id="1f6b9-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="1f6b9-105">Method</span></span>|<span data-ttu-id="1f6b9-106">Opis</span><span class="sxs-lookup"><span data-stu-id="1f6b9-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="1f6b9-107">StrongNameGetPublicKeyEx, metoda</span><span class="sxs-lookup"><span data-stu-id="1f6b9-107">StrongNameGetPublicKeyEx Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/strongnamegetpublickeyex-method.md)|<span data-ttu-id="1f6b9-108">Pobiera klucz publiczny z pary kluczy publiczny/prywatny i określa algorytm wyznaczania wartości skrótu i algorytm podpisu.</span><span class="sxs-lookup"><span data-stu-id="1f6b9-108">Gets the public key from a public/private key pair, and specifies a hash algorithm and a signature algorithm.</span></span>|  
|[<span data-ttu-id="1f6b9-109">StrongNameSignatureVerificationEx2, metoda</span><span class="sxs-lookup"><span data-stu-id="1f6b9-109">StrongNameSignatureVerificationEx2 Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/strongnamesignatureverificationex2-method.md)|<span data-ttu-id="1f6b9-110">Weryfikuje podpis zestawu o silnej nazwie i udostępnia mapowanie z ECMA klucza do rzeczywistego klucza.</span><span class="sxs-lookup"><span data-stu-id="1f6b9-110">Verifies the signature of a strongly named assembly, and provides a mapping from the ECMA key to a real key.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="1f6b9-111">Uwagi</span><span class="sxs-lookup"><span data-stu-id="1f6b9-111">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1f6b9-112">Wymagania</span><span class="sxs-lookup"><span data-stu-id="1f6b9-112">Requirements</span></span>  
 <span data-ttu-id="1f6b9-113">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1f6b9-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1f6b9-114">**Nagłówek:** MetaHost.h</span><span class="sxs-lookup"><span data-stu-id="1f6b9-114">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="1f6b9-115">**Biblioteka:** uwzględnione jako zasób w MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="1f6b9-115">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="1f6b9-116">**Wersje programu .NET framework:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1f6b9-116">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>
