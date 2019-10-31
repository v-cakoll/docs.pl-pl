---
title: GetCORRequiredVersion — Funkcja
ms.date: 03/30/2017
api_name:
- GetCORRequiredVersion
api_location:
- mscoree.dll
api_type:
- DLLExport
f1_keywords:
- GetCORRequiredVersion
helpviewer_keywords:
- GetCORRequiredVersion function [.NET Framework hosting]
ms.assetid: 1588fe7b-c378-4f4b-9c4b-48647f1119cc
topic_type:
- apiref
ms.openlocfilehash: 661eb758e1651901bb56810640a68f0de0b4e851
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73136475"
---
# <a name="getcorrequiredversion-function"></a><span data-ttu-id="463f9-102">GetCORRequiredVersion — Funkcja</span><span class="sxs-lookup"><span data-stu-id="463f9-102">GetCORRequiredVersion Function</span></span>
<span data-ttu-id="463f9-103">Pobiera wymagany numer wersji środowiska uruchomieniowego języka wspólnego (CLR).</span><span class="sxs-lookup"><span data-stu-id="463f9-103">Gets the required common language runtime (CLR) version number.</span></span>  
  
 <span data-ttu-id="463f9-104">Ta funkcja jest przestarzała w .NET Framework 4.</span><span class="sxs-lookup"><span data-stu-id="463f9-104">This function has been deprecated in the .NET Framework 4.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="463f9-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="463f9-105">Syntax</span></span>  
  
```cpp  
HRESULT GetCORRequiredVersion (  
    [out] LPWSTR   pbuffer,  
    [in]  DWORD    cchBuffer,  
    [out] DWORD   *dwLength  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="463f9-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="463f9-106">Parameters</span></span>  
 `pbuffer`  
 <span data-ttu-id="463f9-107">określoną Bufor zawierający ciąg, który określa numer wersji.</span><span class="sxs-lookup"><span data-stu-id="463f9-107">[out] A buffer containing a string that specifies the version number.</span></span>  
  
 `cchBuffer`  
 <span data-ttu-id="463f9-108">podczas Rozmiar bufora (w bajtach).</span><span class="sxs-lookup"><span data-stu-id="463f9-108">[in] The size, in bytes, of the buffer.</span></span>  
  
 `dwLength`  
 <span data-ttu-id="463f9-109">określoną Liczba bajtów zwróconych w buforze.</span><span class="sxs-lookup"><span data-stu-id="463f9-109">[out] The number of bytes returned in the buffer.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="463f9-110">Wymagania</span><span class="sxs-lookup"><span data-stu-id="463f9-110">Requirements</span></span>  
 <span data-ttu-id="463f9-111">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="463f9-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="463f9-112">**Nagłówek:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="463f9-112">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="463f9-113">**Biblioteka:** MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="463f9-113">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="463f9-114">**Wersje .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="463f9-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="463f9-115">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="463f9-115">See also</span></span>

- [<span data-ttu-id="463f9-116">Przestarzałe funkcje hostingu środowiska CLR</span><span class="sxs-lookup"><span data-stu-id="463f9-116">Deprecated CLR Hosting Functions</span></span>](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
