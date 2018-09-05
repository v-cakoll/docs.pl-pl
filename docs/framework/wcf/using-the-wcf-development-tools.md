---
title: Używanie narzędzi deweloperskich programu WCF
ms.date: 03/30/2017
ms.assetid: 054adb87-c244-4d5a-83d1-0b2b44bd454b
ms.openlocfilehash: 3eb349fd795b2067d4d75ff138fd9b5922110bd3
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/04/2018
ms.locfileid: "43674351"
---
# <a name="using-the-wcf-development-tools"></a><span data-ttu-id="48124-102">Używanie narzędzi deweloperskich programu WCF</span><span class="sxs-lookup"><span data-stu-id="48124-102">Using the WCF Development Tools</span></span>
<span data-ttu-id="48124-103">W tej sekcji opisano narzędzia programistyczne programu Visual Studio, które mogą pomóc w rozwoju Twojej WCFservice.</span><span class="sxs-lookup"><span data-stu-id="48124-103">This section describes the Visual Studio development tools that can assist you in developing your WCFservice.</span></span>  
  
 <span data-ttu-id="48124-104">Możesz szybko tworzyć własne usługi za pomocą szablonów programu Visual Studio jako podstawa, a następnie użyj hostów Auto usługi WCF i WCF przetestować klienta do debugowania i testowania usługi.</span><span class="sxs-lookup"><span data-stu-id="48124-104">You can use the Visual Studio templates as a foundation to quickly build your own service, then use WCF Service Auto Host and WCF Test Client to debug and test your service.</span></span> <span data-ttu-id="48124-105">Razem te narzędzia zapewniają szybkie i bezproblemowe debugowanie i cyklu testowania i wyklucza trzeba przekazać do modelu hostowania na wczesnym etapie.</span><span class="sxs-lookup"><span data-stu-id="48124-105">These tools together provide a fast and seamless debug and testing cycle, and preclude the need to commit to a hosting model at an early stage.</span></span>  
  
## <a name="the-wcf-developer-tools"></a><span data-ttu-id="48124-106">Narzędzi deweloperskich programu WCF</span><span class="sxs-lookup"><span data-stu-id="48124-106">The WCF Developer Tools</span></span>  
 [<span data-ttu-id="48124-107">Szablony programu Visual Studio na potrzeby programu WCF</span><span class="sxs-lookup"><span data-stu-id="48124-107">WCF Visual Studio Templates</span></span>](../../../docs/framework/wcf/wcf-vs-templates.md)  
  
 <span data-ttu-id="48124-108">Wstępnie zdefiniowane szablony projektów i elementów programu Visual Studio w programie Visual Studio umożliwia szybkie tworzenie usług WCF i otaczającego aplikacji.</span><span class="sxs-lookup"><span data-stu-id="48124-108">You can use the predefined Visual Studio project and item templates in Visual Studio to quickly build WCF services and surrounding applications.</span></span>  
  
 [<span data-ttu-id="48124-109">Host usługi WCF (WcfSvcHost.exe)</span><span class="sxs-lookup"><span data-stu-id="48124-109">WCF Service Host (WcfSvcHost.exe)</span></span>](../../../docs/framework/wcf/wcf-service-host-wcfsvchost-exe.md)  
  
 <span data-ttu-id="48124-110">Host automatycznie usługi WCF (WcfSvcHost.exe) można uruchomić debugera programu Visual Studio (F5), aby automatycznie obsługiwać i przetestować usługę, w których zaimplementowano.</span><span class="sxs-lookup"><span data-stu-id="48124-110">The WCF Service Auto Host (WcfSvcHost.exe) allows you to launch the Visual Studio debugger (F5) to automatically host and test a service you have implemented.</span></span> <span data-ttu-id="48124-111">Następnie można testować usługę za pomocą testu klient WCF (wcfTestClient.exe) lub własnego klienta można znaleźć i naprawić wszelkie potencjalne błędy.</span><span class="sxs-lookup"><span data-stu-id="48124-111">You can then test the service using the WCF Test Client (wcfTestClient.exe) or your own client to find and fix any potential errors.</span></span>  
  
 [<span data-ttu-id="48124-112">Testowy klient WCF (WcfTestClient.exe)</span><span class="sxs-lookup"><span data-stu-id="48124-112">WCF Test Client (WcfTestClient.exe)</span></span>](../../../docs/framework/wcf/wcf-test-client-wcftestclient-exe.md)  
  
 <span data-ttu-id="48124-113">Testowy klient WCF (WcfTestClient.exe) jest narzędziem graficznego interfejsu użytkownika, które pozwala na arbitralnie wybrane typy parametrów wejściowych, przesyłanie te dane wejściowe do usługi i widok, który odsyła odpowiedź usługi.</span><span class="sxs-lookup"><span data-stu-id="48124-113">WCF Test Client (WcfTestClient.exe) is a GUI tool that allows you to input parameters of arbitrary types, submit that input to the service, and view the response the service sends back.</span></span> <span data-ttu-id="48124-114">Zapewnia bezproblemowe usługi testowania doświadczenie w połączeniu z hostów Auto usługi WCF.</span><span class="sxs-lookup"><span data-stu-id="48124-114">It provides a seamless service testing experience when combined with WCF Service Auto Host.</span></span>  
  
 [<span data-ttu-id="48124-115">Generowanie klas typów danych z kodu XML</span><span class="sxs-lookup"><span data-stu-id="48124-115">Generating Data Type Classes from XML</span></span>](../../../docs/framework/wcf/generating-data-type-classes-from-xml.md)  
  
 <span data-ttu-id="48124-116">XML — dane przechowywane w Schowku można wkleić do strony kodowej.</span><span class="sxs-lookup"><span data-stu-id="48124-116">XML data stored in the clipboard can be pasted into a code page.</span></span> <span data-ttu-id="48124-117">Klas zdefiniowanych w danych zostaną przekonwertowane na typy kodu.</span><span class="sxs-lookup"><span data-stu-id="48124-117">The classes defined in the data will be converted to code types.</span></span>  
  
## <a name="using-the-tools-without-administrator-privilege"></a><span data-ttu-id="48124-118">Za pomocą narzędzi bez uprawnień administratora</span><span class="sxs-lookup"><span data-stu-id="48124-118">Using the Tools without Administrator privilege</span></span>  
 <span data-ttu-id="48124-119">Aby umożliwić użytkownikom bez uprawnień administratora do tworzenia usług WCF, (listę kontroli dostępu) jest tworzony dla przestrzeni nazw "http://+:8731/Design_Time_Addresses" podczas instalacji programu Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="48124-119">To enable users without administrator privilege to develop WCF services, an ACL (Access Control List) is created for the namespace "http://+:8731/Design_Time_Addresses" during the installation of Visual Studio.</span></span> <span data-ttu-id="48124-120">Lista ACL jest równa (UI), która obejmuje wszystkie interaktywne użytkownicy zalogowani na maszynie.</span><span class="sxs-lookup"><span data-stu-id="48124-120">The ACL is set to (UI), which includes all interactive users logged on to the machine.</span></span> <span data-ttu-id="48124-121">Administratorzy mogą dodawać lub usuwać użytkowników z tej listy ACL lub otwarcie dodatkowych portów. Ta lista ACL umożliwia WCF lub WF szablonów do wysyłania i odbierania danych w konfiguracji domyślnej.</span><span class="sxs-lookup"><span data-stu-id="48124-121">Administrators can add or remove users from this ACL, or open additional ports.This ACL enables WCF or WF templates to send and receive data in their default configuration.</span></span> <span data-ttu-id="48124-122">Umożliwia również użytkownikom używanie Host automatycznie usługi WCF (wcfSvcHost.exe) bez nadawania im uprawnień administratora.</span><span class="sxs-lookup"><span data-stu-id="48124-122">It also enables users to use the WCF Service Auto Host (wcfSvcHost.exe) without granting them administrator privileges.</span></span>  
  
 <span data-ttu-id="48124-123">Możesz zmodyfikować dostępu przy użyciu narzędzia Netsh.exe w [!INCLUDE[wv](../../../includes/wv-md.md)] przy użyciu konta administratora z podniesionymi uprawnieniami.</span><span class="sxs-lookup"><span data-stu-id="48124-123">You can modify access using the Netsh.exe tool in [!INCLUDE[wv](../../../includes/wv-md.md)] under the elevated administrator account.</span></span> <span data-ttu-id="48124-124">Oto przykład użycia Netsh.exe.</span><span class="sxs-lookup"><span data-stu-id="48124-124">The following is an example of using Netsh.exe.</span></span>  
  
```  
netsh http add urlacl url=http://+:8001/MyService user=<domain>\<user>  
```  
  
 <span data-ttu-id="48124-125">Aby uzyskać więcej informacji na temat Netsh.exe zobacz [sposób użycia narzędzia Netsh.exe i przełączniki wiersza polecenia](https://go.microsoft.com/fwlink/?LinkId=97877).</span><span class="sxs-lookup"><span data-stu-id="48124-125">For more information about Netsh.exe, see [How to Use the Netsh.exe Tool and Command-Line Switches](https://go.microsoft.com/fwlink/?LinkId=97877).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="48124-126">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="48124-126">See Also</span></span>  
 [<span data-ttu-id="48124-127">Szablony programu Visual Studio na potrzeby programu WCF</span><span class="sxs-lookup"><span data-stu-id="48124-127">WCF Visual Studio Templates</span></span>](../../../docs/framework/wcf/wcf-vs-templates.md)  
 [<span data-ttu-id="48124-128">Host usługi WCF (WcfSvcHost.exe)</span><span class="sxs-lookup"><span data-stu-id="48124-128">WCF Service Host (WcfSvcHost.exe)</span></span>](../../../docs/framework/wcf/wcf-service-host-wcfsvchost-exe.md)  
 [<span data-ttu-id="48124-129">Testowy klient WCF (WcfTestClient.exe)</span><span class="sxs-lookup"><span data-stu-id="48124-129">WCF Test Client (WcfTestClient.exe)</span></span>](../../../docs/framework/wcf/wcf-test-client-wcftestclient-exe.md)
