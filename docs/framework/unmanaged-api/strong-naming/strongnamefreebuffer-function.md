---
title: "StrongNameFreeBuffer — Funkcja"
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
- StrongNameFreeBuffer
api_location:
- mscoree.dll
- mscorsn.dll
- clr.dll
- mscorwks.dll
- mscoreei.dll
api_type:
- DLLExport
f1_keywords:
- StrongNameFreeBuffer
helpviewer_keywords:
- StrongNameFreeBuffer function [.NET Framework strong naming]
ms.assetid: eda21ecf-4734-4f92-aaba-9f34884385db
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: f4f5bde035b0ab9df07bb0ab709a67ae1a4cff3f
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="strongnamefreebuffer-function"></a><span data-ttu-id="88542-102">StrongNameFreeBuffer — Funkcja</span><span class="sxs-lookup"><span data-stu-id="88542-102">StrongNameFreeBuffer Function</span></span>
<span data-ttu-id="88542-103">Zwalnia pamięć, która została przydzielona z poprzedniego wywołania funkcji silnej nazwy, takie jak [StrongNameGetPublicKey](../../../../docs/framework/unmanaged-api/strong-naming/strongnamegetpublickey-function.md), [StrongNameTokenFromPublicKey](../../../../docs/framework/unmanaged-api/strong-naming/strongnametokenfrompublickey-function.md), lub [StrongNameSignatureGeneration ](../../../../docs/framework/unmanaged-api/strong-naming/strongnamesignaturegeneration-function.md).</span><span class="sxs-lookup"><span data-stu-id="88542-103">Frees memory that was allocated with a previous call to a strong name function such as [StrongNameGetPublicKey](../../../../docs/framework/unmanaged-api/strong-naming/strongnamegetpublickey-function.md), [StrongNameTokenFromPublicKey](../../../../docs/framework/unmanaged-api/strong-naming/strongnametokenfrompublickey-function.md), or [StrongNameSignatureGeneration](../../../../docs/framework/unmanaged-api/strong-naming/strongnamesignaturegeneration-function.md).</span></span>  
  
 <span data-ttu-id="88542-104">Ta funkcja jest przestarzała.</span><span class="sxs-lookup"><span data-stu-id="88542-104">This function has been deprecated.</span></span> <span data-ttu-id="88542-105">Użyj [ICLRStrongName::StrongNameFreeBuffer](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamefreebuffer-method.md) metody zamiast tego.</span><span class="sxs-lookup"><span data-stu-id="88542-105">Use the [ICLRStrongName::StrongNameFreeBuffer](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamefreebuffer-method.md) method instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="88542-106">Składnia</span><span class="sxs-lookup"><span data-stu-id="88542-106">Syntax</span></span>  
  
```  
VOID StrongNameFreeBuffer (   
   [in] BYTE   *pbMemory  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="88542-107">Parametry</span><span class="sxs-lookup"><span data-stu-id="88542-107">Parameters</span></span>  
 `pbMemory`  
 <span data-ttu-id="88542-108">[in] Wskaźnik do pamięci w celu zwolnienia.</span><span class="sxs-lookup"><span data-stu-id="88542-108">[in] A pointer to the memory to free.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="88542-109">Wymagania</span><span class="sxs-lookup"><span data-stu-id="88542-109">Requirements</span></span>  
 <span data-ttu-id="88542-110">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="88542-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="88542-111">**Nagłówek:** StrongName.h</span><span class="sxs-lookup"><span data-stu-id="88542-111">**Header:** StrongName.h</span></span>  
  
 <span data-ttu-id="88542-112">**Biblioteka:** uwzględnione jako zasób w MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="88542-112">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="88542-113">**Wersje programu .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="88542-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="88542-114">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="88542-114">See Also</span></span>  
 [<span data-ttu-id="88542-115">StrongNameFreeBuffer, metoda</span><span class="sxs-lookup"><span data-stu-id="88542-115">StrongNameFreeBuffer Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamefreebuffer-method.md)  
 [<span data-ttu-id="88542-116">ICLRStrongName, interfejs</span><span class="sxs-lookup"><span data-stu-id="88542-116">ICLRStrongName Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
