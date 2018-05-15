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
ms.openlocfilehash: 1a129608370cd72967e0c441eff12b4aca7e638c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="strongnamefreebuffer-function"></a><span data-ttu-id="a426c-102">StrongNameFreeBuffer — Funkcja</span><span class="sxs-lookup"><span data-stu-id="a426c-102">StrongNameFreeBuffer Function</span></span>
<span data-ttu-id="a426c-103">Zwalnia pamięć, która została przydzielona z poprzedniego wywołania funkcji silnej nazwy, takie jak [StrongNameGetPublicKey](../../../../docs/framework/unmanaged-api/strong-naming/strongnamegetpublickey-function.md), [StrongNameTokenFromPublicKey](../../../../docs/framework/unmanaged-api/strong-naming/strongnametokenfrompublickey-function.md), lub [StrongNameSignatureGeneration ](../../../../docs/framework/unmanaged-api/strong-naming/strongnamesignaturegeneration-function.md).</span><span class="sxs-lookup"><span data-stu-id="a426c-103">Frees memory that was allocated with a previous call to a strong name function such as [StrongNameGetPublicKey](../../../../docs/framework/unmanaged-api/strong-naming/strongnamegetpublickey-function.md), [StrongNameTokenFromPublicKey](../../../../docs/framework/unmanaged-api/strong-naming/strongnametokenfrompublickey-function.md), or [StrongNameSignatureGeneration](../../../../docs/framework/unmanaged-api/strong-naming/strongnamesignaturegeneration-function.md).</span></span>  
  
 <span data-ttu-id="a426c-104">Ta funkcja jest przestarzała.</span><span class="sxs-lookup"><span data-stu-id="a426c-104">This function has been deprecated.</span></span> <span data-ttu-id="a426c-105">Użyj [ICLRStrongName::StrongNameFreeBuffer](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamefreebuffer-method.md) metody zamiast tego.</span><span class="sxs-lookup"><span data-stu-id="a426c-105">Use the [ICLRStrongName::StrongNameFreeBuffer](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamefreebuffer-method.md) method instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a426c-106">Składnia</span><span class="sxs-lookup"><span data-stu-id="a426c-106">Syntax</span></span>  
  
```  
VOID StrongNameFreeBuffer (   
   [in] BYTE   *pbMemory  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="a426c-107">Parametry</span><span class="sxs-lookup"><span data-stu-id="a426c-107">Parameters</span></span>  
 `pbMemory`  
 <span data-ttu-id="a426c-108">[in] Wskaźnik do pamięci w celu zwolnienia.</span><span class="sxs-lookup"><span data-stu-id="a426c-108">[in] A pointer to the memory to free.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a426c-109">Wymagania</span><span class="sxs-lookup"><span data-stu-id="a426c-109">Requirements</span></span>  
 <span data-ttu-id="a426c-110">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a426c-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a426c-111">**Nagłówek:** StrongName.h</span><span class="sxs-lookup"><span data-stu-id="a426c-111">**Header:** StrongName.h</span></span>  
  
 <span data-ttu-id="a426c-112">**Biblioteka:** uwzględnione jako zasób w MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="a426c-112">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="a426c-113">**Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a426c-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a426c-114">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="a426c-114">See Also</span></span>  
 [<span data-ttu-id="a426c-115">StrongNameFreeBuffer, metoda</span><span class="sxs-lookup"><span data-stu-id="a426c-115">StrongNameFreeBuffer Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamefreebuffer-method.md)  
 [<span data-ttu-id="a426c-116">ICLRStrongName, interfejs</span><span class="sxs-lookup"><span data-stu-id="a426c-116">ICLRStrongName Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
