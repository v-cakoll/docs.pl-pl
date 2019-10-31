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
ms.openlocfilehash: f089769f854bad5d3e572e0307734e06e72ca89c
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73108564"
---
# <a name="createinstallreferenceenum-function"></a><span data-ttu-id="cf478-102">CreateInstallReferenceEnum — Funkcja</span><span class="sxs-lookup"><span data-stu-id="cf478-102">CreateInstallReferenceEnum Function</span></span>
<span data-ttu-id="cf478-103">Pobiera wskaźnik do wystąpienia [IInstallReferenceEnum](iinstallreferenceenum-interface.md) , które reprezentuje listę odwołań aplikacji do określonego zestawu.</span><span class="sxs-lookup"><span data-stu-id="cf478-103">Gets a pointer to an [IInstallReferenceEnum](iinstallreferenceenum-interface.md) instance that represents a list of an application's references to the specified assembly.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cf478-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="cf478-104">Syntax</span></span>  
  
```cpp  
HRESULT CreateInstallReferenceEnum (  
    [out] IInstallReferenceEnum **ppRefEnum,  
    [in]  IAssemblyName         *pName,  
    [in]  DWORD                 dwFlags,  
    [in]  LPVOID                pvReserved  
 );  
```  
  
## <a name="parameters"></a><span data-ttu-id="cf478-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="cf478-105">Parameters</span></span>  
 `ppRefEnum`  
 <span data-ttu-id="cf478-106">określoną Zwrócony wskaźnik `IInstallReferenceEnum`.</span><span class="sxs-lookup"><span data-stu-id="cf478-106">[out] The returned `IInstallReferenceEnum` pointer.</span></span>  
  
 `pName`  
 <span data-ttu-id="cf478-107">podczas [IAssemblyName](iassemblyname-interface.md) , który identyfikuje zestaw, dla którego mają zostać wyliczone odwołania.</span><span class="sxs-lookup"><span data-stu-id="cf478-107">[in] The [IAssemblyName](iassemblyname-interface.md) that identifies the assembly for which to enumerate references.</span></span>  
  
 `dwFlags`  
 <span data-ttu-id="cf478-108">podczas Flagi wpływające na zachowanie modułu wyliczającego.</span><span class="sxs-lookup"><span data-stu-id="cf478-108">[in] Flags that influence the enumerator's behavior.</span></span>  
  
 `pvReserved`  
 <span data-ttu-id="cf478-109">podczas Zarezerwowane do użytku w przyszłości.</span><span class="sxs-lookup"><span data-stu-id="cf478-109">[in] Reserved for future extensibility.</span></span> <span data-ttu-id="cf478-110">`pvReserved` musi być odwołaniem o wartości null.</span><span class="sxs-lookup"><span data-stu-id="cf478-110">`pvReserved` must be a null reference.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="cf478-111">Wymagania</span><span class="sxs-lookup"><span data-stu-id="cf478-111">Requirements</span></span>  
 <span data-ttu-id="cf478-112">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="cf478-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="cf478-113">**Nagłówek:** Fusion. h</span><span class="sxs-lookup"><span data-stu-id="cf478-113">**Header:** Fusion.h</span></span>  
  
 <span data-ttu-id="cf478-114">**Biblioteka:** Fusion. dll i mscorwks. dll.</span><span class="sxs-lookup"><span data-stu-id="cf478-114">**Library:** Fusion.dll and Mscorwks.dll.</span></span> <span data-ttu-id="cf478-115">Aby upewnić się, że docelowa wersja .NET Framework, należy użyć pliku Fusion. dll zamiast Mscorwks. dll.</span><span class="sxs-lookup"><span data-stu-id="cf478-115">Use Fusion.dll instead of Mscorwks.dll to ensure that you target the correct version of the .NET Framework.</span></span>  
  
 <span data-ttu-id="cf478-116">**Wersje .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="cf478-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cf478-117">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="cf478-117">See also</span></span>

- [<span data-ttu-id="cf478-118">IInstallReferenceEnum, interfejs</span><span class="sxs-lookup"><span data-stu-id="cf478-118">IInstallReferenceEnum Interface</span></span>](iinstallreferenceenum-interface.md)
- [<span data-ttu-id="cf478-119">IAssemblyName, interfejs</span><span class="sxs-lookup"><span data-stu-id="cf478-119">IAssemblyName Interface</span></span>](iassemblyname-interface.md)
- [<span data-ttu-id="cf478-120">Łączenie statycznych funkcji globalnych</span><span class="sxs-lookup"><span data-stu-id="cf478-120">Fusion Global Static Functions</span></span>](fusion-global-static-functions.md)
