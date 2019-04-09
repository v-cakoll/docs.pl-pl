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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: f84d50579feade09df1b42a8e2f0c6b3e6a94fac
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59157766"
---
# <a name="iclrstrongnamegethashfromblob-method"></a><span data-ttu-id="6506f-102">ICLRStrongName::GetHashFromBlob — Metoda</span><span class="sxs-lookup"><span data-stu-id="6506f-102">ICLRStrongName::GetHashFromBlob Method</span></span>
<span data-ttu-id="6506f-103">Pobiera skrót zestawu pod adresem określonym pamięci, przy użyciu określonego algorytmu skrótu.</span><span class="sxs-lookup"><span data-stu-id="6506f-103">Gets a hash of the assembly at the specified memory address, using the specified hash algorithm.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6506f-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="6506f-104">Syntax</span></span>  
  
```  
HRESULT GetHashFromBlob (  
    [in]  BYTE    *pbBlob,  
    [in]  DWORD   cchBlob,  
    [in, out] unsigned int   *piHashAlg,  
    [out] BYTE    *pbHash,  
    [in]  DWORD   cchHash,  
    [out] DWORD   *pchHash  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="6506f-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="6506f-105">Parameters</span></span>  
 `pbBlob`  
 <span data-ttu-id="6506f-106">[in] Wskaźnik na adres bloku pamięci, aby zostać obliczona wartość skrótu.</span><span class="sxs-lookup"><span data-stu-id="6506f-106">[in] A pointer to the address of the memory block to be hashed.</span></span>  
  
 `cchBlob`  
 <span data-ttu-id="6506f-107">[in] Długość w bajtach, bloku pamięci.</span><span class="sxs-lookup"><span data-stu-id="6506f-107">[in] The length, in bytes, of the memory block.</span></span>  
  
 `piHashAlg`  
 <span data-ttu-id="6506f-108">[out w] Stała, który określa algorytm wyznaczania wartości skrótu.</span><span class="sxs-lookup"><span data-stu-id="6506f-108">[in, out] A constant that specifies the hash algorithm.</span></span> <span data-ttu-id="6506f-109">Użyj wartości zero dla domyślny algorytm.</span><span class="sxs-lookup"><span data-stu-id="6506f-109">Use zero for the default algorithm.</span></span>  
  
 `pbHash`  
 <span data-ttu-id="6506f-110">[out] Bufor zwrócone wyznaczania wartości skrótu.</span><span class="sxs-lookup"><span data-stu-id="6506f-110">[out] The returned hash buffer.</span></span>  
  
 `cchHash`  
 <span data-ttu-id="6506f-111">[in] Żądany maksymalny rozmiar `pbHash`.</span><span class="sxs-lookup"><span data-stu-id="6506f-111">[in] The requested maximum size of `pbHash`.</span></span>  
  
 `pchHash`  
 <span data-ttu-id="6506f-112">[out] Rozmiar w bajtach zwracanego `pbHash`.</span><span class="sxs-lookup"><span data-stu-id="6506f-112">[out] The size, in bytes, of the returned `pbHash`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="6506f-113">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="6506f-113">Return Value</span></span>  
 `S_OK` <span data-ttu-id="6506f-114">Jeśli metoda została ukończona pomyślnie; w przeciwnym razie wartość HRESULT, która wskazuje błąd (zobacz [typowe wartości HRESULT](https://go.microsoft.com/fwlink/?LinkId=213878) dla listy).</span><span class="sxs-lookup"><span data-stu-id="6506f-114">if the method completed successfully; otherwise, an HRESULT value that indicates failure (see [Common HRESULT Values](https://go.microsoft.com/fwlink/?LinkId=213878) for a list).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6506f-115">Wymagania</span><span class="sxs-lookup"><span data-stu-id="6506f-115">Requirements</span></span>  
 <span data-ttu-id="6506f-116">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6506f-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6506f-117">**Nagłówek:** MetaHost.h</span><span class="sxs-lookup"><span data-stu-id="6506f-117">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="6506f-118">**Biblioteka:** Dołączony jako zasób w MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="6506f-118">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 **<span data-ttu-id="6506f-119">Wersje programu .NET framework:</span><span class="sxs-lookup"><span data-stu-id="6506f-119">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="6506f-120">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="6506f-120">See also</span></span>

- [<span data-ttu-id="6506f-121">ICLRStrongName — Interfejs</span><span class="sxs-lookup"><span data-stu-id="6506f-121">ICLRStrongName Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
