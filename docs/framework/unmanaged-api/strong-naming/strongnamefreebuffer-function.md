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
ms.openlocfilehash: 639664c6ce5714b554f30bff2569a12bf48d1671
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/07/2019
ms.locfileid: "70799127"
---
# <a name="strongnamefreebuffer-function"></a><span data-ttu-id="c3b7c-102">StrongNameFreeBuffer — Funkcja</span><span class="sxs-lookup"><span data-stu-id="c3b7c-102">StrongNameFreeBuffer Function</span></span>
<span data-ttu-id="c3b7c-103">Zwalnia pamięć, która została przypisana przy użyciu poprzedniego wywołania funkcji silnej nazwy, takiej jak [StrongNameGetPublicKey —](strongnamegetpublickey-function.md), [StrongNameTokenFromPublicKey —](strongnametokenfrompublickey-function.md)lub [StrongNameSignatureGeneration —](strongnamesignaturegeneration-function.md).</span><span class="sxs-lookup"><span data-stu-id="c3b7c-103">Frees memory that was allocated with a previous call to a strong name function such as [StrongNameGetPublicKey](strongnamegetpublickey-function.md), [StrongNameTokenFromPublicKey](strongnametokenfrompublickey-function.md), or [StrongNameSignatureGeneration](strongnamesignaturegeneration-function.md).</span></span>  
  
 <span data-ttu-id="c3b7c-104">Ta funkcja jest przestarzała.</span><span class="sxs-lookup"><span data-stu-id="c3b7c-104">This function has been deprecated.</span></span> <span data-ttu-id="c3b7c-105">Zamiast tego użyj metody [ICLRStrongName:: StrongNameFreeBuffer —](../hosting/iclrstrongname-strongnamefreebuffer-method.md) .</span><span class="sxs-lookup"><span data-stu-id="c3b7c-105">Use the [ICLRStrongName::StrongNameFreeBuffer](../hosting/iclrstrongname-strongnamefreebuffer-method.md) method instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c3b7c-106">Składnia</span><span class="sxs-lookup"><span data-stu-id="c3b7c-106">Syntax</span></span>  
  
```cpp  
VOID StrongNameFreeBuffer (   
   [in] BYTE   *pbMemory  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="c3b7c-107">Parametry</span><span class="sxs-lookup"><span data-stu-id="c3b7c-107">Parameters</span></span>  
 `pbMemory`  
 <span data-ttu-id="c3b7c-108">podczas Wskaźnik do pamięci do zwolnienia.</span><span class="sxs-lookup"><span data-stu-id="c3b7c-108">[in] A pointer to the memory to free.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c3b7c-109">Wymagania</span><span class="sxs-lookup"><span data-stu-id="c3b7c-109">Requirements</span></span>  
 <span data-ttu-id="c3b7c-110">**Poszczególnych** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c3b7c-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c3b7c-111">**Nagłówki** StrongName.h</span><span class="sxs-lookup"><span data-stu-id="c3b7c-111">**Header:** StrongName.h</span></span>  
  
 <span data-ttu-id="c3b7c-112">**Biblioteki** Uwzględnione jako zasób w bibliotece MsCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="c3b7c-112">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="c3b7c-113">**.NET Framework wersje:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c3b7c-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c3b7c-114">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="c3b7c-114">See also</span></span>

- [<span data-ttu-id="c3b7c-115">StrongNameFreeBuffer, metoda</span><span class="sxs-lookup"><span data-stu-id="c3b7c-115">StrongNameFreeBuffer Method</span></span>](../hosting/iclrstrongname-strongnamefreebuffer-method.md)
- [<span data-ttu-id="c3b7c-116">ICLRStrongName, interfejs</span><span class="sxs-lookup"><span data-stu-id="c3b7c-116">ICLRStrongName Interface</span></span>](../hosting/iclrstrongname-interface.md)
