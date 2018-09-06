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
ms.openlocfilehash: dc5a40a0e26f116ce1700973a5000e8d6bbbd890
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/05/2018
ms.locfileid: "43732946"
---
# <a name="iclrstrongnamestrongnamesignaturesize-method"></a><span data-ttu-id="406b0-102">ICLRStrongName::StrongNameSignatureSize — Metoda</span><span class="sxs-lookup"><span data-stu-id="406b0-102">ICLRStrongName::StrongNameSignatureSize Method</span></span>
<span data-ttu-id="406b0-103">Zwraca rozmiar podpisu silnej nazwy.</span><span class="sxs-lookup"><span data-stu-id="406b0-103">Returns the size of the strong name signature.</span></span> <span data-ttu-id="406b0-104">Ta metoda jest zwykle używana przez kompilatory, aby określić, ile miejsca do zarezerwowania w pliku, podczas tworzenia zestawu podpisanego z opóźnieniem.</span><span class="sxs-lookup"><span data-stu-id="406b0-104">This method is typically used by compilers to determine how much space to reserve in the file when creating a delay-signed assembly.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="406b0-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="406b0-105">Syntax</span></span>  
  
```  
HRESULT StrongNameSignatureSize (   
    [in]  BYTE   *pbPublicKeyBlob,  
    [in]  ULONG  cbPublicKeyBlob,   
    [in]  DWORD  *pcbSize  
);   
```  
  
#### <a name="parameters"></a><span data-ttu-id="406b0-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="406b0-106">Parameters</span></span>  
 `pbPublicKeyBlob`  
 <span data-ttu-id="406b0-107">[in] Struktury typu [publickeyblob —](../../../../docs/framework/unmanaged-api/strong-naming/publickeyblob-structure.md) zawierający publiczną część pary kluczy używanego do generowania podpisu silnej nazwy.</span><span class="sxs-lookup"><span data-stu-id="406b0-107">[in] A structure of type [PublicKeyBlob](../../../../docs/framework/unmanaged-api/strong-naming/publickeyblob-structure.md) that contains the public portion of the key pair used to generate the strong name signature.</span></span>  
  
 `cbPublicKeyBlob`  
 <span data-ttu-id="406b0-108">[in] Rozmiar w bajtach z `pbPublicKeyBlob`.</span><span class="sxs-lookup"><span data-stu-id="406b0-108">[in] The size, in bytes, of `pbPublicKeyBlob`.</span></span>  
  
 `pcbSize`  
 <span data-ttu-id="406b0-109">[in] Liczba bajtów potrzebnych do przechowania podpisu silnej nazwy.</span><span class="sxs-lookup"><span data-stu-id="406b0-109">[in] The number of bytes required to store the strong name signature.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="406b0-110">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="406b0-110">Return Value</span></span>  
 <span data-ttu-id="406b0-111">`S_OK` Jeśli metoda została ukończona pomyślnie; w przeciwnym razie wartość HRESULT, która wskazuje błąd (zobacz [typowe wartości HRESULT](https://go.microsoft.com/fwlink/?LinkId=213878) dla listy).</span><span class="sxs-lookup"><span data-stu-id="406b0-111">`S_OK` if the method completed successfully; otherwise, an HRESULT value that indicates failure (see [Common HRESULT Values](https://go.microsoft.com/fwlink/?LinkId=213878) for a list).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="406b0-112">Wymagania</span><span class="sxs-lookup"><span data-stu-id="406b0-112">Requirements</span></span>  
 <span data-ttu-id="406b0-113">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="406b0-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="406b0-114">**Nagłówek:** MetaHost.h</span><span class="sxs-lookup"><span data-stu-id="406b0-114">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="406b0-115">**Biblioteka:** dołączony jako zasób w MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="406b0-115">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="406b0-116">**Wersje programu .NET framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="406b0-116">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="406b0-117">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="406b0-117">See Also</span></span>  
 [<span data-ttu-id="406b0-118">ICLRStrongName, interfejs</span><span class="sxs-lookup"><span data-stu-id="406b0-118">ICLRStrongName Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
