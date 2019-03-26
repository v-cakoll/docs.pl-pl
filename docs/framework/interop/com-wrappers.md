---
title: Otoki COM
ms.date: 03/30/2017
helpviewer_keywords:
- wrapper classes
- COM interop, COM wrappers
- COM wrappers
- COM, wrappers
- interoperation with unmanaged code, COM wrappers
- COM callable wrappers
ms.assetid: e56c485b-6b67-4345-8e66-fd21835a6092
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: ce15e0535bbd6bc67054c651a518f11cf9dd2ae1
ms.sourcegitcommit: 3630c2515809e6f4b7dbb697a3354efec105a5cd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/25/2019
ms.locfileid: "58410358"
---
# <a name="com-wrappers"></a><span data-ttu-id="2e391-102">Otoki COM</span><span class="sxs-lookup"><span data-stu-id="2e391-102">COM Wrappers</span></span>
<span data-ttu-id="2e391-103">COM różni się od modelu obiektów programu .NET Framework na kilka sposobów ważne:</span><span class="sxs-lookup"><span data-stu-id="2e391-103">COM differs from the .NET Framework object model in several important ways:</span></span>  
  
-   <span data-ttu-id="2e391-104">Klienci obiektów COM musi zarządzać okresem istnienia tych obiektów; środowisko uruchomieniowe języka wspólnego zarządza czasem istnienia obiektów w swoim środowisku.</span><span class="sxs-lookup"><span data-stu-id="2e391-104">Clients of COM objects must manage the lifetime of those objects; the common language runtime manages the lifetime of objects in its environment.</span></span>  
  
-   <span data-ttu-id="2e391-105">Klienci obiektów COM Dowiedz się, czy usługa jest dostępna, żądając interfejs, który zawiera tę usługę i powrót wskaźnika interfejsu, czy nie.</span><span class="sxs-lookup"><span data-stu-id="2e391-105">Clients of COM objects discover whether a service is available by requesting an interface that provides that service and getting back an interface pointer, or not.</span></span> <span data-ttu-id="2e391-106">Klienci obiektów platformy .NET można uzyskać opisu funkcji obiektu przy użyciu odbicia.</span><span class="sxs-lookup"><span data-stu-id="2e391-106">Clients of .NET objects can obtain a description of an object's functionality using reflection.</span></span>  
  
-   <span data-ttu-id="2e391-107">Obiekty sieci znajdują się w pamięci zarządzane przez środowisko wykonawcze .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="2e391-107">NET objects reside in memory managed by the .NET Framework execution environment.</span></span> <span data-ttu-id="2e391-108">Środowisko wykonawcze można poruszać obiektów w pamięci, ze względu na wydajność i zaktualizuj wszystkie odwołania do obiektów, które przenosi.</span><span class="sxs-lookup"><span data-stu-id="2e391-108">The execution environment can move objects around in memory for performance reasons and update all references to the objects it moves.</span></span> <span data-ttu-id="2e391-109">Niezarządzanych klientów, uzyskaniu wskaźnik do obiektu, zależą od obiektu, aby pozostać w tej samej lokalizacji.</span><span class="sxs-lookup"><span data-stu-id="2e391-109">Unmanaged clients, having obtained a pointer to an object, rely on the object to remain at the same location.</span></span> <span data-ttu-id="2e391-110">Ci klienci mają żaden mechanizm służący do radzenia sobie z obiektem, którego lokalizacja nie zostanie usunięty.</span><span class="sxs-lookup"><span data-stu-id="2e391-110">These clients have no mechanism for dealing with an object whose location is not fixed.</span></span>  
  
 <span data-ttu-id="2e391-111">Aby wyeliminować te różnice, środowisko wykonawcze zapewnia klas otoki się klientów zarządzanych i niezarządzanych, wydaje się, że wywołania obiektów w ramach odpowiednio ich środowiska.</span><span class="sxs-lookup"><span data-stu-id="2e391-111">To overcome these differences, the runtime provides wrapper classes to make both managed and unmanaged clients think they are calling objects within their respective environment.</span></span> <span data-ttu-id="2e391-112">Zawsze, gdy zarządzanego klienta wywołuje metodę dla obiektów COM, środowisko uruchomieniowe tworzy [wywoływana otoka środowiska uruchomieniowego](runtime-callable-wrapper.md) (RCW).</span><span class="sxs-lookup"><span data-stu-id="2e391-112">Whenever your managed client calls a method on a COM object, the runtime creates a [runtime callable wrapper](runtime-callable-wrapper.md) (RCW).</span></span> <span data-ttu-id="2e391-113">RCW abstrakcyjna różnice między mechanizmów odwołania zarządzane i niezarządzane, między innymi.</span><span class="sxs-lookup"><span data-stu-id="2e391-113">RCWs abstract the differences between managed and unmanaged reference mechanisms, among other things.</span></span> <span data-ttu-id="2e391-114">Środowisko uruchomieniowe wzrasta, powstaje [wywoływana otoka COM](com-callable-wrapper.md) (CCW), aby cofnąć ten proces włączania klient modelu COM bezproblemowo wywołania metody wobec obiektu .NET.</span><span class="sxs-lookup"><span data-stu-id="2e391-114">The runtime also creates a [COM callable wrapper](com-callable-wrapper.md) (CCW) to reverse the process, enabling a COM client to seamlessly call a method on a .NET object.</span></span> <span data-ttu-id="2e391-115">Jak pokazano na poniższej ilustracji, perspektywy kod wywołujący Określa, która klasa otoki, środowisko uruchomieniowe tworzy.</span><span class="sxs-lookup"><span data-stu-id="2e391-115">As the following illustration shows, the perspective of the calling code determines which wrapper class the runtime creates.</span></span>  
  
 ![Przegląd otoki COM](./media/com-wrappers/bidirectional-com-overview.gif)  
  
 <span data-ttu-id="2e391-117">W większości przypadków standard RCW lub CCW generowane przez środowisko wykonawcze zapewnia odpowiednie kierowanie wywołań, które przekraczają granicę między COM i .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="2e391-117">In most cases, the standard RCW or CCW generated by the runtime provides adequate marshaling for calls that cross the boundary between COM and the .NET Framework.</span></span> <span data-ttu-id="2e391-118">Za pomocą atrybutów niestandardowych, można opcjonalnie dostosować sposób, środowisko uruchomieniowe reprezentuje kodem zarządzanym i niezarządzanym.</span><span class="sxs-lookup"><span data-stu-id="2e391-118">Using custom attributes, you can optionally adjust the way the runtime represents managed and unmanaged code.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2e391-119">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="2e391-119">See also</span></span>
- <span data-ttu-id="2e391-120">[Zaawansowane współdziałanie modeli COM](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bd9cdfyx(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="2e391-120">[Advanced COM Interoperability](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bd9cdfyx(v=vs.100))</span></span>
- [<span data-ttu-id="2e391-121">Wywoływana otoka środowiska uruchomieniowego</span><span class="sxs-lookup"><span data-stu-id="2e391-121">Runtime Callable Wrapper</span></span>](runtime-callable-wrapper.md)
- [<span data-ttu-id="2e391-122">Wywoływana otoka COM</span><span class="sxs-lookup"><span data-stu-id="2e391-122">COM Callable Wrapper</span></span>](com-callable-wrapper.md)
- <span data-ttu-id="2e391-123">[Dostosowywanie otok standardowych](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/h7hx9abd(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="2e391-123">[Customizing Standard Wrappers](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/h7hx9abd(v=vs.100))</span></span>
- <span data-ttu-id="2e391-124">[Instrukcje: Dostosowywanie wywoływanych otok środowiska uruchomieniowego](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/56kh4hy7(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="2e391-124">[How to: Customize Runtime Callable Wrappers](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/56kh4hy7(v=vs.100))</span></span>
