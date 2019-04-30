---
title: ICLRStrongName2 — Interfejs
ms.date: 03/30/2017
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 6bf9e3d2df8f507e118b393007c3958358a830cc
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61763727"
---
# <a name="iclrstrongname2-interface"></a><span data-ttu-id="2d58d-102">ICLRStrongName2 — Interfejs</span><span class="sxs-lookup"><span data-stu-id="2d58d-102">ICLRStrongName2 Interface</span></span>
<span data-ttu-id="2d58d-103">Zapewnia możliwość tworzenia silnych nazw za pomocą grupy SHA-2 algorytmów wyznaczania wartości skrótu Secure (SHA-256, SHA-384 i SHA-512).</span><span class="sxs-lookup"><span data-stu-id="2d58d-103">Provides the ability to create strong names using the SHA-2 group of Secure Hash Algorithms (SHA-256, SHA-384, and SHA-512).</span></span>  
  
## <a name="methods"></a><span data-ttu-id="2d58d-104">Metody</span><span class="sxs-lookup"><span data-stu-id="2d58d-104">Methods</span></span>  
  
|<span data-ttu-id="2d58d-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="2d58d-105">Method</span></span>|<span data-ttu-id="2d58d-106">Opis</span><span class="sxs-lookup"><span data-stu-id="2d58d-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="2d58d-107">StrongNameGetPublicKeyEx, metoda</span><span class="sxs-lookup"><span data-stu-id="2d58d-107">StrongNameGetPublicKeyEx Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/strongnamegetpublickeyex-method.md)|<span data-ttu-id="2d58d-108">Pobiera klucz publiczny z pary kluczy publiczny/prywatny, a następnie określa algorytm wyznaczania wartości skrótu i algorytm podpisu.</span><span class="sxs-lookup"><span data-stu-id="2d58d-108">Gets the public key from a public/private key pair, and specifies a hash algorithm and a signature algorithm.</span></span>|  
|[<span data-ttu-id="2d58d-109">StrongNameSignatureVerificationEx2, metoda</span><span class="sxs-lookup"><span data-stu-id="2d58d-109">StrongNameSignatureVerificationEx2 Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/strongnamesignatureverificationex2-method.md)|<span data-ttu-id="2d58d-110">Weryfikuje podpis zestaw o silnej nazwie, a następnie udostępnia mapowanie klucz ECMA do rzeczywistego klucza.</span><span class="sxs-lookup"><span data-stu-id="2d58d-110">Verifies the signature of a strongly named assembly, and provides a mapping from the ECMA key to a real key.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="2d58d-111">Uwagi</span><span class="sxs-lookup"><span data-stu-id="2d58d-111">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2d58d-112">Wymagania</span><span class="sxs-lookup"><span data-stu-id="2d58d-112">Requirements</span></span>  
 <span data-ttu-id="2d58d-113">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2d58d-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2d58d-114">**Nagłówek:** MetaHost.h</span><span class="sxs-lookup"><span data-stu-id="2d58d-114">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="2d58d-115">**Biblioteka:** Dołączony jako zasób w MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="2d58d-115">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="2d58d-116">**Wersje programu .NET framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2d58d-116">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>
