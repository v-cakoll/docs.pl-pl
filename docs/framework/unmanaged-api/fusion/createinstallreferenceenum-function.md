---
title: CreateInstallReferenceEnum — Funkcja
ms.date: 03/30/2017
api_name:
- CreateInstallReferenceEnum
api_location:
- fusion.dll
- clr.dll
- mscorwks.dll
api_type:
- DLLExport
f1_keywords:
- CreateInstallReference
helpviewer_keywords:
- CreateInstallReference function [.NET Framework fusion]
ms.assetid: 80dbbbf8-54fc-4894-b74a-0179d3201083
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: da77d2eb848419c35e57ffacc8bf3d4580106fa5
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/10/2019
ms.locfileid: "67764325"
---
# <a name="createinstallreferenceenum-function"></a><span data-ttu-id="939d0-102">CreateInstallReferenceEnum — Funkcja</span><span class="sxs-lookup"><span data-stu-id="939d0-102">CreateInstallReferenceEnum Function</span></span>
<span data-ttu-id="939d0-103">Pobiera wskaźnik do [iinstallreferenceenum —](../../../../docs/framework/unmanaged-api/fusion/iinstallreferenceenum-interface.md) wystąpienia, która reprezentuje listę aplikacji odwołania do określonego zestawu.</span><span class="sxs-lookup"><span data-stu-id="939d0-103">Gets a pointer to an [IInstallReferenceEnum](../../../../docs/framework/unmanaged-api/fusion/iinstallreferenceenum-interface.md) instance that represents a list of an application's references to the specified assembly.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="939d0-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="939d0-104">Syntax</span></span>  
  
```cpp  
HRESULT CreateInstallReferenceEnum (  
    [out] IInstallReferenceEnum **ppRefEnum,  
    [in]  IAssemblyName         *pName,  
    [in]  DWORD                 dwFlags,  
    [in]  LPVOID                pvReserved  
 );  
```  
  
## <a name="parameters"></a><span data-ttu-id="939d0-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="939d0-105">Parameters</span></span>  
 `ppRefEnum`  
 <span data-ttu-id="939d0-106">[out] Zwrócony `IInstallReferenceEnum` wskaźnika.</span><span class="sxs-lookup"><span data-stu-id="939d0-106">[out] The returned `IInstallReferenceEnum` pointer.</span></span>  
  
 `pName`  
 <span data-ttu-id="939d0-107">[in] [Iassemblyname —](../../../../docs/framework/unmanaged-api/fusion/iassemblyname-interface.md) określający zestaw, dla którego wyliczania odwołań.</span><span class="sxs-lookup"><span data-stu-id="939d0-107">[in] The [IAssemblyName](../../../../docs/framework/unmanaged-api/fusion/iassemblyname-interface.md) that identifies the assembly for which to enumerate references.</span></span>  
  
 `dwFlags`  
 <span data-ttu-id="939d0-108">[in] Flagi, które wpływają na zachowanie modułu wyliczającego.</span><span class="sxs-lookup"><span data-stu-id="939d0-108">[in] Flags that influence the enumerator's behavior.</span></span>  
  
 `pvReserved`  
 <span data-ttu-id="939d0-109">[in] Zarezerwowane dla przyszłej rozszerzalności.</span><span class="sxs-lookup"><span data-stu-id="939d0-109">[in] Reserved for future extensibility.</span></span> <span data-ttu-id="939d0-110">`pvReserved` musi być odwołanie o wartości null.</span><span class="sxs-lookup"><span data-stu-id="939d0-110">`pvReserved` must be a null reference.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="939d0-111">Wymagania</span><span class="sxs-lookup"><span data-stu-id="939d0-111">Requirements</span></span>  
 <span data-ttu-id="939d0-112">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="939d0-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="939d0-113">**Nagłówek:** Fusion.h</span><span class="sxs-lookup"><span data-stu-id="939d0-113">**Header:** Fusion.h</span></span>  
  
 <span data-ttu-id="939d0-114">**Biblioteka:** Fusion.dll i Mscorwks.dll.</span><span class="sxs-lookup"><span data-stu-id="939d0-114">**Library:** Fusion.dll and Mscorwks.dll.</span></span> <span data-ttu-id="939d0-115">Użyj Fusion.dll zamiast Mscorwks.dll zapewnienie docelowych poprawną wersję programu .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="939d0-115">Use Fusion.dll instead of Mscorwks.dll to ensure that you target the correct version of the .NET Framework.</span></span>  
  
 <span data-ttu-id="939d0-116">**Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="939d0-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="939d0-117">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="939d0-117">See also</span></span>

- [<span data-ttu-id="939d0-118">IInstallReferenceEnum, interfejs</span><span class="sxs-lookup"><span data-stu-id="939d0-118">IInstallReferenceEnum Interface</span></span>](../../../../docs/framework/unmanaged-api/fusion/iinstallreferenceenum-interface.md)
- [<span data-ttu-id="939d0-119">IAssemblyName, interfejs</span><span class="sxs-lookup"><span data-stu-id="939d0-119">IAssemblyName Interface</span></span>](../../../../docs/framework/unmanaged-api/fusion/iassemblyname-interface.md)
- [<span data-ttu-id="939d0-120">Łączenie statycznych funkcji globalnych</span><span class="sxs-lookup"><span data-stu-id="939d0-120">Fusion Global Static Functions</span></span>](../../../../docs/framework/unmanaged-api/fusion/fusion-global-static-functions.md)
