---
title: IInstallReferenceEnum — Interfejs
ms.date: 03/30/2017
api_name:
- IInstallReferenceEnum
api_location:
- fusion.dll
api_type:
- COM
f1_keywords:
- IInstallReferenceEnum
helpviewer_keywords:
- IInstallReferenceEnum interface [.NET Framework fusion]
ms.assetid: 2863b33b-a541-462c-bbe8-702a2832898e
topic_type:
- apiref
ms.openlocfilehash: d3f7c24b4bd373924c44dbc0490c890e7f1322bd
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73131733"
---
# <a name="iinstallreferenceenum-interface"></a><span data-ttu-id="cb996-102">IInstallReferenceEnum — Interfejs</span><span class="sxs-lookup"><span data-stu-id="cb996-102">IInstallReferenceEnum Interface</span></span>
<span data-ttu-id="cb996-103">Reprezentuje moduł wyliczający dla zestawów, do których istnieją odwołania zainstalowane w globalnej pamięci podręcznej zestawów.</span><span class="sxs-lookup"><span data-stu-id="cb996-103">Represents an enumerator for the referenced assemblies installed in the global assembly cache.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cb996-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="cb996-104">Syntax</span></span>  
  
```cpp  
interface IInstallReferenceEnum : IUnknown {  
    HRESULT GetNextInstallReferenceItem (  
        [out] IInstallReferenceItem **ppRefItem,  
        [in]  DWORD dwFlags,  
        [in]  LPVOID pvReserved  
    );  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="cb996-105">Metody</span><span class="sxs-lookup"><span data-stu-id="cb996-105">Methods</span></span>  
  
|<span data-ttu-id="cb996-106">Metoda</span><span class="sxs-lookup"><span data-stu-id="cb996-106">Method</span></span>|<span data-ttu-id="cb996-107">Opis</span><span class="sxs-lookup"><span data-stu-id="cb996-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="cb996-108">GetNextInstallReferenceItem, metoda</span><span class="sxs-lookup"><span data-stu-id="cb996-108">GetNextInstallReferenceItem Method</span></span>](iinstallreferenceenum-getnextinstallreferenceitem-method.md)|<span data-ttu-id="cb996-109">Pobiera wskaźnik do następnego `IInstallReferenceItem` zawartego w tym `IInstallReferenceEnum`.</span><span class="sxs-lookup"><span data-stu-id="cb996-109">Gets a pointer to the next `IInstallReferenceItem` contained in this `IInstallReferenceEnum`.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="cb996-110">Wymagania</span><span class="sxs-lookup"><span data-stu-id="cb996-110">Requirements</span></span>  
 <span data-ttu-id="cb996-111">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="cb996-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="cb996-112">**Nagłówek:** Fusion. h</span><span class="sxs-lookup"><span data-stu-id="cb996-112">**Header:** Fusion.h</span></span>  
  
 <span data-ttu-id="cb996-113">**Wersje .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="cb996-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cb996-114">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="cb996-114">See also</span></span>

- [<span data-ttu-id="cb996-115">Interfejsy łączenia</span><span class="sxs-lookup"><span data-stu-id="cb996-115">Fusion Interfaces</span></span>](fusion-interfaces.md)
- [<span data-ttu-id="cb996-116">IInstallReferenceItem, interfejs</span><span class="sxs-lookup"><span data-stu-id="cb996-116">IInstallReferenceItem Interface</span></span>](iinstallreferenceitem-interface.md)
