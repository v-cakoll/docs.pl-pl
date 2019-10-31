---
title: CreateAssemblyNameObject — Funkcja
ms.date: 03/30/2017
api_name:
- CreateAssemblyNameObject
api_location:
- fusion.dll
- clr.dll
- mscorwks.dll
api_type:
- DLLExport
f1_keywords:
- CreateAssemblyNameObject
helpviewer_keywords:
- CreateAssemblyNameObject function [.NET Framework fusion]
ms.assetid: 55c8b41e-fbe4-4ae0-aa29-68fbb2311691
topic_type:
- apiref
ms.openlocfilehash: 00345f6c95c67f0494aa721c662f56a9e98cdd7f
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73108715"
---
# <a name="createassemblynameobject-function"></a><span data-ttu-id="f2966-102">CreateAssemblyNameObject — Funkcja</span><span class="sxs-lookup"><span data-stu-id="f2966-102">CreateAssemblyNameObject Function</span></span>
<span data-ttu-id="f2966-103">Pobiera wskaźnik interfejsu do wystąpienia [IAssemblyName](iassemblyname-interface.md) , które reprezentuje unikatową tożsamość zestawu o określonej nazwie.</span><span class="sxs-lookup"><span data-stu-id="f2966-103">Gets an interface pointer to an [IAssemblyName](iassemblyname-interface.md) instance that represents the unique identity of the assembly with the specified name.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f2966-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="f2966-104">Syntax</span></span>  
  
```cpp  
HRESULT CreateAssemblyNameObject (  
    [out] LPASSEMBLYNAME  *ppAssemblyNameObj,  
    [in]  LPCWSTR         szAssemblyName,  
    [in]  DWORD           dwFlags,  
    [in]  LPVOID          pvReserved  
 );  
```  
  
## <a name="parameters"></a><span data-ttu-id="f2966-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="f2966-105">Parameters</span></span>  
 `ppAssemblyNameObj`  
 <span data-ttu-id="f2966-106">określoną Zwrócony `IAssemblyName`.</span><span class="sxs-lookup"><span data-stu-id="f2966-106">[out] The returned `IAssemblyName`.</span></span>  
  
 `szAssemblyName`  
 <span data-ttu-id="f2966-107">podczas Nazwa zestawu, dla którego ma zostać utworzone nowe wystąpienie `IAssemblyName`.</span><span class="sxs-lookup"><span data-stu-id="f2966-107">[in] The name of the assembly for which to create the new `IAssemblyName` instance.</span></span>  
  
 `dwFlags`  
 <span data-ttu-id="f2966-108">podczas Flagi do przekazania do konstruktora obiektów.</span><span class="sxs-lookup"><span data-stu-id="f2966-108">[in] Flags to pass to the object constructor.</span></span>  
  
 `pvReserved`  
 <span data-ttu-id="f2966-109">podczas Zarezerwowane do użytku w przyszłości.</span><span class="sxs-lookup"><span data-stu-id="f2966-109">[in] Reserved for future extensibility.</span></span> <span data-ttu-id="f2966-110">`pvReserved` musi być odwołaniem o wartości null.</span><span class="sxs-lookup"><span data-stu-id="f2966-110">`pvReserved` must be a null reference.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f2966-111">Wymagania</span><span class="sxs-lookup"><span data-stu-id="f2966-111">Requirements</span></span>  
 <span data-ttu-id="f2966-112">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f2966-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f2966-113">**Nagłówek:** Fusion. h</span><span class="sxs-lookup"><span data-stu-id="f2966-113">**Header:** Fusion.h</span></span>  
  
 <span data-ttu-id="f2966-114">**Biblioteka:** Uwzględnione jako zasób w bibliotece MsCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="f2966-114">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="f2966-115">**Wersje .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f2966-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f2966-116">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="f2966-116">See also</span></span>

- [<span data-ttu-id="f2966-117">IAssemblyName, interfejs</span><span class="sxs-lookup"><span data-stu-id="f2966-117">IAssemblyName Interface</span></span>](iassemblyname-interface.md)
- [<span data-ttu-id="f2966-118">Łączenie statycznych funkcji globalnych</span><span class="sxs-lookup"><span data-stu-id="f2966-118">Fusion Global Static Functions</span></span>](fusion-global-static-functions.md)
