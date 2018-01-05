---
title: "Funkcja CreateIDispatchSTAForwarder (WPF niezarządzany wykaz interfejsów API)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: cpp
api_name: CreateIDispatchSTAForwarder
api_location: PresentationHost_v0400.dll
ms.assetid: 57a02dfa-f091-4ace-9c06-1f4ab52b3527
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 5139784fdc067c09d032c0bf37114e0eb1caac33
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="createidispatchstaforwarder-function-wpf-unmanaged-api-reference"></a><span data-ttu-id="3c2fc-102">Funkcja CreateIDispatchSTAForwarder (WPF niezarządzany wykaz interfejsów API)</span><span class="sxs-lookup"><span data-stu-id="3c2fc-102">CreateIDispatchSTAForwarder Function (WPF Unmanaged API Reference)</span></span>
<span data-ttu-id="3c2fc-103">Ten interfejs API obsługuje infrastrukturę programu Windows Presentation Foundation (WPF) i nie jest przeznaczona do użycia bezpośrednio w kodzie.</span><span class="sxs-lookup"><span data-stu-id="3c2fc-103">This API supports the Windows Presentation Foundation (WPF) infrastructure and is not intended to be used directly from your code.</span></span>  
  
 <span data-ttu-id="3c2fc-104">Używane przez infrastrukturę Windows Presentation Foundation (WPF) do zarządzania wątku i systemu windows.</span><span class="sxs-lookup"><span data-stu-id="3c2fc-104">Used by the Windows Presentation Foundation (WPF) infrastructure for thread and windows management.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3c2fc-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="3c2fc-105">Syntax</span></span>  
  
```cpp  
HRESULT CreateIDispatchSTAForwarder(  
   __in IDispatch *pDispatchDelegate,   
   __deref_out IDispatch **ppForwarder  
)  
```  
  
#### <a name="parameters"></a><span data-ttu-id="3c2fc-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="3c2fc-106">Parameters</span></span>  
  
## <a name="property-valuereturn-value"></a><span data-ttu-id="3c2fc-107">Wartość właściwości/Zwracana wartość</span><span class="sxs-lookup"><span data-stu-id="3c2fc-107">Property Value/Return Value</span></span>  
 <span data-ttu-id="3c2fc-108">pDispatchDelegate</span><span class="sxs-lookup"><span data-stu-id="3c2fc-108">pDispatchDelegate</span></span>  
 <span data-ttu-id="3c2fc-109">Wskaźnik do `IDispatch` interfejsu.</span><span class="sxs-lookup"><span data-stu-id="3c2fc-109">A pointer to an `IDispatch` interface.</span></span>  
  
 <span data-ttu-id="3c2fc-110">ppForwarder</span><span class="sxs-lookup"><span data-stu-id="3c2fc-110">ppForwarder</span></span>  
 <span data-ttu-id="3c2fc-111">Wskaźnik do adresu `IDispatch` interfejsu.</span><span class="sxs-lookup"><span data-stu-id="3c2fc-111">A pointer to the address of an `IDispatch` interface.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3c2fc-112">Wymagania</span><span class="sxs-lookup"><span data-stu-id="3c2fc-112">Requirements</span></span>  
 <span data-ttu-id="3c2fc-113">**Platformy:** zobacz [wymagania systemowe programu .NET Framework](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3c2fc-113">**Platforms:** See [.NET Framework System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3c2fc-114">**BIBLIOTEKI DLL:**</span><span class="sxs-lookup"><span data-stu-id="3c2fc-114">**DLL:**</span></span>  
  
 <span data-ttu-id="3c2fc-115">W programie .NET Framework 3.0 i 3.5: PresentationHostDLL.dll</span><span class="sxs-lookup"><span data-stu-id="3c2fc-115">In the .NET Framework 3.0 and 3.5: PresentationHostDLL.dll</span></span>  
  
 <span data-ttu-id="3c2fc-116">W wersji programu .NET Framework 4 i nowszych: PresentationHost_v0400.dll</span><span class="sxs-lookup"><span data-stu-id="3c2fc-116">In the .NET Framework 4 and later: PresentationHost_v0400.dll</span></span>  
  
 <span data-ttu-id="3c2fc-117">**Wersja platformy .NET framework:**[!INCLUDE[net_current_v30plus](../../../../includes/net-current-v30plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3c2fc-117">**.NET Framework Version:** [!INCLUDE[net_current_v30plus](../../../../includes/net-current-v30plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3c2fc-118">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="3c2fc-118">See Also</span></span>  
 [<span data-ttu-id="3c2fc-119">Niezarządzane interfejsy API WPF — informacje</span><span class="sxs-lookup"><span data-stu-id="3c2fc-119">WPF Unmanaged API Reference</span></span>](../../../../docs/framework/wpf/advanced/wpf-unmanaged-api-reference.md)
