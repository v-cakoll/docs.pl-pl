---
title: StrongNameFreeBuffer — Funkcja
ms.date: 03/30/2017
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 9bfc6491a1d18c81a44a7d9c5084f744c9b76281
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59072581"
---
# <a name="strongnamefreebuffer-function"></a><span data-ttu-id="291ed-102">StrongNameFreeBuffer — Funkcja</span><span class="sxs-lookup"><span data-stu-id="291ed-102">StrongNameFreeBuffer Function</span></span>
<span data-ttu-id="291ed-103">Zwalnia pamięć, która została przydzielona z poprzedniego wywołania do funkcji silnej nazwy, takie jak [StrongNameGetPublicKey](../../../../docs/framework/unmanaged-api/strong-naming/strongnamegetpublickey-function.md), [StrongNameTokenFromPublicKey](../../../../docs/framework/unmanaged-api/strong-naming/strongnametokenfrompublickey-function.md), lub [StrongNameSignatureGeneration ](../../../../docs/framework/unmanaged-api/strong-naming/strongnamesignaturegeneration-function.md).</span><span class="sxs-lookup"><span data-stu-id="291ed-103">Frees memory that was allocated with a previous call to a strong name function such as [StrongNameGetPublicKey](../../../../docs/framework/unmanaged-api/strong-naming/strongnamegetpublickey-function.md), [StrongNameTokenFromPublicKey](../../../../docs/framework/unmanaged-api/strong-naming/strongnametokenfrompublickey-function.md), or [StrongNameSignatureGeneration](../../../../docs/framework/unmanaged-api/strong-naming/strongnamesignaturegeneration-function.md).</span></span>  
  
 <span data-ttu-id="291ed-104">Ta funkcja jest przestarzała.</span><span class="sxs-lookup"><span data-stu-id="291ed-104">This function has been deprecated.</span></span> <span data-ttu-id="291ed-105">Użyj [iclrstrongname::strongnamefreebuffer —](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamefreebuffer-method.md) metody zamiast tego.</span><span class="sxs-lookup"><span data-stu-id="291ed-105">Use the [ICLRStrongName::StrongNameFreeBuffer](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamefreebuffer-method.md) method instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="291ed-106">Składnia</span><span class="sxs-lookup"><span data-stu-id="291ed-106">Syntax</span></span>  
  
```  
VOID StrongNameFreeBuffer (   
   [in] BYTE   *pbMemory  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="291ed-107">Parametry</span><span class="sxs-lookup"><span data-stu-id="291ed-107">Parameters</span></span>  
 `pbMemory`  
 <span data-ttu-id="291ed-108">[in] Wskaźnik do pamięci, aby zwolnić.</span><span class="sxs-lookup"><span data-stu-id="291ed-108">[in] A pointer to the memory to free.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="291ed-109">Wymagania</span><span class="sxs-lookup"><span data-stu-id="291ed-109">Requirements</span></span>  
 <span data-ttu-id="291ed-110">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="291ed-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="291ed-111">**Nagłówek:** StrongName.h</span><span class="sxs-lookup"><span data-stu-id="291ed-111">**Header:** StrongName.h</span></span>  
  
 <span data-ttu-id="291ed-112">**Biblioteka:** Dołączony jako zasób w MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="291ed-112">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 **<span data-ttu-id="291ed-113">Wersje programu .NET framework:</span><span class="sxs-lookup"><span data-stu-id="291ed-113">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="291ed-114">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="291ed-114">See also</span></span>

- [<span data-ttu-id="291ed-115">StrongNameFreeBuffer, metoda</span><span class="sxs-lookup"><span data-stu-id="291ed-115">StrongNameFreeBuffer Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamefreebuffer-method.md)
- [<span data-ttu-id="291ed-116">ICLRStrongName — Interfejs</span><span class="sxs-lookup"><span data-stu-id="291ed-116">ICLRStrongName Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
