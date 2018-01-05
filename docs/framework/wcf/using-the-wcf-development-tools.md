---
title: "Używanie narzędzi deweloperskich programu WCF"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 054adb87-c244-4d5a-83d1-0b2b44bd454b
caps.latest.revision: "15"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 7d253f38fab21496dd305cc67e7b6e84846579f3
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="using-the-wcf-development-tools"></a><span data-ttu-id="d7740-102">Używanie narzędzi deweloperskich programu WCF</span><span class="sxs-lookup"><span data-stu-id="d7740-102">Using the WCF Development Tools</span></span>
<span data-ttu-id="d7740-103">W tej sekcji opisano [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] [!INCLUDE[indigo1](../../../includes/indigo1-md.md)] narzędzi programistycznych, które mogą pomóc w tworzeniu sieci [!INCLUDE[indigo2](../../../includes/indigo2-md.md)]usługi.</span><span class="sxs-lookup"><span data-stu-id="d7740-103">This section describes the [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)][!INCLUDE[indigo1](../../../includes/indigo1-md.md)] development tools that can assist you in developing your [!INCLUDE[indigo2](../../../includes/indigo2-md.md)]service.</span></span>  
  
 <span data-ttu-id="d7740-104">Można użyć [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] następnie użyć szablonów jako podstawę do szybko tworzyć własne usługi [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] hosta usługi automatycznie i [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] testowanie klienta do debugowania i testowania usługi.</span><span class="sxs-lookup"><span data-stu-id="d7740-104">You can use the [!INCLUDE[indigo2](../../../includes/indigo2-md.md)][!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] templates as a foundation to quickly build your own service, then use [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] Service Auto Host and [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] Test Client to debug and test your service.</span></span> <span data-ttu-id="d7740-105">Te narzędzia razem Podaj szybkiego i łatwego debugowania i testowania cyklu i wyklucza trzeba przekazać do obsługi modelu na wczesnym etapie.</span><span class="sxs-lookup"><span data-stu-id="d7740-105">These tools together provide a fast and seamless debug and testing cycle, and preclude the need to commit to a hosting model at an early stage.</span></span>  
  
## <a name="the-wcf-developer-tools"></a><span data-ttu-id="d7740-106">Narzędzia deweloperskie programu WCF</span><span class="sxs-lookup"><span data-stu-id="d7740-106">The WCF Developer Tools</span></span>  
 [<span data-ttu-id="d7740-107">Szablony programu Visual Studio na potrzeby programu WCF</span><span class="sxs-lookup"><span data-stu-id="d7740-107">WCF Visual Studio Templates</span></span>](../../../docs/framework/wcf/wcf-vs-templates.md)  
  
 <span data-ttu-id="d7740-108">Można użyć wstępnie zdefiniowane [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] szablonów projektów i elementów w [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] można szybko utworzyć [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] usługi i aplikacje otaczającego.</span><span class="sxs-lookup"><span data-stu-id="d7740-108">You can use the predefined [!INCLUDE[indigo2](../../../includes/indigo2-md.md)][!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] project and item templates in [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] to quickly build [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] services and surrounding applications.</span></span>  
  
 [<span data-ttu-id="d7740-109">Host usługi WCF (WcfSvcHost.exe)</span><span class="sxs-lookup"><span data-stu-id="d7740-109">WCF Service Host (WcfSvcHost.exe)</span></span>](../../../docs/framework/wcf/wcf-service-host-wcfsvchost-exe.md)  
  
 <span data-ttu-id="d7740-110">[!INCLUDE[indigo2](../../../includes/indigo2-md.md)] Hosta usługi automatycznie (WcfSvcHost.exe) pozwala na uruchamianie [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] debugera (F5), aby automatycznie udostępniać i testowanie usługi zostały zaimplementowane.</span><span class="sxs-lookup"><span data-stu-id="d7740-110">The [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] Service Auto Host (WcfSvcHost.exe) allows you to launch the [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] debugger (F5) to automatically host and test a service you have implemented.</span></span> <span data-ttu-id="d7740-111">Następnie można testować przy użyciu usługi [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] testowanie klienta (wcfTestClient.exe) lub własnego klienta, aby znaleźć i rozwiązać wszelkie potencjalne błędy.</span><span class="sxs-lookup"><span data-stu-id="d7740-111">You can then test the service using the [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] Test Client (wcfTestClient.exe) or your own client to find and fix any potential errors.</span></span>  
  
 [<span data-ttu-id="d7740-112">Testowy klient WCF (WcfTestClient.exe)</span><span class="sxs-lookup"><span data-stu-id="d7740-112">WCF Test Client (WcfTestClient.exe)</span></span>](../../../docs/framework/wcf/wcf-test-client-wcftestclient-exe.md)  
  
 [!INCLUDE[indigo2](../../../includes/indigo2-md.md)]<span data-ttu-id="d7740-113">Klient testowy (WcfTestClient.exe) to narzędzie graficznego interfejsu użytkownika, które można wprowadzić parametry dowolnego typu, że dane wejściowe do usługi i widoku, który odsyła odpowiedź usługi przesyłania.</span><span class="sxs-lookup"><span data-stu-id="d7740-113"> Test Client (WcfTestClient.exe) is a GUI tool that allows you to input parameters of arbitrary types, submit that input to the service, and view the response the service sends back.</span></span> <span data-ttu-id="d7740-114">Zapewnia bezproblemowe usługi testowania czynności w połączeniu z [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] hosta usługi automatycznie.</span><span class="sxs-lookup"><span data-stu-id="d7740-114">It provides a seamless service testing experience when combined with [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] Service Auto Host.</span></span>  
  
 [<span data-ttu-id="d7740-115">Generowanie klas typów danych z kodu XML</span><span class="sxs-lookup"><span data-stu-id="d7740-115">Generating Data Type Classes from XML</span></span>](../../../docs/framework/wcf/generating-data-type-classes-from-xml.md)  
  
 <span data-ttu-id="d7740-116">Dane XML przechowywane w Schowku można wkleić do strony kodowej.</span><span class="sxs-lookup"><span data-stu-id="d7740-116">XML data stored in the clipboard can be pasted into a code page.</span></span> <span data-ttu-id="d7740-117">Klas zdefiniowanych w danych zostanie przekonwertowany na typy kodu.</span><span class="sxs-lookup"><span data-stu-id="d7740-117">The classes defined in the data will be converted to code types.</span></span>  
  
## <a name="using-the-tools-without-administrator-privilege"></a><span data-ttu-id="d7740-118">Za pomocą narzędzi bez uprawnień administratora</span><span class="sxs-lookup"><span data-stu-id="d7740-118">Using the Tools without Administrator privilege</span></span>  
 <span data-ttu-id="d7740-119">Aby umożliwić użytkownikom bez uprawnień administratora do opracowywania [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] usług, list kontroli dostępu (listy kontroli dostępu) jest tworzona podczas instalacji dla przestrzeni nazw "http://+:8731/Design_Time_Addresses" [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)].</span><span class="sxs-lookup"><span data-stu-id="d7740-119">To enable users without administrator privilege to develop [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] services, an ACL (Access Control List) is created for the namespace "http://+:8731/Design_Time_Addresses" during the installation of [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)].</span></span> <span data-ttu-id="d7740-120">Listy ACL ustawiono (UI), która obejmuje wszystkie interaktywne użytkownicy zalogowani do komputera.</span><span class="sxs-lookup"><span data-stu-id="d7740-120">The ACL is set to (UI), which includes all interactive users logged on to the machine.</span></span> <span data-ttu-id="d7740-121">Administratorzy mogą dodawać lub usuwać użytkowników z tej listy ACL lub Otwórz dodatkowych portów. Tej listy ACL umożliwia WCF i WF szablony do wysyłania i odbierania danych w domyślnej konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="d7740-121">Administrators can add or remove users from this ACL, or open additional ports.This ACL enables WCF or WF templates to send and receive data in their default configuration.</span></span> <span data-ttu-id="d7740-122">Umożliwia również użytkownikom używanie [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] automatycznie hosta usługi (wcfSvcHost.exe) bez przyznania im uprawnień administratora.</span><span class="sxs-lookup"><span data-stu-id="d7740-122">It also enables users to use the [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] Service Auto Host (wcfSvcHost.exe) without granting them administrator privileges.</span></span>  
  
 <span data-ttu-id="d7740-123">Można zmodyfikować dostępu za pomocą narzędzia Netsh.exe w [!INCLUDE[wv](../../../includes/wv-md.md)] przy użyciu konta administratora z podniesionymi uprawnieniami.</span><span class="sxs-lookup"><span data-stu-id="d7740-123">You can modify access using the Netsh.exe tool in [!INCLUDE[wv](../../../includes/wv-md.md)] under the elevated administrator account.</span></span> <span data-ttu-id="d7740-124">Oto przykład użycia Netsh.exe.</span><span class="sxs-lookup"><span data-stu-id="d7740-124">The following is an example of using Netsh.exe.</span></span>  
  
```  
netsh http add urlacl url=http://+:8001/MyService user=<domain>\<user>  
```  
  
 [!INCLUDE[crabout](../../../includes/crabout-md.md)]<span data-ttu-id="d7740-125">Netsh.exe, zobacz [jak używać narzędzia Netsh.exe i przełączniki wiersza polecenia](http://go.microsoft.com/fwlink/?LinkId=97877).</span><span class="sxs-lookup"><span data-stu-id="d7740-125"> Netsh.exe, see [How to Use the Netsh.exe Tool and Command-Line Switches](http://go.microsoft.com/fwlink/?LinkId=97877).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d7740-126">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="d7740-126">See Also</span></span>  
 [<span data-ttu-id="d7740-127">Szablony programu Visual Studio na potrzeby programu WCF</span><span class="sxs-lookup"><span data-stu-id="d7740-127">WCF Visual Studio Templates</span></span>](../../../docs/framework/wcf/wcf-vs-templates.md)  
 [<span data-ttu-id="d7740-128">Host usługi WCF (WcfSvcHost.exe)</span><span class="sxs-lookup"><span data-stu-id="d7740-128">WCF Service Host (WcfSvcHost.exe)</span></span>](../../../docs/framework/wcf/wcf-service-host-wcfsvchost-exe.md)  
 [<span data-ttu-id="d7740-129">Testowy klient WCF (WcfTestClient.exe)</span><span class="sxs-lookup"><span data-stu-id="d7740-129">WCF Test Client (WcfTestClient.exe)</span></span>](../../../docs/framework/wcf/wcf-test-client-wcftestclient-exe.md)
