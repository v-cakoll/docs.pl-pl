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
ms.openlocfilehash: 776150bdb7f7a74b6adc9a6f41bf61cae3d800ed
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54541017"
---
# <a name="strongnamefreebuffer-function"></a><span data-ttu-id="f5324-102">StrongNameFreeBuffer — Funkcja</span><span class="sxs-lookup"><span data-stu-id="f5324-102">StrongNameFreeBuffer Function</span></span>
<span data-ttu-id="f5324-103">Zwalnia pamięć, która została przydzielona z poprzedniego wywołania do funkcji silnej nazwy, takie jak [StrongNameGetPublicKey](../../../../docs/framework/unmanaged-api/strong-naming/strongnamegetpublickey-function.md), [StrongNameTokenFromPublicKey](../../../../docs/framework/unmanaged-api/strong-naming/strongnametokenfrompublickey-function.md), lub [StrongNameSignatureGeneration ](../../../../docs/framework/unmanaged-api/strong-naming/strongnamesignaturegeneration-function.md).</span><span class="sxs-lookup"><span data-stu-id="f5324-103">Frees memory that was allocated with a previous call to a strong name function such as [StrongNameGetPublicKey](../../../../docs/framework/unmanaged-api/strong-naming/strongnamegetpublickey-function.md), [StrongNameTokenFromPublicKey](../../../../docs/framework/unmanaged-api/strong-naming/strongnametokenfrompublickey-function.md), or [StrongNameSignatureGeneration](../../../../docs/framework/unmanaged-api/strong-naming/strongnamesignaturegeneration-function.md).</span></span>  
  
 <span data-ttu-id="f5324-104">Ta funkcja jest przestarzała.</span><span class="sxs-lookup"><span data-stu-id="f5324-104">This function has been deprecated.</span></span> <span data-ttu-id="f5324-105">Użyj [iclrstrongname::strongnamefreebuffer —](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamefreebuffer-method.md) metody zamiast tego.</span><span class="sxs-lookup"><span data-stu-id="f5324-105">Use the [ICLRStrongName::StrongNameFreeBuffer](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamefreebuffer-method.md) method instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f5324-106">Składnia</span><span class="sxs-lookup"><span data-stu-id="f5324-106">Syntax</span></span>  
  
```  
VOID StrongNameFreeBuffer (   
   [in] BYTE   *pbMemory  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="f5324-107">Parametry</span><span class="sxs-lookup"><span data-stu-id="f5324-107">Parameters</span></span>  
 `pbMemory`  
 <span data-ttu-id="f5324-108">[in] Wskaźnik do pamięci, aby zwolnić.</span><span class="sxs-lookup"><span data-stu-id="f5324-108">[in] A pointer to the memory to free.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f5324-109">Wymagania</span><span class="sxs-lookup"><span data-stu-id="f5324-109">Requirements</span></span>  
 <span data-ttu-id="f5324-110">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f5324-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f5324-111">**Nagłówek:** StrongName.h</span><span class="sxs-lookup"><span data-stu-id="f5324-111">**Header:** StrongName.h</span></span>  
  
 <span data-ttu-id="f5324-112">**Biblioteka:** Dołączony jako zasób w MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="f5324-112">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="f5324-113">**Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f5324-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f5324-114">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="f5324-114">See also</span></span>
- [<span data-ttu-id="f5324-115">StrongNameFreeBuffer, metoda</span><span class="sxs-lookup"><span data-stu-id="f5324-115">StrongNameFreeBuffer Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamefreebuffer-method.md)
- [<span data-ttu-id="f5324-116">ICLRStrongName, interfejs</span><span class="sxs-lookup"><span data-stu-id="f5324-116">ICLRStrongName Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
