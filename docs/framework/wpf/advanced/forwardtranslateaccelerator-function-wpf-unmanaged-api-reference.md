---
title: "Funkcja ForwardTranslateAccelerator (WPF niezarządzany wykaz interfejsów API)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: cpp
api_name: ForwardTranslateAccelerator
api_location: PresentationHost_v0400.dll
ms.assetid: fff47a86-9d9f-4176-9530-10e1876e393f
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 663b28ed1a9430a6280ccd0ee9a44da2dea0c3cd
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="forwardtranslateaccelerator-function-wpf-unmanaged-api-reference"></a><span data-ttu-id="12a5f-102">Funkcja ForwardTranslateAccelerator (WPF niezarządzany wykaz interfejsów API)</span><span class="sxs-lookup"><span data-stu-id="12a5f-102">ForwardTranslateAccelerator Function (WPF Unmanaged API Reference)</span></span>
<span data-ttu-id="12a5f-103">Ten interfejs API obsługuje infrastrukturę programu Windows Presentation Foundation (WPF) i nie jest przeznaczona do użycia bezpośrednio w kodzie.</span><span class="sxs-lookup"><span data-stu-id="12a5f-103">This API supports the Windows Presentation Foundation (WPF) infrastructure and is not intended to be used directly from your code.</span></span>  
  
 <span data-ttu-id="12a5f-104">Używane przez infrastrukturę Windows Presentation Foundation (WPF) do zarządzania systemu windows.</span><span class="sxs-lookup"><span data-stu-id="12a5f-104">Used by the Windows Presentation Foundation (WPF) infrastructure for windows management.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="12a5f-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="12a5f-105">Syntax</span></span>  
  
```cpp  
HRESULT ForwardTranslateAccelerator(  
   MSG* pMsg,   
   VARIANT_BOOL appUnhandled  
)  
```  
  
#### <a name="parameters"></a><span data-ttu-id="12a5f-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="12a5f-106">Parameters</span></span>  
 <span data-ttu-id="12a5f-107">pMsg</span><span class="sxs-lookup"><span data-stu-id="12a5f-107">pMsg</span></span>  
 <span data-ttu-id="12a5f-108">Wskaźnik do wiadomości.</span><span class="sxs-lookup"><span data-stu-id="12a5f-108">A pointer to a message.</span></span>  
  
 <span data-ttu-id="12a5f-109">appUnhandled</span><span class="sxs-lookup"><span data-stu-id="12a5f-109">appUnhandled</span></span>  
 <span data-ttu-id="12a5f-110">`true`gdy aplikacja została już podana możliwość obsługi komunikatu wejściowego, ale nie jest obsługiwane. w przeciwnym razie `false`.</span><span class="sxs-lookup"><span data-stu-id="12a5f-110">`true` when the app has already been given a chance to handle the input message, but has not handled it; otherwise, `false`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="12a5f-111">Wymagania</span><span class="sxs-lookup"><span data-stu-id="12a5f-111">Requirements</span></span>  
 <span data-ttu-id="12a5f-112">**Platformy:** zobacz [wymagania systemowe programu .NET Framework](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="12a5f-112">**Platforms:** See [.NET Framework System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="12a5f-113">**BIBLIOTEKI DLL:**</span><span class="sxs-lookup"><span data-stu-id="12a5f-113">**DLL:**</span></span>  
  
 <span data-ttu-id="12a5f-114">W programie .NET Framework 3.0 i 3.5: PresentationHostDLL.dll</span><span class="sxs-lookup"><span data-stu-id="12a5f-114">In the .NET Framework 3.0 and 3.5: PresentationHostDLL.dll</span></span>  
  
 <span data-ttu-id="12a5f-115">W wersji programu .NET Framework 4 i nowszych: PresentationHost_v0400.dll</span><span class="sxs-lookup"><span data-stu-id="12a5f-115">In the .NET Framework 4 and later: PresentationHost_v0400.dll</span></span>  
  
 <span data-ttu-id="12a5f-116">**Wersja platformy .NET framework:**[!INCLUDE[net_current_v30plus](../../../../includes/net-current-v30plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="12a5f-116">**.NET Framework Version:** [!INCLUDE[net_current_v30plus](../../../../includes/net-current-v30plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="12a5f-117">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="12a5f-117">See Also</span></span>  
 [<span data-ttu-id="12a5f-118">WPF niezarządzany wykaz interfejsów API</span><span class="sxs-lookup"><span data-stu-id="12a5f-118">WPF Unmanaged API Reference</span></span>](../../../../docs/framework/wpf/advanced/wpf-unmanaged-api-reference.md)
