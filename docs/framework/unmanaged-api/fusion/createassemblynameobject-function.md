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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: fb53014a28fb291b8463535addfb61e62d32d7d6
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/07/2019
ms.locfileid: "70795356"
---
# <a name="createassemblynameobject-function"></a><span data-ttu-id="238e6-102">CreateAssemblyNameObject — Funkcja</span><span class="sxs-lookup"><span data-stu-id="238e6-102">CreateAssemblyNameObject Function</span></span>
<span data-ttu-id="238e6-103">Pobiera wskaźnik interfejsu do wystąpienia [IAssemblyName](iassemblyname-interface.md) , które reprezentuje unikatową tożsamość zestawu o określonej nazwie.</span><span class="sxs-lookup"><span data-stu-id="238e6-103">Gets an interface pointer to an [IAssemblyName](iassemblyname-interface.md) instance that represents the unique identity of the assembly with the specified name.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="238e6-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="238e6-104">Syntax</span></span>  
  
```cpp  
HRESULT CreateAssemblyNameObject (  
    [out] LPASSEMBLYNAME  *ppAssemblyNameObj,  
    [in]  LPCWSTR         szAssemblyName,  
    [in]  DWORD           dwFlags,  
    [in]  LPVOID          pvReserved  
 );  
```  
  
## <a name="parameters"></a><span data-ttu-id="238e6-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="238e6-105">Parameters</span></span>  
 `ppAssemblyNameObj`  
 <span data-ttu-id="238e6-106">określoną Zwracana `IAssemblyName`wartość.</span><span class="sxs-lookup"><span data-stu-id="238e6-106">[out] The returned `IAssemblyName`.</span></span>  
  
 `szAssemblyName`  
 <span data-ttu-id="238e6-107">podczas Nazwa zestawu, dla którego ma zostać utworzone nowe `IAssemblyName` wystąpienie.</span><span class="sxs-lookup"><span data-stu-id="238e6-107">[in] The name of the assembly for which to create the new `IAssemblyName` instance.</span></span>  
  
 `dwFlags`  
 <span data-ttu-id="238e6-108">podczas Flagi do przekazania do konstruktora obiektów.</span><span class="sxs-lookup"><span data-stu-id="238e6-108">[in] Flags to pass to the object constructor.</span></span>  
  
 `pvReserved`  
 <span data-ttu-id="238e6-109">podczas Zarezerwowane do użytku w przyszłości.</span><span class="sxs-lookup"><span data-stu-id="238e6-109">[in] Reserved for future extensibility.</span></span> <span data-ttu-id="238e6-110">`pvReserved`musi być odwołaniem o wartości null.</span><span class="sxs-lookup"><span data-stu-id="238e6-110">`pvReserved` must be a null reference.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="238e6-111">Wymagania</span><span class="sxs-lookup"><span data-stu-id="238e6-111">Requirements</span></span>  
 <span data-ttu-id="238e6-112">**Poszczególnych** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="238e6-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="238e6-113">**Nagłówki** Fusion. h</span><span class="sxs-lookup"><span data-stu-id="238e6-113">**Header:** Fusion.h</span></span>  
  
 <span data-ttu-id="238e6-114">**Biblioteki** Uwzględnione jako zasób w bibliotece MsCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="238e6-114">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="238e6-115">**.NET Framework wersje:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="238e6-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="238e6-116">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="238e6-116">See also</span></span>

- [<span data-ttu-id="238e6-117">IAssemblyName, interfejs</span><span class="sxs-lookup"><span data-stu-id="238e6-117">IAssemblyName Interface</span></span>](iassemblyname-interface.md)
- [<span data-ttu-id="238e6-118">Łączenie statycznych funkcji globalnych</span><span class="sxs-lookup"><span data-stu-id="238e6-118">Fusion Global Static Functions</span></span>](fusion-global-static-functions.md)
