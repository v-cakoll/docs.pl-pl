---
title: Funkcja CreateIDispatchSTAForwarder — odwołanie do niezarządzanego interfejsu API WPF WPF
titleSuffix: ''
ms.date: 03/30/2017
dev_langs:
- cpp
api_name:
- CreateIDispatchSTAForwarder
api_location:
- PresentationHost_v0400.dll
ms.assetid: 57a02dfa-f091-4ace-9c06-1f4ab52b3527
ms.openlocfilehash: e151ffa6eb5f1dc7479c699e0d7f9f3f57833ebd
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79174722"
---
# <a name="createidispatchstaforwarder-function-wpf-unmanaged-api-reference"></a><span data-ttu-id="59cb4-102">Funkcja CreateIDispatchSTAForwarder (odwołanie do interfejsu API niezarządzanego WPF)</span><span class="sxs-lookup"><span data-stu-id="59cb4-102">CreateIDispatchSTAForwarder Function (WPF Unmanaged API Reference)</span></span>
<span data-ttu-id="59cb4-103">Ten interfejs API obsługuje infrastrukturę Programu Windows Presentation Foundation (WPF) i nie jest przeznaczony do użycia bezpośrednio z kodu.</span><span class="sxs-lookup"><span data-stu-id="59cb4-103">This API supports the Windows Presentation Foundation (WPF) infrastructure and is not intended to be used directly from your code.</span></span>  
  
 <span data-ttu-id="59cb4-104">Używane przez Windows Presentation Foundation (WPF) infrastruktury do zarządzania wątkami i oknami.</span><span class="sxs-lookup"><span data-stu-id="59cb4-104">Used by the Windows Presentation Foundation (WPF) infrastructure for thread and windows management.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="59cb4-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="59cb4-105">Syntax</span></span>  
  
```cpp  
HRESULT CreateIDispatchSTAForwarder(  
   __in IDispatch *pDispatchDelegate,
   __deref_out IDispatch **ppForwarder  
)  
```  
  
## <a name="parameters"></a><span data-ttu-id="59cb4-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="59cb4-106">Parameters</span></span>  
  
## <a name="property-valuereturn-value"></a><span data-ttu-id="59cb4-107">Wartość właściwości/Zwracana wartość</span><span class="sxs-lookup"><span data-stu-id="59cb4-107">Property Value/Return Value</span></span>  
 <span data-ttu-id="59cb4-108">pDispatchDelegate</span><span class="sxs-lookup"><span data-stu-id="59cb4-108">pDispatchDelegate</span></span>  
 <span data-ttu-id="59cb4-109">Wskaźnik do `IDispatch` interfejsu.</span><span class="sxs-lookup"><span data-stu-id="59cb4-109">A pointer to an `IDispatch` interface.</span></span>  
  
 <span data-ttu-id="59cb4-110">ppForwarder (Polski)</span><span class="sxs-lookup"><span data-stu-id="59cb4-110">ppForwarder</span></span>  
 <span data-ttu-id="59cb4-111">Wskaźnik do adresu `IDispatch` interfejsu.</span><span class="sxs-lookup"><span data-stu-id="59cb4-111">A pointer to the address of an `IDispatch` interface.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="59cb4-112">Wymagania</span><span class="sxs-lookup"><span data-stu-id="59cb4-112">Requirements</span></span>  
 <span data-ttu-id="59cb4-113">**Platformy:** Zobacz [.NET Framework Wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="59cb4-113">**Platforms:** See [.NET Framework System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="59cb4-114">**Dll:**</span><span class="sxs-lookup"><span data-stu-id="59cb4-114">**DLL:**</span></span>  
  
 <span data-ttu-id="59cb4-115">W pliku .NET Framework 3.0 i 3.5: PresentationHostDLL.dll</span><span class="sxs-lookup"><span data-stu-id="59cb4-115">In the .NET Framework 3.0 and 3.5: PresentationHostDLL.dll</span></span>  
  
 <span data-ttu-id="59cb4-116">W pliku .NET Framework 4 i nowszym: PresentationHost_v0400.dll</span><span class="sxs-lookup"><span data-stu-id="59cb4-116">In the .NET Framework 4 and later: PresentationHost_v0400.dll</span></span>  
  
 <span data-ttu-id="59cb4-117">**Wersja programu .NET Framework:**[!INCLUDE[net_current_v30plus](../../../../includes/net-current-v30plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="59cb4-117">**.NET Framework Version:** [!INCLUDE[net_current_v30plus](../../../../includes/net-current-v30plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="59cb4-118">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="59cb4-118">See also</span></span>

- [<span data-ttu-id="59cb4-119">Niezarządzane interfejsy API WPF — informacje</span><span class="sxs-lookup"><span data-stu-id="59cb4-119">WPF Unmanaged API Reference</span></span>](wpf-unmanaged-api-reference.md)
