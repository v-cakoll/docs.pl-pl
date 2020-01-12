---
title: ICLRStrongName::GetHashFromHandle — Metoda
ms.date: 03/30/2017
api_name:
- ICLRStrongName.GetHashFromHandle
- ICLRStrongName.StrongNameCompareAssemblies
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRStrongName::GetHashFromHandle
helpviewer_keywords:
- GetHashFromHandle method, ICLRStrongName interface [.NET Framework hosting]
- ICLRStrongName::GetHashFromHandle method [.NET Framework hosting]
ms.assetid: 3bedbb7d-3cdd-4175-b370-10ae734062db
topic_type:
- apiref
ms.openlocfilehash: c095c99ee60d6b2ea0e5bce7010a66d40160443d
ms.sourcegitcommit: 7088f87e9a7da144266135f4b2397e611cf0a228
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/11/2020
ms.locfileid: "75899686"
---
# <a name="iclrstrongnamegethashfromhandle-method"></a><span data-ttu-id="88626-102">ICLRStrongName::GetHashFromHandle — Metoda</span><span class="sxs-lookup"><span data-stu-id="88626-102">ICLRStrongName::GetHashFromHandle Method</span></span>
<span data-ttu-id="88626-103">Generuje skrót do zawartości pliku, który ma określone dojście do pliku, przy użyciu określonego algorytmu wyznaczania wartości skrótu.</span><span class="sxs-lookup"><span data-stu-id="88626-103">Generates a hash over the contents of the file that has the specified file handle, using the specified hash algorithm.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="88626-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="88626-104">Syntax</span></span>  
  
```cpp  
HRESULT GetHashFromHandle (  
    [in]  HANDLE   hFile,  
    [in, out] unsigned int   *piHashAlg,  
    [out] BYTE     *pbHash,  
    [in]  DWORD    cchHash,  
    [out] DWORD    *pchHash  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="88626-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="88626-105">Parameters</span></span>  
 `hFile`  
 <span data-ttu-id="88626-106">podczas Dojście pliku do mieszania.</span><span class="sxs-lookup"><span data-stu-id="88626-106">[in] The handle of the file to be hashed.</span></span>  
  
 `piHashAlg`  
 <span data-ttu-id="88626-107">[in. out] Stała, która określa algorytm wyznaczania wartości skrótu.</span><span class="sxs-lookup"><span data-stu-id="88626-107">[in, out] A constant that specifies the hash algorithm.</span></span> <span data-ttu-id="88626-108">Użyj wartości zero dla algorytmu domyślnego.</span><span class="sxs-lookup"><span data-stu-id="88626-108">Use zero for the default algorithm.</span></span>  
  
 `pbHash`  
 <span data-ttu-id="88626-109">określoną Zwrócony bufor wyznaczania wartości skrótu.</span><span class="sxs-lookup"><span data-stu-id="88626-109">[out] The returned hash buffer.</span></span>  
  
 `cchHash`  
 <span data-ttu-id="88626-110">podczas Żądany maksymalny rozmiar `pbHash`.</span><span class="sxs-lookup"><span data-stu-id="88626-110">[in] The requested maximum size of `pbHash`.</span></span>  
  
 `pchHash`  
 <span data-ttu-id="88626-111">określoną Rozmiar w bajtach zwracanej `pbHash`.</span><span class="sxs-lookup"><span data-stu-id="88626-111">[out] The size, in bytes, of the returned `pbHash`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="88626-112">Wartość zwrócona</span><span class="sxs-lookup"><span data-stu-id="88626-112">Return Value</span></span>  
 <span data-ttu-id="88626-113">`S_OK`, jeśli metoda została ukończona pomyślnie; w przeciwnym razie wartość HRESULT wskazująca niepowodzenie (zobacz [typowe wartości HRESULT](/windows/win32/seccrypto/common-hresult-values) dla listy).</span><span class="sxs-lookup"><span data-stu-id="88626-113">`S_OK` if the method completed successfully; otherwise, an HRESULT value that indicates failure (see [Common HRESULT Values](/windows/win32/seccrypto/common-hresult-values) for a list).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="88626-114">Wymagania</span><span class="sxs-lookup"><span data-stu-id="88626-114">Requirements</span></span>  
 <span data-ttu-id="88626-115">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="88626-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="88626-116">**Nagłówek:** Obiekt ServiceHost. h</span><span class="sxs-lookup"><span data-stu-id="88626-116">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="88626-117">**Biblioteka:** Uwzględnione jako zasób w bibliotece MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="88626-117">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="88626-118">**Wersje .NET Framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="88626-118">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="88626-119">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="88626-119">See also</span></span>

- [<span data-ttu-id="88626-120">ICLRStrongName, interfejs</span><span class="sxs-lookup"><span data-stu-id="88626-120">ICLRStrongName Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
