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
ms.openlocfilehash: 9715369f4cf1b2a7078be14a2fc597f735ab6fd3
ms.sourcegitcommit: c76c8b2c39ed2f0eee422b61a2ab4c05ca7771fa
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/21/2020
ms.locfileid: "83763166"
---
# <a name="iclrstrongname2-interface"></a><span data-ttu-id="7e5ad-102">ICLRStrongName2 — Interfejs</span><span class="sxs-lookup"><span data-stu-id="7e5ad-102">ICLRStrongName2 Interface</span></span>
<span data-ttu-id="7e5ad-103">Zapewnia możliwość tworzenia silnych nazw przy użyciu grupy SHA-2 bezpiecznych algorytmów wyznaczania wartości skrótu (SHA-256, SHA-384 i SHA-512).</span><span class="sxs-lookup"><span data-stu-id="7e5ad-103">Provides the ability to create strong names using the SHA-2 group of Secure Hash Algorithms (SHA-256, SHA-384, and SHA-512).</span></span>  
  
## <a name="methods"></a><span data-ttu-id="7e5ad-104">Metody</span><span class="sxs-lookup"><span data-stu-id="7e5ad-104">Methods</span></span>  
  
|<span data-ttu-id="7e5ad-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="7e5ad-105">Method</span></span>|<span data-ttu-id="7e5ad-106">Opis</span><span class="sxs-lookup"><span data-stu-id="7e5ad-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="7e5ad-107">StrongNameGetPublicKeyEx, metoda</span><span class="sxs-lookup"><span data-stu-id="7e5ad-107">StrongNameGetPublicKeyEx Method</span></span>](strongnamegetpublickeyex-method.md)|<span data-ttu-id="7e5ad-108">Pobiera klucz publiczny z pary kluczy publiczny/prywatny i określa algorytm skrótu i algorytm podpisu.</span><span class="sxs-lookup"><span data-stu-id="7e5ad-108">Gets the public key from a public/private key pair, and specifies a hash algorithm and a signature algorithm.</span></span>|  
|[<span data-ttu-id="7e5ad-109">StrongNameSignatureVerificationEx2, metoda</span><span class="sxs-lookup"><span data-stu-id="7e5ad-109">StrongNameSignatureVerificationEx2 Method</span></span>](strongnamesignatureverificationex2-method.md)|<span data-ttu-id="7e5ad-110">Weryfikuje podpis zestawu o silnej nazwie i zapewnia mapowanie z klucza ECMA do klucza rzeczywistego.</span><span class="sxs-lookup"><span data-stu-id="7e5ad-110">Verifies the signature of a strongly named assembly, and provides a mapping from the ECMA key to a real key.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="7e5ad-111">Uwagi</span><span class="sxs-lookup"><span data-stu-id="7e5ad-111">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7e5ad-112">Wymagania</span><span class="sxs-lookup"><span data-stu-id="7e5ad-112">Requirements</span></span>  
 <span data-ttu-id="7e5ad-113">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7e5ad-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7e5ad-114">**Nagłówek:** Obiekt ServiceHost. h</span><span class="sxs-lookup"><span data-stu-id="7e5ad-114">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="7e5ad-115">**Biblioteka:** Uwzględnione jako zasób w bibliotece MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="7e5ad-115">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="7e5ad-116">**.NET Framework wersje:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7e5ad-116">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>
