---
title: "Funkcja ForwardTranslateAccelerator (WPF niezarządzany wykaz interfejsów API)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- cpp
api_name:
- ForwardTranslateAccelerator
api_location:
- PresentationHost_v0400.dll
ms.assetid: fff47a86-9d9f-4176-9530-10e1876e393f
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: cca9c78eaf13e04d22fce9f61ce4a7ab9ee09769
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="forwardtranslateaccelerator-function-wpf-unmanaged-api-reference"></a><span data-ttu-id="b802b-102">Funkcja ForwardTranslateAccelerator (WPF niezarządzany wykaz interfejsów API)</span><span class="sxs-lookup"><span data-stu-id="b802b-102">ForwardTranslateAccelerator Function (WPF Unmanaged API Reference)</span></span>
<span data-ttu-id="b802b-103">Ten interfejs API obsługuje infrastrukturę programu Windows Presentation Foundation (WPF) i nie jest przeznaczona do użycia bezpośrednio w kodzie.</span><span class="sxs-lookup"><span data-stu-id="b802b-103">This API supports the Windows Presentation Foundation (WPF) infrastructure and is not intended to be used directly from your code.</span></span>  
  
 <span data-ttu-id="b802b-104">Używane przez infrastrukturę Windows Presentation Foundation (WPF) do zarządzania systemu windows.</span><span class="sxs-lookup"><span data-stu-id="b802b-104">Used by the Windows Presentation Foundation (WPF) infrastructure for windows management.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b802b-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="b802b-105">Syntax</span></span>  
  
```cpp  
HRESULT ForwardTranslateAccelerator(  
   MSG* pMsg,   
   VARIANT_BOOL appUnhandled  
)  
```  
  
#### <a name="parameters"></a><span data-ttu-id="b802b-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="b802b-106">Parameters</span></span>  
 <span data-ttu-id="b802b-107">pMsg</span><span class="sxs-lookup"><span data-stu-id="b802b-107">pMsg</span></span>  
 <span data-ttu-id="b802b-108">Wskaźnik do wiadomości.</span><span class="sxs-lookup"><span data-stu-id="b802b-108">A pointer to a message.</span></span>  
  
 <span data-ttu-id="b802b-109">appUnhandled</span><span class="sxs-lookup"><span data-stu-id="b802b-109">appUnhandled</span></span>  
 <span data-ttu-id="b802b-110">`true`gdy aplikacja została już podana możliwość obsługi komunikatu wejściowego, ale nie jest obsługiwane. w przeciwnym razie `false`.</span><span class="sxs-lookup"><span data-stu-id="b802b-110">`true` when the app has already been given a chance to handle the input message, but has not handled it; otherwise, `false`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b802b-111">Wymagania</span><span class="sxs-lookup"><span data-stu-id="b802b-111">Requirements</span></span>  
 <span data-ttu-id="b802b-112">**Platformy:** zobacz [wymagania systemowe programu .NET Framework](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b802b-112">**Platforms:** See [.NET Framework System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b802b-113">**BIBLIOTEKI DLL:**</span><span class="sxs-lookup"><span data-stu-id="b802b-113">**DLL:**</span></span>  
  
 <span data-ttu-id="b802b-114">W programie .NET Framework 3.0 i 3.5: PresentationHostDLL.dll</span><span class="sxs-lookup"><span data-stu-id="b802b-114">In the .NET Framework 3.0 and 3.5: PresentationHostDLL.dll</span></span>  
  
 <span data-ttu-id="b802b-115">W wersji programu .NET Framework 4 i nowszych: PresentationHost_v0400.dll</span><span class="sxs-lookup"><span data-stu-id="b802b-115">In the .NET Framework 4 and later: PresentationHost_v0400.dll</span></span>  
  
 <span data-ttu-id="b802b-116">**Wersja platformy .NET framework:**[!INCLUDE[net_current_v30plus](../../../../includes/net-current-v30plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b802b-116">**.NET Framework Version:** [!INCLUDE[net_current_v30plus](../../../../includes/net-current-v30plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b802b-117">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="b802b-117">See Also</span></span>  
 [<span data-ttu-id="b802b-118">Niezarządzane interfejsy API WPF — informacje</span><span class="sxs-lookup"><span data-stu-id="b802b-118">WPF Unmanaged API Reference</span></span>](../../../../docs/framework/wpf/advanced/wpf-unmanaged-api-reference.md)
