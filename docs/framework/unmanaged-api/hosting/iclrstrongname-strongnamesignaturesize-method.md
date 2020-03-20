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
ms.openlocfilehash: e789996af3aedd17251fc52cde52a336f65053ec
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79176347"
---
# <a name="iclrstrongnamestrongnamesignaturesize-method"></a><span data-ttu-id="9ffca-102">ICLRStrongName::StrongNameSignatureSize — Metoda</span><span class="sxs-lookup"><span data-stu-id="9ffca-102">ICLRStrongName::StrongNameSignatureSize Method</span></span>
<span data-ttu-id="9ffca-103">Zwraca rozmiar podpisu silnej nazwy.</span><span class="sxs-lookup"><span data-stu-id="9ffca-103">Returns the size of the strong name signature.</span></span> <span data-ttu-id="9ffca-104">Ta metoda jest zwykle używana przez kompilatory, aby określić, ile miejsca do zarezerwowania w pliku podczas tworzenia zestawu podpisane z opóźnieniem.</span><span class="sxs-lookup"><span data-stu-id="9ffca-104">This method is typically used by compilers to determine how much space to reserve in the file when creating a delay-signed assembly.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9ffca-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="9ffca-105">Syntax</span></span>  
  
```cpp  
HRESULT StrongNameSignatureSize (
    [in]  BYTE   *pbPublicKeyBlob,  
    [in]  ULONG  cbPublicKeyBlob,
    [in]  DWORD  *pcbSize  
);
```  
  
## <a name="parameters"></a><span data-ttu-id="9ffca-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="9ffca-106">Parameters</span></span>  
 `pbPublicKeyBlob`  
 <span data-ttu-id="9ffca-107">[w] Struktura typu [PublicKeyBlob,](../../../../docs/framework/unmanaged-api/strong-naming/publickeyblob-structure.md) który zawiera część publiczną pary kluczy używane do generowania podpisu silnej nazwy.</span><span class="sxs-lookup"><span data-stu-id="9ffca-107">[in] A structure of type [PublicKeyBlob](../../../../docs/framework/unmanaged-api/strong-naming/publickeyblob-structure.md) that contains the public portion of the key pair used to generate the strong name signature.</span></span>  
  
 `cbPublicKeyBlob`  
 <span data-ttu-id="9ffca-108">[w] Rozmiar w bajtach `pbPublicKeyBlob`.</span><span class="sxs-lookup"><span data-stu-id="9ffca-108">[in] The size, in bytes, of `pbPublicKeyBlob`.</span></span>  
  
 `pcbSize`  
 <span data-ttu-id="9ffca-109">[w] Liczba bajtów wymaganych do przechowywania podpisu silnej nazwy.</span><span class="sxs-lookup"><span data-stu-id="9ffca-109">[in] The number of bytes required to store the strong name signature.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="9ffca-110">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="9ffca-110">Return Value</span></span>  
 <span data-ttu-id="9ffca-111">`S_OK`jeśli metoda została pomyślnie ukończona; w przeciwnym razie wartość HRESULT wskazująca błąd (zobacz [typowe wartości HRESULT](/windows/win32/seccrypto/common-hresult-values) dla listy).</span><span class="sxs-lookup"><span data-stu-id="9ffca-111">`S_OK` if the method completed successfully; otherwise, an HRESULT value that indicates failure (see [Common HRESULT Values](/windows/win32/seccrypto/common-hresult-values) for a list).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9ffca-112">Wymagania</span><span class="sxs-lookup"><span data-stu-id="9ffca-112">Requirements</span></span>  
 <span data-ttu-id="9ffca-113">**Platformy:** Zobacz [Wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9ffca-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9ffca-114">**Nagłówek:** MetaHost.h</span><span class="sxs-lookup"><span data-stu-id="9ffca-114">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="9ffca-115">**Biblioteka:** Uwzględnione jako zasób w pliku MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="9ffca-115">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="9ffca-116">**Wersje programu .NET Framework:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9ffca-116">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9ffca-117">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="9ffca-117">See also</span></span>

- [<span data-ttu-id="9ffca-118">ICLRStrongName, interfejs</span><span class="sxs-lookup"><span data-stu-id="9ffca-118">ICLRStrongName Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
