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
ms.openlocfilehash: 11821acbeeb04ae09464eb0e032b9bf387914168
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73095049"
---
# <a name="strongnamefreebuffer-function"></a><span data-ttu-id="056e5-102">StrongNameFreeBuffer — Funkcja</span><span class="sxs-lookup"><span data-stu-id="056e5-102">StrongNameFreeBuffer Function</span></span>
<span data-ttu-id="056e5-103">Zwalnia pamięć, która została przypisana przy użyciu poprzedniego wywołania funkcji silnej nazwy, takiej jak [StrongNameGetPublicKey —](strongnamegetpublickey-function.md), [StrongNameTokenFromPublicKey —](strongnametokenfrompublickey-function.md)lub [StrongNameSignatureGeneration —](strongnamesignaturegeneration-function.md).</span><span class="sxs-lookup"><span data-stu-id="056e5-103">Frees memory that was allocated with a previous call to a strong name function such as [StrongNameGetPublicKey](strongnamegetpublickey-function.md), [StrongNameTokenFromPublicKey](strongnametokenfrompublickey-function.md), or [StrongNameSignatureGeneration](strongnamesignaturegeneration-function.md).</span></span>  
  
 <span data-ttu-id="056e5-104">Ta funkcja jest przestarzała.</span><span class="sxs-lookup"><span data-stu-id="056e5-104">This function has been deprecated.</span></span> <span data-ttu-id="056e5-105">Zamiast tego użyj metody [ICLRStrongName:: StrongNameFreeBuffer —](../hosting/iclrstrongname-strongnamefreebuffer-method.md) .</span><span class="sxs-lookup"><span data-stu-id="056e5-105">Use the [ICLRStrongName::StrongNameFreeBuffer](../hosting/iclrstrongname-strongnamefreebuffer-method.md) method instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="056e5-106">Składnia</span><span class="sxs-lookup"><span data-stu-id="056e5-106">Syntax</span></span>  
  
```cpp  
VOID StrongNameFreeBuffer (   
   [in] BYTE   *pbMemory  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="056e5-107">Parametry</span><span class="sxs-lookup"><span data-stu-id="056e5-107">Parameters</span></span>  
 `pbMemory`  
 <span data-ttu-id="056e5-108">podczas Wskaźnik do pamięci do zwolnienia.</span><span class="sxs-lookup"><span data-stu-id="056e5-108">[in] A pointer to the memory to free.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="056e5-109">Wymagania</span><span class="sxs-lookup"><span data-stu-id="056e5-109">Requirements</span></span>  
 <span data-ttu-id="056e5-110">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="056e5-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="056e5-111">**Nagłówek:** StrongName. h</span><span class="sxs-lookup"><span data-stu-id="056e5-111">**Header:** StrongName.h</span></span>  
  
 <span data-ttu-id="056e5-112">**Biblioteka:** Uwzględnione jako zasób w bibliotece MsCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="056e5-112">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="056e5-113">**Wersje .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="056e5-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="056e5-114">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="056e5-114">See also</span></span>

- [<span data-ttu-id="056e5-115">StrongNameFreeBuffer, metoda</span><span class="sxs-lookup"><span data-stu-id="056e5-115">StrongNameFreeBuffer Method</span></span>](../hosting/iclrstrongname-strongnamefreebuffer-method.md)
- [<span data-ttu-id="056e5-116">ICLRStrongName, interfejs</span><span class="sxs-lookup"><span data-stu-id="056e5-116">ICLRStrongName Interface</span></span>](../hosting/iclrstrongname-interface.md)
