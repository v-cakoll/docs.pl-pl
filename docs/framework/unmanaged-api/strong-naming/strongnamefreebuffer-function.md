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
ms.openlocfilehash: 50e3cc6e677de45be9256a2a818ebd6ed7d8b843
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79176919"
---
# <a name="strongnamefreebuffer-function"></a><span data-ttu-id="f9a19-102">StrongNameFreeBuffer — Funkcja</span><span class="sxs-lookup"><span data-stu-id="f9a19-102">StrongNameFreeBuffer Function</span></span>
<span data-ttu-id="f9a19-103">Zwalnia pamięć, która została przydzielona przy poprzednim wywołaniu funkcji silnej nazwy, takiej jak [StrongNameGetPublicKey](strongnamegetpublickey-function.md), [StrongNameTokenFromPublicKey](strongnametokenfrompublickey-function.md)lub [StrongNameSignatureGeneration](strongnamesignaturegeneration-function.md).</span><span class="sxs-lookup"><span data-stu-id="f9a19-103">Frees memory that was allocated with a previous call to a strong name function such as [StrongNameGetPublicKey](strongnamegetpublickey-function.md), [StrongNameTokenFromPublicKey](strongnametokenfrompublickey-function.md), or [StrongNameSignatureGeneration](strongnamesignaturegeneration-function.md).</span></span>  
  
 <span data-ttu-id="f9a19-104">Ta funkcja została przestarzała.</span><span class="sxs-lookup"><span data-stu-id="f9a19-104">This function has been deprecated.</span></span> <span data-ttu-id="f9a19-105">Zamiast tego należy użyć metody [ICLRStrongName::StrongNameFreeBuffer.](../hosting/iclrstrongname-strongnamefreebuffer-method.md)</span><span class="sxs-lookup"><span data-stu-id="f9a19-105">Use the [ICLRStrongName::StrongNameFreeBuffer](../hosting/iclrstrongname-strongnamefreebuffer-method.md) method instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f9a19-106">Składnia</span><span class="sxs-lookup"><span data-stu-id="f9a19-106">Syntax</span></span>  
  
```cpp  
VOID StrongNameFreeBuffer (
   [in] BYTE   *pbMemory  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="f9a19-107">Parametry</span><span class="sxs-lookup"><span data-stu-id="f9a19-107">Parameters</span></span>  
 `pbMemory`  
 <span data-ttu-id="f9a19-108">[w] Wskaźnik do pamięci, aby zwolnić.</span><span class="sxs-lookup"><span data-stu-id="f9a19-108">[in] A pointer to the memory to free.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f9a19-109">Wymagania</span><span class="sxs-lookup"><span data-stu-id="f9a19-109">Requirements</span></span>  
 <span data-ttu-id="f9a19-110">**Platformy:** Zobacz [Wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f9a19-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f9a19-111">**Nagłówek:** StrongName.h (Nazwa siła)-h</span><span class="sxs-lookup"><span data-stu-id="f9a19-111">**Header:** StrongName.h</span></span>  
  
 <span data-ttu-id="f9a19-112">**Biblioteka:** Uwzględnione jako zasób w pliku MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="f9a19-112">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="f9a19-113">**Wersje programu .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f9a19-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f9a19-114">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="f9a19-114">See also</span></span>

- [<span data-ttu-id="f9a19-115">StrongNameFreeBuffer, metoda</span><span class="sxs-lookup"><span data-stu-id="f9a19-115">StrongNameFreeBuffer Method</span></span>](../hosting/iclrstrongname-strongnamefreebuffer-method.md)
- [<span data-ttu-id="f9a19-116">ICLRStrongName, interfejs</span><span class="sxs-lookup"><span data-stu-id="f9a19-116">ICLRStrongName Interface</span></span>](../hosting/iclrstrongname-interface.md)
