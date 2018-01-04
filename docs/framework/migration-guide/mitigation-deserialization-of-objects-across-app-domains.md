---
title: "Ograniczenie: Deserializacja obiektów między domenami aplikacji"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 30c2d66c-04a8-41a5-ad31-646b937f61b5
caps.latest.revision: "5"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: fa156c914d2a1bb2ff0601d9e06c9b87d4190754
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="mitigation-deserialization-of-objects-across-app-domains"></a><span data-ttu-id="f9ebb-102">Ograniczenie: Deserializacja obiektów między domenami aplikacji</span><span class="sxs-lookup"><span data-stu-id="f9ebb-102">Mitigation: Deserialization of Objects Across App Domains</span></span>
<span data-ttu-id="f9ebb-103">W niektórych przypadkach, gdy aplikacja używa dwóch lub większej liczby domen aplikacji z różnymi bazami aplikacji, próba deserializacji obiektów w logicznym kontekście wywołań między różnymi domenami aplikacji zgłasza wyjątek.</span><span class="sxs-lookup"><span data-stu-id="f9ebb-103">In some cases, when an app uses two or more app domains with different application bases, the attempt to deserialize objects in the logical call context across app domains throws an exception.</span></span>  
  
## <a name="diagnosing-the-issue"></a><span data-ttu-id="f9ebb-104">Diagnozowanie problemu</span><span class="sxs-lookup"><span data-stu-id="f9ebb-104">Diagnosing the issue</span></span>  
 <span data-ttu-id="f9ebb-105">Problem pojawia się w obszarze następującej sekwencji warunków:</span><span class="sxs-lookup"><span data-stu-id="f9ebb-105">The issue arises under the following sequence of conditions:</span></span>  
  
1.  <span data-ttu-id="f9ebb-106">Aplikacja używa dwóch lub większej liczby domen aplikacji z różnymi bazami aplikacji.</span><span class="sxs-lookup"><span data-stu-id="f9ebb-106">An app uses two or more app domains with different application bases.</span></span>  
  
2.  <span data-ttu-id="f9ebb-107">Niektóre typy są jawnie dodawane do <xref:System.Runtime.Remoting.Messaging.LogicalCallContext> przez wywołanie metody takiej jak <xref:System.Runtime.Remoting.Messaging.LogicalCallContext.SetData%2A?displayProperty=nameWithType> lub <xref:System.Runtime.Remoting.Messaging.CallContext.LogicalSetData%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="f9ebb-107">Some types are explicitly added to the <xref:System.Runtime.Remoting.Messaging.LogicalCallContext> by calling a method such as <xref:System.Runtime.Remoting.Messaging.LogicalCallContext.SetData%2A?displayProperty=nameWithType> or <xref:System.Runtime.Remoting.Messaging.CallContext.LogicalSetData%2A?displayProperty=nameWithType>.</span></span> <span data-ttu-id="f9ebb-108">Te typu nie są oznaczane jako możliwe do serializacji i nie są przechowywane w globalnej pamięci podręcznej zestawów.</span><span class="sxs-lookup"><span data-stu-id="f9ebb-108">These types are not marked as serializable and are not stored in the global assembly cache.</span></span>  
  
3.  <span data-ttu-id="f9ebb-109">Później, kod uruchomiony w domenie aplikacji innej niż domyślna próbuje odczytać wartość z pliku konfiguracji lub zdeserializować obiekt za pomocą XML.</span><span class="sxs-lookup"><span data-stu-id="f9ebb-109">Later, code running in the non-default app domain tries to read a value from a configuration file or use XML to deserialize an object.</span></span>  
  
4.  <span data-ttu-id="f9ebb-110">Aby czytać z pliku konfiguracji lub deserializować obiekt, obiekt <xref:System.Xml.XmlReader> próbuje uzyskać dostęp do systemu konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="f9ebb-110">In order to read from a configuration file or deserialize the object, an <xref:System.Xml.XmlReader> object tries to access the configuration system.</span></span>  
  
5.  <span data-ttu-id="f9ebb-111">Jeśli system konfiguracji nie został jeszcze zainicjowany, musi on zakończyć proces inicjacji.</span><span class="sxs-lookup"><span data-stu-id="f9ebb-111">If the configuration system has not already been initialized, it must complete its initialization.</span></span> <span data-ttu-id="f9ebb-112">Oznacza to, między innymi, że środowisko wykonawcze musi utworzyć stabilną ścieżkę dla systemu konfiguracji, co wykonuje w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="f9ebb-112">This means, among other things, that the runtime has to create a stable path for a configuration system, which it does as follows:</span></span>  
  
    1.  <span data-ttu-id="f9ebb-113">Szuka dowodu dla domeny aplikacji innej niż domyślna.</span><span class="sxs-lookup"><span data-stu-id="f9ebb-113">It looks for evidence for the non-default app domain.</span></span>  
  
    2.  <span data-ttu-id="f9ebb-114">Próbuje obliczyć dowód dla domeny aplikacji innej niż domyślna na podstawie domyślnej domeny aplikacji.</span><span class="sxs-lookup"><span data-stu-id="f9ebb-114">It tries to calculate the evidence for the non-default app domain based on the default app domain.</span></span>  
  
    3.  <span data-ttu-id="f9ebb-115">Wywołanie w celu uzyskania dowodu dla domyślnej domeny aplikacji wyzwala międzyaplikacyjne wywołanie domeny z domeny aplikacji innej niż domyślna do domyślnej domeny aplikacji.</span><span class="sxs-lookup"><span data-stu-id="f9ebb-115">The call to get evidence for the default app domain triggers a cross-app domain call from the non-default app domain to the default app domain.</span></span>  
  
    4.  <span data-ttu-id="f9ebb-116">Zgodnie z częścią kontraktu domeny międzyaplikacyjnej w .NET Framework, zawartość logicznego kontekstu wywołań musiała być skierowana poza granice domeny aplikacji.</span><span class="sxs-lookup"><span data-stu-id="f9ebb-116">As part of the cross-app domain contract in the .NET Framework, the contents of the logical call context also have to be marshaled across app domain boundaries.</span></span>  
  
6.  <span data-ttu-id="f9ebb-117">Ponieważ typy znajdujące się w logicznym kontekście wywołań nie mogą być rozpoznane w domyślnej domenie aplikacji, zgłaszany jest wyjątek.</span><span class="sxs-lookup"><span data-stu-id="f9ebb-117">Because the types that are in the logical call context cannot be resolved in the default app domain, an exception is thrown.</span></span>  
  
## <a name="mitigation"></a><span data-ttu-id="f9ebb-118">Ograniczenie</span><span class="sxs-lookup"><span data-stu-id="f9ebb-118">Mitigation</span></span>  
 <span data-ttu-id="f9ebb-119">Aby obejść ten problem, należy wykonać następujące czynności</span><span class="sxs-lookup"><span data-stu-id="f9ebb-119">To work around this issue, do the following</span></span>  
  
1.  <span data-ttu-id="f9ebb-120">Poszukaj wywołania `get_Evidence` w stosie wywołań gdy wyjątek jest zgłaszany.</span><span class="sxs-lookup"><span data-stu-id="f9ebb-120">Look for the call to `get_Evidence` in the call stack when the exception is thrown.</span></span> <span data-ttu-id="f9ebb-121">Może to być dowolny wyjątek z dużego podzbioru wyjątków, łącznie z <xref:System.IO.FileNotFoundException> i <xref:System.Runtime.Serialization.SerializationException>.</span><span class="sxs-lookup"><span data-stu-id="f9ebb-121">The exception can be any of a large subset of exceptions, including <xref:System.IO.FileNotFoundException> and <xref:System.Runtime.Serialization.SerializationException>.</span></span>  
  
2.  <span data-ttu-id="f9ebb-122">Następnie należy znaleźć miejsce w aplikacji, gdzie żadne obiekty nie są dodawane do kontekstu wywołania logicznego i dodać następujący kod:</span><span class="sxs-lookup"><span data-stu-id="f9ebb-122">Identify the place in the app where no objects are added to the logical call context and add the following code:</span></span>  
  
    ```  
    System.Configuration.ConfigurationManager.GetSection("system.xml/xmlReader");  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="f9ebb-123">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="f9ebb-123">See Also</span></span>  
 [<span data-ttu-id="f9ebb-124">Zmiany środowiska uruchomieniowego</span><span class="sxs-lookup"><span data-stu-id="f9ebb-124">Runtime Changes</span></span>](../../../docs/framework/migration-guide/runtime-changes-in-the-net-framework-4-5-1.md)
