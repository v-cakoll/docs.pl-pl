---
title: "Funkcja LoadFromHistory (WPF niezarządzany wykaz interfejsów API)"
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
- LoadFromHistory
api_location:
- PresentationHost_v0400.dll
ms.assetid: d037c062-a911-4949-b251-ccd3e48b1d17
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 6eca1c30664e381101b6e51c1347341432a042b2
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="loadfromhistory-function-wpf-unmanaged-api-reference"></a><span data-ttu-id="ca34e-102">Funkcja LoadFromHistory (WPF niezarządzany wykaz interfejsów API)</span><span class="sxs-lookup"><span data-stu-id="ca34e-102">LoadFromHistory Function (WPF Unmanaged API Reference)</span></span>
<span data-ttu-id="ca34e-103">Ten interfejs API obsługuje infrastrukturę programu Windows Presentation Foundation (WPF) i nie jest przeznaczona do użycia bezpośrednio w kodzie.</span><span class="sxs-lookup"><span data-stu-id="ca34e-103">This API supports the Windows Presentation Foundation (WPF) infrastructure and is not intended to be used directly from your code.</span></span>  
  
 <span data-ttu-id="ca34e-104">Używane przez infrastrukturę Windows Presentation Foundation (WPF) do zarządzania systemu windows.</span><span class="sxs-lookup"><span data-stu-id="ca34e-104">Used by the Windows Presentation Foundation (WPF) infrastructure for windows management.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ca34e-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="ca34e-105">Syntax</span></span>  
  
```cpp  
HRESULT LoadFromHistory_export(  
        IStream* pHistoryStream,   
        IBindCtx* pBindCtx  
)  
```  
  
#### <a name="parameters"></a><span data-ttu-id="ca34e-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="ca34e-106">Parameters</span></span>  
 <span data-ttu-id="ca34e-107">pHistoryStream</span><span class="sxs-lookup"><span data-stu-id="ca34e-107">pHistoryStream</span></span>  
 <span data-ttu-id="ca34e-108">Wskaźnik do strumienia informacji historii.</span><span class="sxs-lookup"><span data-stu-id="ca34e-108">A pointer to a stream of history information.</span></span>  
  
 <span data-ttu-id="ca34e-109">pBindCtx</span><span class="sxs-lookup"><span data-stu-id="ca34e-109">pBindCtx</span></span>  
 <span data-ttu-id="ca34e-110">Wskaźnik do kontekstu powiązania.</span><span class="sxs-lookup"><span data-stu-id="ca34e-110">A pointer to a bind context.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ca34e-111">Wymagania</span><span class="sxs-lookup"><span data-stu-id="ca34e-111">Requirements</span></span>  
 <span data-ttu-id="ca34e-112">**Platformy:** zobacz [wymagania systemowe programu .NET Framework](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ca34e-112">**Platforms:** See [.NET Framework System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ca34e-113">**BIBLIOTEKI DLL:**</span><span class="sxs-lookup"><span data-stu-id="ca34e-113">**DLL:**</span></span>  
  
 <span data-ttu-id="ca34e-114">W programie .NET Framework 3.0 i 3.5: PresentationHostDLL.dll</span><span class="sxs-lookup"><span data-stu-id="ca34e-114">In the .NET Framework 3.0 and 3.5: PresentationHostDLL.dll</span></span>  
  
 <span data-ttu-id="ca34e-115">W wersji programu .NET Framework 4 i nowszych: PresentationHost_v0400.dll</span><span class="sxs-lookup"><span data-stu-id="ca34e-115">In the .NET Framework 4 and later: PresentationHost_v0400.dll</span></span>  
  
 <span data-ttu-id="ca34e-116">**Wersja platformy .NET framework:**[!INCLUDE[net_current_v30plus](../../../../includes/net-current-v30plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ca34e-116">**.NET Framework Version:** [!INCLUDE[net_current_v30plus](../../../../includes/net-current-v30plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ca34e-117">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="ca34e-117">See Also</span></span>  
 [<span data-ttu-id="ca34e-118">Niezarządzane interfejsy API WPF — informacje</span><span class="sxs-lookup"><span data-stu-id="ca34e-118">WPF Unmanaged API Reference</span></span>](../../../../docs/framework/wpf/advanced/wpf-unmanaged-api-reference.md)
