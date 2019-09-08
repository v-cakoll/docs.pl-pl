---
title: GetTypeLibInfo — Funkcja
ms.date: 03/30/2017
api_name:
- GetTypeLibInfo
api_location:
- TlbRef.dll
api_type:
- DLLExport
f1_keywords:
- GetTypeLibInfo
helpviewer_keywords:
- GetTypeLibInfo function [.NET Framework]
ms.assetid: a1c4d165-9bdc-4ca8-940e-292d4ffcc338
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: d8ea7df9396e9199d04ad5609daa9d2b01761f36
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/07/2019
ms.locfileid: "70798896"
---
# <a name="gettypelibinfo-function"></a><span data-ttu-id="5ba5e-102">GetTypeLibInfo — Funkcja</span><span class="sxs-lookup"><span data-stu-id="5ba5e-102">GetTypeLibInfo Function</span></span>
<span data-ttu-id="5ba5e-103">Zwraca informacje o określonej bibliotece typów, badając jej strukturę [TLIBATTR](https://docs.microsoft.com/windows/win32/api/oaidl/ns-oaidl-tlibattr) .</span><span class="sxs-lookup"><span data-stu-id="5ba5e-103">Returns information about the specified type library by examining its [TLIBATTR](https://docs.microsoft.com/windows/win32/api/oaidl/ns-oaidl-tlibattr) structure.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5ba5e-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="5ba5e-104">Syntax</span></span>  
  
```cpp  
HRESULT GetTypeLibInfo(  
    [in]   LPWSTR     szFile,  
    [out]  GUID      *pTypeLibID,  
    [out]  LCID      *pTypeLibLCID,  
    [out]  SYSKIND   *pTypeLibPlatform,  
    [out]  USHORT    *pTypeLibMajorVer,  
    [out]  USHORT    *pTypeLibMinorVer  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="5ba5e-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="5ba5e-105">Parameters</span></span>  
 `szFile`  
 <span data-ttu-id="5ba5e-106">podczas Nazwa pliku biblioteki typów.</span><span class="sxs-lookup"><span data-stu-id="5ba5e-106">[in] The file name of the type library.</span></span>  
  
 `pTypeLibID`  
 <span data-ttu-id="5ba5e-107">określoną Identyfikator GUID biblioteki typów.</span><span class="sxs-lookup"><span data-stu-id="5ba5e-107">[out] The GUID of the type library.</span></span>  
  
 `pTypeLibLCID`  
 <span data-ttu-id="5ba5e-108">określoną Identyfikator lokalizacji biblioteki typów.</span><span class="sxs-lookup"><span data-stu-id="5ba5e-108">[out] The localization ID of the type library.</span></span>  
  
 `pTypeLibPlatform`  
 <span data-ttu-id="5ba5e-109">określoną Flaga [SYSKIND](https://docs.microsoft.com/windows/win32/api/oaidl/ne-oaidl-syskind) , która identyfikuje docelowy system operacyjny dla biblioteki typów.</span><span class="sxs-lookup"><span data-stu-id="5ba5e-109">[out] A [SYSKIND](https://docs.microsoft.com/windows/win32/api/oaidl/ne-oaidl-syskind) flag that identifies the target operating system for the type library.</span></span> <span data-ttu-id="5ba5e-110">Wspólne wartości to SYS_WIN32 i SYS_WIN64.</span><span class="sxs-lookup"><span data-stu-id="5ba5e-110">Common values are SYS_WIN32 and SYS_WIN64.</span></span>  
  
 `pTypeLibMajorVer`  
 <span data-ttu-id="5ba5e-111">określoną Numer wersji głównej biblioteki typów.</span><span class="sxs-lookup"><span data-stu-id="5ba5e-111">[out] The major version number of the type library.</span></span> <span data-ttu-id="5ba5e-112">Na przykład w przypadku wersji *x. y*główny numer wersji to *x*.</span><span class="sxs-lookup"><span data-stu-id="5ba5e-112">For example, for version *x.y*, the major version number is *x*.</span></span>  
  
 `pTypeLibMinorVer`  
 <span data-ttu-id="5ba5e-113">określoną Numer wersji pomocniczej biblioteki typów.</span><span class="sxs-lookup"><span data-stu-id="5ba5e-113">[out] The minor version number of the type library.</span></span> <span data-ttu-id="5ba5e-114">Na przykład w przypadku wersji *x. y*pomocniczy numer wersji to *y*.</span><span class="sxs-lookup"><span data-stu-id="5ba5e-114">For example, for version *x.y*, the minor version number is *y*.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="5ba5e-115">Uwagi</span><span class="sxs-lookup"><span data-stu-id="5ba5e-115">Remarks</span></span>  
 <span data-ttu-id="5ba5e-116">Funkcja jest wywoływana przez [Tlbexp. exe (Eksporter biblioteki typów).](../../tools/tlbexp-exe-type-library-exporter.md) `GetTypeLibInfo`</span><span class="sxs-lookup"><span data-stu-id="5ba5e-116">The `GetTypeLibInfo` function is called by the [Tlbexp.exe (Type Library Exporter)](../../tools/tlbexp-exe-type-library-exporter.md).</span></span> <span data-ttu-id="5ba5e-117">To narzędzie generuje bibliotekę typów, która opisuje typy w zestawie środowiska uruchomieniowego języka wspólnego (CLR).</span><span class="sxs-lookup"><span data-stu-id="5ba5e-117">This tool generates a type library that describes the types in a common language runtime (CLR) assembly.</span></span>  
  
 <span data-ttu-id="5ba5e-118">Jeśli dowolny parametr ma wartość null, funkcja zwraca wartość `HRESULT`. `E_POINTER`</span><span class="sxs-lookup"><span data-stu-id="5ba5e-118">If any parameter is null, the function returns an `HRESULT` of `E_POINTER`.</span></span> <span data-ttu-id="5ba5e-119">W przeciwnym razie zwraca `S_OK`.</span><span class="sxs-lookup"><span data-stu-id="5ba5e-119">Otherwise, it returns `S_OK`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5ba5e-120">Wymagania</span><span class="sxs-lookup"><span data-stu-id="5ba5e-120">Requirements</span></span>  
 <span data-ttu-id="5ba5e-121">**Poszczególnych** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5ba5e-121">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5ba5e-122">**Nagłówki** TlbRef. h</span><span class="sxs-lookup"><span data-stu-id="5ba5e-122">**Header:** TlbRef.h</span></span>  
  
 <span data-ttu-id="5ba5e-123">**Biblioteki** TlbRef.lib</span><span class="sxs-lookup"><span data-stu-id="5ba5e-123">**Library:** TlbRef.lib</span></span>  
  
 <span data-ttu-id="5ba5e-124">**.NET Framework wersje:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5ba5e-124">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5ba5e-125">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="5ba5e-125">See also</span></span>

- [<span data-ttu-id="5ba5e-126">Tlbexp, funkcje pomocy</span><span class="sxs-lookup"><span data-stu-id="5ba5e-126">Tlbexp Helper Functions</span></span>](index.md)
- [<span data-ttu-id="5ba5e-127">LoadTypeLibEx, funkcja</span><span class="sxs-lookup"><span data-stu-id="5ba5e-127">LoadTypeLibEx Function</span></span>](https://docs.microsoft.com/previous-versions/windows/desktop/api/oleauto/nf-oleauto-loadtypelibex)
