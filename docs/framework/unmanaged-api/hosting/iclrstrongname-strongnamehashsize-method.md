---
title: ICLRStrongName::StrongNameHashSize — Metoda
ms.date: 03/30/2017
api_name:
- ICLRStrongName.StrongNameHashSize
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRStrongName::StrongNameHashSize
helpviewer_keywords:
- ICLRStrongName::StrongNameHashSize method [.NET Framework hosting]
- StrongNameHashSize method, ICLRStrongName interface [.NET Framework hosting]
ms.assetid: 4a05ee56-08e4-4f3a-86a9-9b52083d5c0f
topic_type:
- apiref
ms.openlocfilehash: 0f4fdcbdfb9db7664920a42b9406a58f9c2de0b8
ms.sourcegitcommit: c76c8b2c39ed2f0eee422b61a2ab4c05ca7771fa
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/21/2020
ms.locfileid: "83763114"
---
# <a name="iclrstrongnamestrongnamehashsize-method"></a><span data-ttu-id="4d4ac-102">ICLRStrongName::StrongNameHashSize — Metoda</span><span class="sxs-lookup"><span data-stu-id="4d4ac-102">ICLRStrongName::StrongNameHashSize Method</span></span>
<span data-ttu-id="4d4ac-103">Pobiera rozmiar buforu wymagany dla skrótu przy użyciu określonego algorytmu wyznaczania wartości skrótu.</span><span class="sxs-lookup"><span data-stu-id="4d4ac-103">Gets the buffer size required for a hash, using the specified hash algorithm.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4d4ac-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="4d4ac-104">Syntax</span></span>  
  
```cpp  
HRESULT StrongNameHashSize (  
    [in]  ULONG   ulHashAlg,  
    [out] DWORD   *pcbSize  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="4d4ac-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="4d4ac-105">Parameters</span></span>  
 `ulHashAlg`  
 <span data-ttu-id="4d4ac-106">podczas Algorytm wyznaczania wartości skrótu używany do obliczania rozmiaru buforu.</span><span class="sxs-lookup"><span data-stu-id="4d4ac-106">[in] The hash algorithm used to compute the buffer size.</span></span>  
  
 `pcbSize`  
 <span data-ttu-id="4d4ac-107">określoną Zwrócony rozmiar buforu w bajtach.</span><span class="sxs-lookup"><span data-stu-id="4d4ac-107">[out] The returned buffer size, in bytes.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="4d4ac-108">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="4d4ac-108">Return Value</span></span>  
 <span data-ttu-id="4d4ac-109">`S_OK`Jeśli metoda została ukończona pomyślnie; w przeciwnym razie wartość HRESULT wskazująca niepowodzenie (zobacz [typowe wartości HRESULT](/windows/win32/seccrypto/common-hresult-values) dla listy).</span><span class="sxs-lookup"><span data-stu-id="4d4ac-109">`S_OK` if the method completed successfully; otherwise, an HRESULT value that indicates failure (see [Common HRESULT Values](/windows/win32/seccrypto/common-hresult-values) for a list).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4d4ac-110">Wymagania</span><span class="sxs-lookup"><span data-stu-id="4d4ac-110">Requirements</span></span>  
 <span data-ttu-id="4d4ac-111">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4d4ac-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4d4ac-112">**Nagłówek:** Obiekt ServiceHost. h</span><span class="sxs-lookup"><span data-stu-id="4d4ac-112">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="4d4ac-113">**Biblioteka:** Uwzględnione jako zasób w bibliotece MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="4d4ac-113">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="4d4ac-114">**.NET Framework wersje:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4d4ac-114">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4d4ac-115">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="4d4ac-115">See also</span></span>

- [<span data-ttu-id="4d4ac-116">ICLRStrongName, interfejs</span><span class="sxs-lookup"><span data-stu-id="4d4ac-116">ICLRStrongName Interface</span></span>](iclrstrongname-interface.md)
