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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: deec4d40270a11b9e48a0ab39504d774314c077c
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/10/2019
ms.locfileid: "67736189"
---
# <a name="getcorsystemdirectory-function"></a><span data-ttu-id="a7ebf-102">GetCORSystemDirectory — Funkcja</span><span class="sxs-lookup"><span data-stu-id="a7ebf-102">GetCORSystemDirectory Function</span></span>
<span data-ttu-id="a7ebf-103">Zwraca katalog instalacyjny środowisko uruchomieniowe języka wspólnego (CLR), który jest ładowany do procesu.</span><span class="sxs-lookup"><span data-stu-id="a7ebf-103">Returns the installation directory of the common language runtime (CLR) that is loaded into the process.</span></span> <span data-ttu-id="a7ebf-104">Katalog instalacyjny jest w pełni kwalifikowany, na przykład "c:\windows\microsoft.net\framework\v1.0.3705".</span><span class="sxs-lookup"><span data-stu-id="a7ebf-104">The installation directory is fully qualified, for example, "c:\windows\microsoft.net\framework\v1.0.3705".</span></span>  
  
 <span data-ttu-id="a7ebf-105">Ta funkcja jest przestarzała.</span><span class="sxs-lookup"><span data-stu-id="a7ebf-105">This function is deprecated.</span></span> <span data-ttu-id="a7ebf-106">Zostało zastąpione przez [iclrruntimeinfo::getruntimedirectory —](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-getruntimedirectory-method.md) metody dostarczone w programie .NET Framework 4.</span><span class="sxs-lookup"><span data-stu-id="a7ebf-106">It is superseded by the [ICLRRuntimeInfo::GetRuntimeDirectory](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-getruntimedirectory-method.md) method provided in the .NET Framework 4.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a7ebf-107">Składnia</span><span class="sxs-lookup"><span data-stu-id="a7ebf-107">Syntax</span></span>  
  
```cpp  
HRESULT GetCORSystemDirectory (   
    [out] LPWSTR  pbuffer,     
    [in]  DWORD   cchBuffer,   
    [out] DWORD*  dwlength  
);   
```  
  
## <a name="parameters"></a><span data-ttu-id="a7ebf-108">Parametry</span><span class="sxs-lookup"><span data-stu-id="a7ebf-108">Parameters</span></span>  
 `pbuffer`  
 <span data-ttu-id="a7ebf-109">[out] Bufor, w którym środowisko wykonawcze zwraca ciąg zawierający w pełni kwalifikowaną nazwę katalogu instalacyjnego dla środowiska uruchomieniowego, który jest ładowany do procesu.</span><span class="sxs-lookup"><span data-stu-id="a7ebf-109">[out] A buffer in which the runtime returns a string that contains the fully qualified name of the installation directory for the runtime that is loaded into the process.</span></span> <span data-ttu-id="a7ebf-110">Jeśli środowisko wykonawcze nie został jeszcze załadowany do procesu, funkcja zwraca informacje odpowiedniego katalogu dla najnowszej wersji środowiska uruchomieniowego zainstalowanego na komputerze.</span><span class="sxs-lookup"><span data-stu-id="a7ebf-110">If the runtime has not yet been loaded into the process, the function returns the appropriate directory information for the latest version of the runtime installed on the computer.</span></span>  
  
 `cchBuffer`  
 <span data-ttu-id="a7ebf-111">[in] Rozmiar w bajtach z `pbuffer`.</span><span class="sxs-lookup"><span data-stu-id="a7ebf-111">[in] The size, in bytes, of `pbuffer`.</span></span>  
  
 `dwLength`  
 <span data-ttu-id="a7ebf-112">[out] Liczba znaków zwracane w `pbuffer`.</span><span class="sxs-lookup"><span data-stu-id="a7ebf-112">[out] The number of characters returned in `pbuffer`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="a7ebf-113">Uwagi</span><span class="sxs-lookup"><span data-stu-id="a7ebf-113">Remarks</span></span>  
  
> [!CAUTION]
>  <span data-ttu-id="a7ebf-114">Nie należy używać tej funkcji w procesach, które działają w wersji 4 środowiska CLR.</span><span class="sxs-lookup"><span data-stu-id="a7ebf-114">Do not use this function in processes that are running version 4 of the CLR.</span></span> <span data-ttu-id="a7ebf-115">Jeśli starszą wersję środowiska CLR jest zainstalowany na komputerze, ta funkcja zwraca katalog instalacyjny dla danej wersji.</span><span class="sxs-lookup"><span data-stu-id="a7ebf-115">If an earlier version of the CLR is installed on the computer, this function returns the installation directory for that version.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a7ebf-116">Wymagania</span><span class="sxs-lookup"><span data-stu-id="a7ebf-116">Requirements</span></span>  
 <span data-ttu-id="a7ebf-117">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a7ebf-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a7ebf-118">**Nagłówek:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="a7ebf-118">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="a7ebf-119">**Biblioteka:** MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="a7ebf-119">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="a7ebf-120">**Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a7ebf-120">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a7ebf-121">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="a7ebf-121">See also</span></span>

- [<span data-ttu-id="a7ebf-122">Przestarzałe funkcje hostingu środowiska CLR</span><span class="sxs-lookup"><span data-stu-id="a7ebf-122">Deprecated CLR Hosting Functions</span></span>](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
