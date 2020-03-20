---
title: GetCORSystemDirectory — Funkcja
ms.date: 03/30/2017
api_name:
- GetCORSystemDirectory
api_location:
- mscoree.dll
- mscoreei.dll
api_type:
- DLLExport
f1_keywords:
- GetCORSystemDirectory
helpviewer_keywords:
- GetCORSystemDirectory function [.NET Framework hosting]
ms.assetid: 3dcd16a7-dafc-4ca8-b5cd-20ffb37db91d
topic_type:
- apiref
ms.openlocfilehash: bdafacfe52d678aacfcd44de1e924bcb88547424
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79178205"
---
# <a name="getcorsystemdirectory-function"></a><span data-ttu-id="edfa3-102">GetCORSystemDirectory — Funkcja</span><span class="sxs-lookup"><span data-stu-id="edfa3-102">GetCORSystemDirectory Function</span></span>
<span data-ttu-id="edfa3-103">Zwraca katalog instalacyjny środowiska wykonawczego języka wspólnego (CLR), który jest ładowany do procesu.</span><span class="sxs-lookup"><span data-stu-id="edfa3-103">Returns the installation directory of the common language runtime (CLR) that is loaded into the process.</span></span> <span data-ttu-id="edfa3-104">Katalog instalacyjny jest w pełni kwalifikowany, na przykład "c:\windows\microsoft.net\framework\v1.0.3705".</span><span class="sxs-lookup"><span data-stu-id="edfa3-104">The installation directory is fully qualified, for example, "c:\windows\microsoft.net\framework\v1.0.3705".</span></span>  
  
 <span data-ttu-id="edfa3-105">Ta funkcja jest przestarzała.</span><span class="sxs-lookup"><span data-stu-id="edfa3-105">This function is deprecated.</span></span> <span data-ttu-id="edfa3-106">Zastępuje go metoda [ICLRRuntimeInfo::GetRuntimeDirectory](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-getruntimedirectory-method.md) dostępna w ramach .NET Framework 4.</span><span class="sxs-lookup"><span data-stu-id="edfa3-106">It is superseded by the [ICLRRuntimeInfo::GetRuntimeDirectory](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-getruntimedirectory-method.md) method provided in the .NET Framework 4.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="edfa3-107">Składnia</span><span class="sxs-lookup"><span data-stu-id="edfa3-107">Syntax</span></span>  
  
```cpp  
HRESULT GetCORSystemDirectory (
    [out] LPWSTR  pbuffer,
    [in]  DWORD   cchBuffer,
    [out] DWORD*  dwlength  
);
```  
  
## <a name="parameters"></a><span data-ttu-id="edfa3-108">Parametry</span><span class="sxs-lookup"><span data-stu-id="edfa3-108">Parameters</span></span>  
 `pbuffer`  
 <span data-ttu-id="edfa3-109">[na zewnątrz] Bufor, w którym środowisko wykonawcze zwraca ciąg zawierający w pełni kwalifikowaną nazwę katalogu instalacyjnego dla środowiska wykonawczego, który jest ładowany do procesu.</span><span class="sxs-lookup"><span data-stu-id="edfa3-109">[out] A buffer in which the runtime returns a string that contains the fully qualified name of the installation directory for the runtime that is loaded into the process.</span></span> <span data-ttu-id="edfa3-110">Jeśli środowisko wykonawcze nie zostało jeszcze załadowane do procesu, funkcja zwraca odpowiednie informacje o katalogu dla najnowszej wersji środowiska wykonawczego zainstalowanego na komputerze.</span><span class="sxs-lookup"><span data-stu-id="edfa3-110">If the runtime has not yet been loaded into the process, the function returns the appropriate directory information for the latest version of the runtime installed on the computer.</span></span>  
  
 `cchBuffer`  
 <span data-ttu-id="edfa3-111">[w] Rozmiar w bajtach `pbuffer`.</span><span class="sxs-lookup"><span data-stu-id="edfa3-111">[in] The size, in bytes, of `pbuffer`.</span></span>  
  
 `dwLength`  
 <span data-ttu-id="edfa3-112">[na zewnątrz] Liczba znaków zwróconych `pbuffer`w pliku .</span><span class="sxs-lookup"><span data-stu-id="edfa3-112">[out] The number of characters returned in `pbuffer`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="edfa3-113">Uwagi</span><span class="sxs-lookup"><span data-stu-id="edfa3-113">Remarks</span></span>  
  
> [!CAUTION]
> <span data-ttu-id="edfa3-114">Nie należy używać tej funkcji w procesach, które są uruchomione w wersji 4 CLR.</span><span class="sxs-lookup"><span data-stu-id="edfa3-114">Do not use this function in processes that are running version 4 of the CLR.</span></span> <span data-ttu-id="edfa3-115">Jeśli na komputerze jest zainstalowana wcześniejsza wersja programu CLR, ta funkcja zwraca katalog instalacyjny dla tej wersji.</span><span class="sxs-lookup"><span data-stu-id="edfa3-115">If an earlier version of the CLR is installed on the computer, this function returns the installation directory for that version.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="edfa3-116">Wymagania</span><span class="sxs-lookup"><span data-stu-id="edfa3-116">Requirements</span></span>  
 <span data-ttu-id="edfa3-117">**Platformy:** Zobacz [Wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="edfa3-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="edfa3-118">**Nagłówek:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="edfa3-118">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="edfa3-119">**Biblioteka:** Mscoree.dll</span><span class="sxs-lookup"><span data-stu-id="edfa3-119">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="edfa3-120">**Wersje programu .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="edfa3-120">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="edfa3-121">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="edfa3-121">See also</span></span>

- [<span data-ttu-id="edfa3-122">Przestarzałe funkcje hostingu środowiska CLR</span><span class="sxs-lookup"><span data-stu-id="edfa3-122">Deprecated CLR Hosting Functions</span></span>](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
