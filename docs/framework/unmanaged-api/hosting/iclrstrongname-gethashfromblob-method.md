---
title: ICLRStrongName::GetHashFromBlob — Metoda
ms.date: 03/30/2017
api_name:
- ICLRStrongName.GetHashFromBlob
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRStrongName::GetHashFromBlob
helpviewer_keywords:
- ICLRStrongName::GetHashFromBlob method [.NET Framework hosting]
- GetHashFromBlob method, ICLRStrongName interface [.NET Framework hosting]
ms.assetid: f91d0f89-f356-49ac-aafb-50fad963c13d
topic_type:
- apiref
ms.openlocfilehash: 0c9adcc252fe16c95da8b2afca45bb2ee5dc545a
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73135203"
---
# <a name="iclrstrongnamegethashfromblob-method"></a><span data-ttu-id="1fcaf-102">ICLRStrongName::GetHashFromBlob — Metoda</span><span class="sxs-lookup"><span data-stu-id="1fcaf-102">ICLRStrongName::GetHashFromBlob Method</span></span>
<span data-ttu-id="1fcaf-103">Pobiera skrót zestawu pod określonym adresem pamięci przy użyciu określonego algorytmu wyznaczania wartości skrótu.</span><span class="sxs-lookup"><span data-stu-id="1fcaf-103">Gets a hash of the assembly at the specified memory address, using the specified hash algorithm.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1fcaf-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="1fcaf-104">Syntax</span></span>  
  
```cpp  
HRESULT GetHashFromBlob (  
    [in]  BYTE    *pbBlob,  
    [in]  DWORD   cchBlob,  
    [in, out] unsigned int   *piHashAlg,  
    [out] BYTE    *pbHash,  
    [in]  DWORD   cchHash,  
    [out] DWORD   *pchHash  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="1fcaf-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="1fcaf-105">Parameters</span></span>  
 `pbBlob`  
 <span data-ttu-id="1fcaf-106">podczas Wskaźnik do adresu bloku pamięci, który ma zostać zmieszany.</span><span class="sxs-lookup"><span data-stu-id="1fcaf-106">[in] A pointer to the address of the memory block to be hashed.</span></span>  
  
 `cchBlob`  
 <span data-ttu-id="1fcaf-107">podczas Długość (w bajtach) bloku pamięci.</span><span class="sxs-lookup"><span data-stu-id="1fcaf-107">[in] The length, in bytes, of the memory block.</span></span>  
  
 `piHashAlg`  
 <span data-ttu-id="1fcaf-108">[in. out] Stała, która określa algorytm wyznaczania wartości skrótu.</span><span class="sxs-lookup"><span data-stu-id="1fcaf-108">[in, out] A constant that specifies the hash algorithm.</span></span> <span data-ttu-id="1fcaf-109">Użyj wartości zero dla algorytmu domyślnego.</span><span class="sxs-lookup"><span data-stu-id="1fcaf-109">Use zero for the default algorithm.</span></span>  
  
 `pbHash`  
 <span data-ttu-id="1fcaf-110">określoną Zwrócony bufor wyznaczania wartości skrótu.</span><span class="sxs-lookup"><span data-stu-id="1fcaf-110">[out] The returned hash buffer.</span></span>  
  
 `cchHash`  
 <span data-ttu-id="1fcaf-111">podczas Żądany maksymalny rozmiar `pbHash`.</span><span class="sxs-lookup"><span data-stu-id="1fcaf-111">[in] The requested maximum size of `pbHash`.</span></span>  
  
 `pchHash`  
 <span data-ttu-id="1fcaf-112">określoną Rozmiar w bajtach zwracanej `pbHash`.</span><span class="sxs-lookup"><span data-stu-id="1fcaf-112">[out] The size, in bytes, of the returned `pbHash`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="1fcaf-113">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="1fcaf-113">Return Value</span></span>  
 <span data-ttu-id="1fcaf-114">`S_OK`, jeśli metoda została ukończona pomyślnie; w przeciwnym razie wartość HRESULT wskazująca niepowodzenie (zobacz [typowe wartości HRESULT](https://go.microsoft.com/fwlink/?LinkId=213878) dla listy).</span><span class="sxs-lookup"><span data-stu-id="1fcaf-114">`S_OK` if the method completed successfully; otherwise, an HRESULT value that indicates failure (see [Common HRESULT Values](https://go.microsoft.com/fwlink/?LinkId=213878) for a list).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1fcaf-115">Wymagania</span><span class="sxs-lookup"><span data-stu-id="1fcaf-115">Requirements</span></span>  
 <span data-ttu-id="1fcaf-116">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1fcaf-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1fcaf-117">**Nagłówek:** Obiekt ServiceHost. h</span><span class="sxs-lookup"><span data-stu-id="1fcaf-117">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="1fcaf-118">**Biblioteka:** Uwzględnione jako zasób w bibliotece MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="1fcaf-118">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="1fcaf-119">**Wersje .NET Framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1fcaf-119">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1fcaf-120">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="1fcaf-120">See also</span></span>

- [<span data-ttu-id="1fcaf-121">ICLRStrongName, interfejs</span><span class="sxs-lookup"><span data-stu-id="1fcaf-121">ICLRStrongName Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
