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
ms.openlocfilehash: 63195ce2a47add2606f528b18d0d1d58ab0d968c
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="createidispatchstaforwarder-function-wpf-unmanaged-api-reference"></a><span data-ttu-id="07f00-102">Funkcja CreateIDispatchSTAForwarder (WPF niezarządzany wykaz interfejsów API)</span><span class="sxs-lookup"><span data-stu-id="07f00-102">CreateIDispatchSTAForwarder Function (WPF Unmanaged API Reference)</span></span>
<span data-ttu-id="07f00-103">Ten interfejs API obsługuje infrastrukturę programu Windows Presentation Foundation (WPF) i nie jest przeznaczona do użycia bezpośrednio w kodzie.</span><span class="sxs-lookup"><span data-stu-id="07f00-103">This API supports the Windows Presentation Foundation (WPF) infrastructure and is not intended to be used directly from your code.</span></span>  
  
 <span data-ttu-id="07f00-104">Używane przez infrastrukturę Windows Presentation Foundation (WPF) do zarządzania wątku i systemu windows.</span><span class="sxs-lookup"><span data-stu-id="07f00-104">Used by the Windows Presentation Foundation (WPF) infrastructure for thread and windows management.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="07f00-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="07f00-105">Syntax</span></span>  
  
```cpp  
HRESULT CreateIDispatchSTAForwarder(  
   __in IDispatch *pDispatchDelegate,   
   __deref_out IDispatch **ppForwarder  
)  
```  
  
#### <a name="parameters"></a><span data-ttu-id="07f00-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="07f00-106">Parameters</span></span>  
  
## <a name="property-valuereturn-value"></a><span data-ttu-id="07f00-107">Wartość właściwości/Zwracana wartość</span><span class="sxs-lookup"><span data-stu-id="07f00-107">Property Value/Return Value</span></span>  
 <span data-ttu-id="07f00-108">pDispatchDelegate</span><span class="sxs-lookup"><span data-stu-id="07f00-108">pDispatchDelegate</span></span>  
 <span data-ttu-id="07f00-109">Wskaźnik do `IDispatch` interfejsu.</span><span class="sxs-lookup"><span data-stu-id="07f00-109">A pointer to an `IDispatch` interface.</span></span>  
  
 <span data-ttu-id="07f00-110">ppForwarder</span><span class="sxs-lookup"><span data-stu-id="07f00-110">ppForwarder</span></span>  
 <span data-ttu-id="07f00-111">Wskaźnik do adresu `IDispatch` interfejsu.</span><span class="sxs-lookup"><span data-stu-id="07f00-111">A pointer to the address of an `IDispatch` interface.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="07f00-112">Wymagania</span><span class="sxs-lookup"><span data-stu-id="07f00-112">Requirements</span></span>  
 <span data-ttu-id="07f00-113">**Platformy:** zobacz [wymagania systemowe programu .NET Framework](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="07f00-113">**Platforms:** See [.NET Framework System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="07f00-114">**BIBLIOTEKI DLL:**</span><span class="sxs-lookup"><span data-stu-id="07f00-114">**DLL:**</span></span>  
  
 <span data-ttu-id="07f00-115">W programie .NET Framework 3.0 i 3.5: PresentationHostDLL.dll</span><span class="sxs-lookup"><span data-stu-id="07f00-115">In the .NET Framework 3.0 and 3.5: PresentationHostDLL.dll</span></span>  
  
 <span data-ttu-id="07f00-116">W wersji programu .NET Framework 4 i nowszych: PresentationHost_v0400.dll</span><span class="sxs-lookup"><span data-stu-id="07f00-116">In the .NET Framework 4 and later: PresentationHost_v0400.dll</span></span>  
  
 <span data-ttu-id="07f00-117">**Wersja platformy .NET framework:**[!INCLUDE[net_current_v30plus](../../../../includes/net-current-v30plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="07f00-117">**.NET Framework Version:** [!INCLUDE[net_current_v30plus](../../../../includes/net-current-v30plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="07f00-118">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="07f00-118">See Also</span></span>  
 [<span data-ttu-id="07f00-119">WPF niezarządzany wykaz interfejsów API</span><span class="sxs-lookup"><span data-stu-id="07f00-119">WPF Unmanaged API Reference</span></span>](../../../../docs/framework/wpf/advanced/wpf-unmanaged-api-reference.md)
