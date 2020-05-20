---
title: GetFileVersion — Funkcja
ms.date: 03/30/2017
api_name:
- GetFileVersion
api_location:
- mscoree.dll
api_type:
- DLLExport
f1_keywords:
- GetFileVersion
helpviewer_keywords:
- GetFileVersion function [.NET Framework hosting]
ms.assetid: b3222c85-da88-4485-97d7-3a6ee3e8d358
topic_type:
- apiref
ms.openlocfilehash: 2dd004a44b20d48dafc72711ac23abcb55739224
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/19/2020
ms.locfileid: "83617203"
---
# <a name="getfileversion-function"></a><span data-ttu-id="9fea2-102">GetFileVersion — Funkcja</span><span class="sxs-lookup"><span data-stu-id="9fea2-102">GetFileVersion Function</span></span>
<span data-ttu-id="9fea2-103">Pobiera informacje o wersji środowiska uruchomieniowego języka wspólnego (CLR) określonego pliku przy użyciu określonego buforu.</span><span class="sxs-lookup"><span data-stu-id="9fea2-103">Gets the common language runtime (CLR) version information of the specified file, using the specified buffer.</span></span>  
  
 <span data-ttu-id="9fea2-104">Ta funkcja jest przestarzała w .NET Framework 4.</span><span class="sxs-lookup"><span data-stu-id="9fea2-104">This function has been deprecated in the .NET Framework 4.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9fea2-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="9fea2-105">Syntax</span></span>  
  
```cpp  
HRESULT GetFileVersion (  
    [in]  LPCWSTR      szFilename,
    [in, out] LPWSTR   szBuffer,
    [in]  DWORD        cchBuffer,
    [out] DWORD        *dwLength  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="9fea2-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="9fea2-106">Parameters</span></span>  
 `szFilename`  
 <span data-ttu-id="9fea2-107">podczas Ścieżka pliku, który ma zostać zbadany.</span><span class="sxs-lookup"><span data-stu-id="9fea2-107">[in] The path of the file to be examined.</span></span>  
  
 `szBuffer`  
 <span data-ttu-id="9fea2-108">[in. out] Bufor przydzielony dla zwracanych informacji o wersji.</span><span class="sxs-lookup"><span data-stu-id="9fea2-108">[in, out] The buffer allocated for the version information that is returned.</span></span>  
  
 `cchBuffer`  
 <span data-ttu-id="9fea2-109">podczas Rozmiar, w postaci znaków dwubajtowych, z `szBuffer` .</span><span class="sxs-lookup"><span data-stu-id="9fea2-109">[in] The size, in wide characters, of `szBuffer`.</span></span>  
  
 `dwLength`  
 <span data-ttu-id="9fea2-110">określoną Rozmiar zwracanych wartości (w bajtach) `szBuffer` .</span><span class="sxs-lookup"><span data-stu-id="9fea2-110">[out] The size, in bytes, of the returned `szBuffer`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9fea2-111">Wymagania</span><span class="sxs-lookup"><span data-stu-id="9fea2-111">Requirements</span></span>  
 <span data-ttu-id="9fea2-112">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9fea2-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9fea2-113">**Nagłówek:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="9fea2-113">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="9fea2-114">**.NET Framework wersje:**[!INCLUDE[net_current_v11plus](../../../../includes/net-current-v11plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9fea2-114">**.NET Framework Versions:** [!INCLUDE[net_current_v11plus](../../../../includes/net-current-v11plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9fea2-115">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="9fea2-115">See also</span></span>

- [<span data-ttu-id="9fea2-116">Przestarzałe funkcje hostingu środowiska CLR</span><span class="sxs-lookup"><span data-stu-id="9fea2-116">Deprecated CLR Hosting Functions</span></span>](deprecated-clr-hosting-functions.md)
