---
title: Otoki COM
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- wrapper classes
- COM interop, COM wrappers
- COM wrappers
- COM, wrappers
- interoperation with unmanaged code, COM wrappers
- COM callable wrappers
ms.assetid: e56c485b-6b67-4345-8e66-fd21835a6092
caps.latest.revision: "12"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: b899ed162fa626f8c378923907f275cebf9a7db4
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/19/2018
---
# <a name="com-wrappers"></a><span data-ttu-id="1428b-102">Otoki COM</span><span class="sxs-lookup"><span data-stu-id="1428b-102">COM Wrappers</span></span>
<span data-ttu-id="1428b-103">COM różni się od modelu obiektów programu .NET Framework w kilka sposobów:</span><span class="sxs-lookup"><span data-stu-id="1428b-103">COM differs from the .NET Framework object model in several important ways:</span></span>  
  
-   <span data-ttu-id="1428b-104">Klienci obiektów COM należy zarządzać okres istnienia tych obiektów; środowisko uruchomieniowe języka wspólnego zarządza czasem istnienia obiektów w ich środowisku.</span><span class="sxs-lookup"><span data-stu-id="1428b-104">Clients of COM objects must manage the lifetime of those objects; the common language runtime manages the lifetime of objects in its environment.</span></span>  
  
-   <span data-ttu-id="1428b-105">Klienci obiektów COM wykrywa, czy usługa jest dostępna, żądając interfejs, który udostępnia usługi i odzyskać wskaźnika interfejsu, czy nie.</span><span class="sxs-lookup"><span data-stu-id="1428b-105">Clients of COM objects discover whether a service is available by requesting an interface that provides that service and getting back an interface pointer, or not.</span></span> <span data-ttu-id="1428b-106">Klienci obiektów .NET mogą uzyskiwać opisu funkcji obiektu za pomocą odbicia.</span><span class="sxs-lookup"><span data-stu-id="1428b-106">Clients of .NET objects can obtain a description of an object's functionality using reflection.</span></span>  
  
-   <span data-ttu-id="1428b-107">NET obiekty znajdują się w pamięci, zarządzanych przez środowiska wykonawczego .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="1428b-107">NET objects reside in memory managed by the .NET Framework execution environment.</span></span> <span data-ttu-id="1428b-108">Poruszanie obiektów w pamięci, ze względu na wydajność i aktualizować wszystkie odwołania do obiektów, które powoduje przeniesienie można środowiska wykonawczego.</span><span class="sxs-lookup"><span data-stu-id="1428b-108">The execution environment can move objects around in memory for performance reasons and update all references to the objects it moves.</span></span> <span data-ttu-id="1428b-109">Klienci Niezarządzani po otrzymaniu wskaźnika do obiektu, zależą od obiektu ma pozostać w tej samej lokalizacji.</span><span class="sxs-lookup"><span data-stu-id="1428b-109">Unmanaged clients, having obtained a pointer to an object, rely on the object to remain at the same location.</span></span> <span data-ttu-id="1428b-110">Ci klienci mają mechanizm zajmujących się obiekt, którego lokalizacja nie jest stały.</span><span class="sxs-lookup"><span data-stu-id="1428b-110">These clients have no mechanism for dealing with an object whose location is not fixed.</span></span>  
  
 <span data-ttu-id="1428b-111">Aby wyeliminować te różnice, środowiska uruchomieniowego zawiera klasy otoki, aby klienci zarządzane i niezarządzane, wydaje się, że wywoływania obiektów w ich środowisku odpowiednich.</span><span class="sxs-lookup"><span data-stu-id="1428b-111">To overcome these differences, the runtime provides wrapper classes to make both managed and unmanaged clients think they are calling objects within their respective environment.</span></span> <span data-ttu-id="1428b-112">Zawsze, gdy klient zarządzany wywołuje metodę dla obiekt COM, tworzy środowisko uruchomieniowe [wywoływana otoka środowiska uruchomieniowego](../../../docs/framework/interop/runtime-callable-wrapper.md) (otoki RCW).</span><span class="sxs-lookup"><span data-stu-id="1428b-112">Whenever your managed client calls a method on a COM object, the runtime creates a [runtime callable wrapper](../../../docs/framework/interop/runtime-callable-wrapper.md) (RCW).</span></span> <span data-ttu-id="1428b-113">RCWs abstrakcyjnej różnice między mechanizmów odwołania zarządzane i niezarządzane, między innymi.</span><span class="sxs-lookup"><span data-stu-id="1428b-113">RCWs abstract the differences between managed and unmanaged reference mechanisms, among other things.</span></span> <span data-ttu-id="1428b-114">Środowisko uruchomieniowe tworzy także [wywoływana otoka COM](../../../docs/framework/interop/com-callable-wrapper.md) (CCW), aby odwrócić procesu włączania klientowi COM bezproblemowo wywołać metody dla obiektu .NET.</span><span class="sxs-lookup"><span data-stu-id="1428b-114">The runtime also creates a [COM callable wrapper](../../../docs/framework/interop/com-callable-wrapper.md) (CCW) to reverse the process, enabling a COM client to seamlessly call a method on a .NET object.</span></span> <span data-ttu-id="1428b-115">Jak pokazano na poniższej ilustracji, perspektywy kod wywołujący Określa, która klasa otoki tworzy środowiska uruchomieniowego.</span><span class="sxs-lookup"><span data-stu-id="1428b-115">As the following illustration shows, the perspective of the calling code determines which wrapper class the runtime creates.</span></span>  
  
 <span data-ttu-id="1428b-116">![Przegląd otoki COM](../../../docs/framework/interop/media/bidirectional.gif "dwukierunkowych")</span><span class="sxs-lookup"><span data-stu-id="1428b-116">![COM wrapper overview](../../../docs/framework/interop/media/bidirectional.gif "bidirectional")</span></span>  
<span data-ttu-id="1428b-117">Przegląd otoki COM</span><span class="sxs-lookup"><span data-stu-id="1428b-117">COM wrapper overview</span></span>  
  
 <span data-ttu-id="1428b-118">W większości przypadków standardowe otoki RCW lub CCW generowane przez środowisko uruchomieniowe zawiera odpowiednie marshaling dla wywołania, które przekraczają granicę między COM i .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="1428b-118">In most cases, the standard RCW or CCW generated by the runtime provides adequate marshaling for calls that cross the boundary between COM and the .NET Framework.</span></span> <span data-ttu-id="1428b-119">Za pomocą atrybutów niestandardowych, można opcjonalnie dostosować sposób środowiska uruchomieniowego reprezentuje kod zarządzane i niezarządzane.</span><span class="sxs-lookup"><span data-stu-id="1428b-119">Using custom attributes, you can optionally adjust the way the runtime represents managed and unmanaged code.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1428b-120">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="1428b-120">See Also</span></span>  
 [<span data-ttu-id="1428b-121">Współdziałanie COM zaawansowane</span><span class="sxs-lookup"><span data-stu-id="1428b-121">Advanced COM Interoperability</span></span>](http://msdn.microsoft.com/library/3ada36e5-2390-4d70-b490-6ad8de92f2fb)  
 [<span data-ttu-id="1428b-122">Wywoływana otoka środowiska uruchomieniowego</span><span class="sxs-lookup"><span data-stu-id="1428b-122">Runtime Callable Wrapper</span></span>](../../../docs/framework/interop/runtime-callable-wrapper.md)  
 [<span data-ttu-id="1428b-123">Wywoływana otoka COM</span><span class="sxs-lookup"><span data-stu-id="1428b-123">COM Callable Wrapper</span></span>](../../../docs/framework/interop/com-callable-wrapper.md)  
 [<span data-ttu-id="1428b-124">Dostosowywanie standardowych otoki</span><span class="sxs-lookup"><span data-stu-id="1428b-124">Customizing Standard Wrappers</span></span>](http://msdn.microsoft.com/library/c40d089b-6a3c-41b5-a20d-d760c215e49d)  
 [<span data-ttu-id="1428b-125">Porady: dostosowywanie wywoływane otoki środowiska uruchomieniowego</span><span class="sxs-lookup"><span data-stu-id="1428b-125">How to: Customize Runtime Callable Wrappers</span></span>](http://msdn.microsoft.com/library/4a4bb3da-4d60-4517-99f2-78d46a681732)
