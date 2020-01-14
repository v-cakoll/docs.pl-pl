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
ms.openlocfilehash: 4f05eb2e6ef31cf1993a623c38bb177f7e3c297e
ms.sourcegitcommit: 7e2128d4a4c45b4274bea3b8e5760d4694569ca1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/14/2020
ms.locfileid: "75935648"
---
# <a name="gettypelibinfo-function"></a><span data-ttu-id="2f5d2-102">GetTypeLibInfo — Funkcja</span><span class="sxs-lookup"><span data-stu-id="2f5d2-102">GetTypeLibInfo Function</span></span>
<span data-ttu-id="2f5d2-103">Zwraca informacje o określonej bibliotece typów, badając jej strukturę [TLIBATTR](/windows/win32/api/oaidl/ns-oaidl-tlibattr) .</span><span class="sxs-lookup"><span data-stu-id="2f5d2-103">Returns information about the specified type library by examining its [TLIBATTR](/windows/win32/api/oaidl/ns-oaidl-tlibattr) structure.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2f5d2-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="2f5d2-104">Syntax</span></span>  
  
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
  
## <a name="parameters"></a><span data-ttu-id="2f5d2-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="2f5d2-105">Parameters</span></span>  
 `szFile`  
 <span data-ttu-id="2f5d2-106">podczas Nazwa pliku biblioteki typów.</span><span class="sxs-lookup"><span data-stu-id="2f5d2-106">[in] The file name of the type library.</span></span>  
  
 `pTypeLibID`  
 <span data-ttu-id="2f5d2-107">określoną Identyfikator GUID biblioteki typów.</span><span class="sxs-lookup"><span data-stu-id="2f5d2-107">[out] The GUID of the type library.</span></span>  
  
 `pTypeLibLCID`  
 <span data-ttu-id="2f5d2-108">określoną Identyfikator lokalizacji biblioteki typów.</span><span class="sxs-lookup"><span data-stu-id="2f5d2-108">[out] The localization ID of the type library.</span></span>  
  
 `pTypeLibPlatform`  
 <span data-ttu-id="2f5d2-109">określoną Flaga [SYSKIND](/windows/win32/api/oaidl/ne-oaidl-syskind) , która identyfikuje docelowy system operacyjny dla biblioteki typów.</span><span class="sxs-lookup"><span data-stu-id="2f5d2-109">[out] A [SYSKIND](/windows/win32/api/oaidl/ne-oaidl-syskind) flag that identifies the target operating system for the type library.</span></span> <span data-ttu-id="2f5d2-110">Typowe wartości to SYS_WIN32 i SYS_WIN64.</span><span class="sxs-lookup"><span data-stu-id="2f5d2-110">Common values are SYS_WIN32 and SYS_WIN64.</span></span>  
  
 `pTypeLibMajorVer`  
 <span data-ttu-id="2f5d2-111">określoną Numer wersji głównej biblioteki typów.</span><span class="sxs-lookup"><span data-stu-id="2f5d2-111">[out] The major version number of the type library.</span></span> <span data-ttu-id="2f5d2-112">Na przykład w przypadku wersji *x. y*główny numer wersji to *x*.</span><span class="sxs-lookup"><span data-stu-id="2f5d2-112">For example, for version *x.y*, the major version number is *x*.</span></span>  
  
 `pTypeLibMinorVer`  
 <span data-ttu-id="2f5d2-113">określoną Numer wersji pomocniczej biblioteki typów.</span><span class="sxs-lookup"><span data-stu-id="2f5d2-113">[out] The minor version number of the type library.</span></span> <span data-ttu-id="2f5d2-114">Na przykład w przypadku wersji *x. y*pomocniczy numer wersji to *y*.</span><span class="sxs-lookup"><span data-stu-id="2f5d2-114">For example, for version *x.y*, the minor version number is *y*.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="2f5d2-115">Uwagi</span><span class="sxs-lookup"><span data-stu-id="2f5d2-115">Remarks</span></span>  
 <span data-ttu-id="2f5d2-116">Funkcja `GetTypeLibInfo` jest wywoływana przez [Tlbexp. exe (Eksporter biblioteki typów)](../../tools/tlbexp-exe-type-library-exporter.md).</span><span class="sxs-lookup"><span data-stu-id="2f5d2-116">The `GetTypeLibInfo` function is called by the [Tlbexp.exe (Type Library Exporter)](../../tools/tlbexp-exe-type-library-exporter.md).</span></span> <span data-ttu-id="2f5d2-117">To narzędzie generuje bibliotekę typów, która opisuje typy w zestawie środowiska uruchomieniowego języka wspólnego (CLR).</span><span class="sxs-lookup"><span data-stu-id="2f5d2-117">This tool generates a type library that describes the types in a common language runtime (CLR) assembly.</span></span>  
  
 <span data-ttu-id="2f5d2-118">Jeśli dowolny parametr ma wartość null, funkcja zwraca `HRESULT` `E_POINTER`.</span><span class="sxs-lookup"><span data-stu-id="2f5d2-118">If any parameter is null, the function returns an `HRESULT` of `E_POINTER`.</span></span> <span data-ttu-id="2f5d2-119">W przeciwnym razie zwraca `S_OK`.</span><span class="sxs-lookup"><span data-stu-id="2f5d2-119">Otherwise, it returns `S_OK`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2f5d2-120">Wymagania</span><span class="sxs-lookup"><span data-stu-id="2f5d2-120">Requirements</span></span>  
 <span data-ttu-id="2f5d2-121">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2f5d2-121">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2f5d2-122">**Nagłówek:** TlbRef. h</span><span class="sxs-lookup"><span data-stu-id="2f5d2-122">**Header:** TlbRef.h</span></span>  
  
 <span data-ttu-id="2f5d2-123">**Biblioteka:** TlbRef. lib</span><span class="sxs-lookup"><span data-stu-id="2f5d2-123">**Library:** TlbRef.lib</span></span>  
  
 <span data-ttu-id="2f5d2-124">**Wersje .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2f5d2-124">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2f5d2-125">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="2f5d2-125">See also</span></span>

- [<span data-ttu-id="2f5d2-126">Tlbexp, funkcje pomocy</span><span class="sxs-lookup"><span data-stu-id="2f5d2-126">Tlbexp Helper Functions</span></span>](index.md)
- [<span data-ttu-id="2f5d2-127">LoadTypeLibEx, funkcja</span><span class="sxs-lookup"><span data-stu-id="2f5d2-127">LoadTypeLibEx Function</span></span>](https://docs.microsoft.com/previous-versions/windows/desktop/api/oleauto/nf-oleauto-loadtypelibex)
