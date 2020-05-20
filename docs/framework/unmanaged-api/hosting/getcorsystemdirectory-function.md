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
ms.openlocfilehash: 137b2e30916cb1934d4389c5668bfb7eb5066064
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/19/2020
ms.locfileid: "83617233"
---
# <a name="getcorsystemdirectory-function"></a><span data-ttu-id="0425f-102">GetCORSystemDirectory — Funkcja</span><span class="sxs-lookup"><span data-stu-id="0425f-102">GetCORSystemDirectory Function</span></span>
<span data-ttu-id="0425f-103">Zwraca katalog instalacyjny środowiska uruchomieniowego języka wspólnego (CLR), który jest ładowany do procesu.</span><span class="sxs-lookup"><span data-stu-id="0425f-103">Returns the installation directory of the common language runtime (CLR) that is loaded into the process.</span></span> <span data-ttu-id="0425f-104">Katalog instalacyjny jest w pełni kwalifikowany, na przykład "c:\Windows\Microsoft.NET\Framework\v1.0.3705".</span><span class="sxs-lookup"><span data-stu-id="0425f-104">The installation directory is fully qualified, for example, "c:\windows\microsoft.net\framework\v1.0.3705".</span></span>  
  
 <span data-ttu-id="0425f-105">Ta funkcja jest przestarzała.</span><span class="sxs-lookup"><span data-stu-id="0425f-105">This function is deprecated.</span></span> <span data-ttu-id="0425f-106">Jest zastępowany przez metodę [ICLRRuntimeInfo:: GetRuntimeDirectory —](iclrruntimeinfo-getruntimedirectory-method.md) podaną w .NET Framework 4.</span><span class="sxs-lookup"><span data-stu-id="0425f-106">It is superseded by the [ICLRRuntimeInfo::GetRuntimeDirectory](iclrruntimeinfo-getruntimedirectory-method.md) method provided in the .NET Framework 4.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0425f-107">Składnia</span><span class="sxs-lookup"><span data-stu-id="0425f-107">Syntax</span></span>  
  
```cpp  
HRESULT GetCORSystemDirectory (
    [out] LPWSTR  pbuffer,
    [in]  DWORD   cchBuffer,
    [out] DWORD*  dwlength  
);
```  
  
## <a name="parameters"></a><span data-ttu-id="0425f-108">Parametry</span><span class="sxs-lookup"><span data-stu-id="0425f-108">Parameters</span></span>  
 `pbuffer`  
 <span data-ttu-id="0425f-109">określoną Bufor, w którym środowisko uruchomieniowe zwraca ciąg, który zawiera w pełni kwalifikowaną nazwę katalogu instalacyjnego dla środowiska uruchomieniowego, które jest ładowane do procesu.</span><span class="sxs-lookup"><span data-stu-id="0425f-109">[out] A buffer in which the runtime returns a string that contains the fully qualified name of the installation directory for the runtime that is loaded into the process.</span></span> <span data-ttu-id="0425f-110">Jeśli środowisko uruchomieniowe nie zostało jeszcze załadowane do procesu, funkcja zwróci odpowiednie informacje dotyczące katalogu dla najnowszej wersji środowiska uruchomieniowego zainstalowanej na komputerze.</span><span class="sxs-lookup"><span data-stu-id="0425f-110">If the runtime has not yet been loaded into the process, the function returns the appropriate directory information for the latest version of the runtime installed on the computer.</span></span>  
  
 `cchBuffer`  
 <span data-ttu-id="0425f-111">podczas Rozmiar, w bajtach, z `pbuffer` .</span><span class="sxs-lookup"><span data-stu-id="0425f-111">[in] The size, in bytes, of `pbuffer`.</span></span>  
  
 `dwLength`  
 <span data-ttu-id="0425f-112">określoną Liczba znaków zwrócona w `pbuffer` .</span><span class="sxs-lookup"><span data-stu-id="0425f-112">[out] The number of characters returned in `pbuffer`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="0425f-113">Uwagi</span><span class="sxs-lookup"><span data-stu-id="0425f-113">Remarks</span></span>  
  
> [!CAUTION]
> <span data-ttu-id="0425f-114">Nie należy używać tej funkcji w procesach, w których jest uruchomiona wersja 4 środowiska CLR.</span><span class="sxs-lookup"><span data-stu-id="0425f-114">Do not use this function in processes that are running version 4 of the CLR.</span></span> <span data-ttu-id="0425f-115">Jeśli na komputerze jest zainstalowana starsza wersja środowiska CLR, ta funkcja zwróci katalog instalacji dla tej wersji.</span><span class="sxs-lookup"><span data-stu-id="0425f-115">If an earlier version of the CLR is installed on the computer, this function returns the installation directory for that version.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0425f-116">Wymagania</span><span class="sxs-lookup"><span data-stu-id="0425f-116">Requirements</span></span>  
 <span data-ttu-id="0425f-117">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0425f-117">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0425f-118">**Nagłówek:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="0425f-118">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="0425f-119">**Biblioteka:** MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="0425f-119">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="0425f-120">**.NET Framework wersje:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0425f-120">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0425f-121">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="0425f-121">See also</span></span>

- [<span data-ttu-id="0425f-122">Przestarzałe funkcje hostingu środowiska CLR</span><span class="sxs-lookup"><span data-stu-id="0425f-122">Deprecated CLR Hosting Functions</span></span>](deprecated-clr-hosting-functions.md)
