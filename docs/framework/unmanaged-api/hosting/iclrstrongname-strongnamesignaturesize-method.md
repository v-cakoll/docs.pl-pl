---
title: ICLRStrongName::StrongNameSignatureSize — Metoda
ms.date: 03/30/2017
api_name:
- ICLRStrongName.StrongNameSignatureSize
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRStrongName::StrongNameSignatureSize
helpviewer_keywords:
- ICLRStrongName::StrongNameSignatureSize method [.NET Framework hosting]
- StrongNameSignatureSize method, ICLRStrongName interface [.NET Framework hosting]
ms.assetid: 76d4f93a-5e25-4399-abcc-a1389549481d
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: b0c81b51deb6affb3dd39677184ea0a4b2e6ff61
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59219983"
---
# <a name="iclrstrongnamestrongnamesignaturesize-method"></a><span data-ttu-id="46ba2-102">ICLRStrongName::StrongNameSignatureSize — Metoda</span><span class="sxs-lookup"><span data-stu-id="46ba2-102">ICLRStrongName::StrongNameSignatureSize Method</span></span>
<span data-ttu-id="46ba2-103">Zwraca rozmiar podpisu silnej nazwy.</span><span class="sxs-lookup"><span data-stu-id="46ba2-103">Returns the size of the strong name signature.</span></span> <span data-ttu-id="46ba2-104">Ta metoda jest zwykle używana przez kompilatory, aby określić, ile miejsca do zarezerwowania w pliku, podczas tworzenia zestawu podpisanego z opóźnieniem.</span><span class="sxs-lookup"><span data-stu-id="46ba2-104">This method is typically used by compilers to determine how much space to reserve in the file when creating a delay-signed assembly.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="46ba2-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="46ba2-105">Syntax</span></span>  
  
```  
HRESULT StrongNameSignatureSize (   
    [in]  BYTE   *pbPublicKeyBlob,  
    [in]  ULONG  cbPublicKeyBlob,   
    [in]  DWORD  *pcbSize  
);   
```  
  
## <a name="parameters"></a><span data-ttu-id="46ba2-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="46ba2-106">Parameters</span></span>  
 `pbPublicKeyBlob`  
 <span data-ttu-id="46ba2-107">[in] Struktury typu [publickeyblob —](../../../../docs/framework/unmanaged-api/strong-naming/publickeyblob-structure.md) zawierający publiczną część pary kluczy używanego do generowania podpisu silnej nazwy.</span><span class="sxs-lookup"><span data-stu-id="46ba2-107">[in] A structure of type [PublicKeyBlob](../../../../docs/framework/unmanaged-api/strong-naming/publickeyblob-structure.md) that contains the public portion of the key pair used to generate the strong name signature.</span></span>  
  
 `cbPublicKeyBlob`  
 <span data-ttu-id="46ba2-108">[in] Rozmiar w bajtach z `pbPublicKeyBlob`.</span><span class="sxs-lookup"><span data-stu-id="46ba2-108">[in] The size, in bytes, of `pbPublicKeyBlob`.</span></span>  
  
 `pcbSize`  
 <span data-ttu-id="46ba2-109">[in] Liczba bajtów potrzebnych do przechowania podpisu silnej nazwy.</span><span class="sxs-lookup"><span data-stu-id="46ba2-109">[in] The number of bytes required to store the strong name signature.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="46ba2-110">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="46ba2-110">Return Value</span></span>  
 `S_OK` <span data-ttu-id="46ba2-111">Jeśli metoda została ukończona pomyślnie; w przeciwnym razie wartość HRESULT, która wskazuje błąd (zobacz [typowe wartości HRESULT](https://go.microsoft.com/fwlink/?LinkId=213878) dla listy).</span><span class="sxs-lookup"><span data-stu-id="46ba2-111">if the method completed successfully; otherwise, an HRESULT value that indicates failure (see [Common HRESULT Values](https://go.microsoft.com/fwlink/?LinkId=213878) for a list).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="46ba2-112">Wymagania</span><span class="sxs-lookup"><span data-stu-id="46ba2-112">Requirements</span></span>  
 <span data-ttu-id="46ba2-113">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="46ba2-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="46ba2-114">**Nagłówek:** MetaHost.h</span><span class="sxs-lookup"><span data-stu-id="46ba2-114">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="46ba2-115">**Biblioteka:** Dołączony jako zasób w MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="46ba2-115">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 **<span data-ttu-id="46ba2-116">Wersje programu .NET framework:</span><span class="sxs-lookup"><span data-stu-id="46ba2-116">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="46ba2-117">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="46ba2-117">See also</span></span>

- [<span data-ttu-id="46ba2-118">ICLRStrongName — Interfejs</span><span class="sxs-lookup"><span data-stu-id="46ba2-118">ICLRStrongName Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
