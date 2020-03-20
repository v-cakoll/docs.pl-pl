---
title: Używanie narzędzi deweloperskich programu WCF
ms.date: 03/30/2017
ms.assetid: 054adb87-c244-4d5a-83d1-0b2b44bd454b
ms.openlocfilehash: 82bb7e225492bcdba4d2e611de405a09571355c0
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79183082"
---
# <a name="using-the-wcf-development-tools"></a><span data-ttu-id="e1dbe-102">Używanie narzędzi deweloperskich programu WCF</span><span class="sxs-lookup"><span data-stu-id="e1dbe-102">Using the WCF Development Tools</span></span>
<span data-ttu-id="e1dbe-103">W tej sekcji opisano narzędzia programistyczne programu Visual Studio, które mogą pomóc w tworzeniu usługi WCFservice.</span><span class="sxs-lookup"><span data-stu-id="e1dbe-103">This section describes the Visual Studio development tools that can assist you in developing your WCFservice.</span></span>  
  
 <span data-ttu-id="e1dbe-104">Szablony programu Visual Studio można użyć jako podstawa do szybkiego tworzenia własnej usługi, a następnie użyć WCF Service Auto Host i WCF Test Client do debugowania i testowania usługi.</span><span class="sxs-lookup"><span data-stu-id="e1dbe-104">You can use the Visual Studio templates as a foundation to quickly build your own service, then use WCF Service Auto Host and WCF Test Client to debug and test your service.</span></span> <span data-ttu-id="e1dbe-105">Te narzędzia razem zapewniają szybki i bezproblemowy cykl debugowania i testowania i wykluczają konieczność zatwierdzania modelu hostingu na wczesnym etapie.</span><span class="sxs-lookup"><span data-stu-id="e1dbe-105">These tools together provide a fast and seamless debug and testing cycle, and preclude the need to commit to a hosting model at an early stage.</span></span>  

 > [!NOTE]
 > <span data-ttu-id="e1dbe-106">Począwszy od programu Visual Studio 2017 narzędzia programistyczne WCF nie są instalowane domyślnie.</span><span class="sxs-lookup"><span data-stu-id="e1dbe-106">Starting with Visual Studio 2017, the WCF development tools are not installed by default.</span></span> <span data-ttu-id="e1dbe-107">Aby korzystać z tych funkcji, należy upewnić się, że składnik Programu Windows Communication Foundation jest wybrany w instalatorze programu Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="e1dbe-107">In order to use these features, you must ensure the Windows Communication Foundation component is selected in the Visual Studio installer.</span></span>
  
## <a name="the-wcf-developer-tools"></a><span data-ttu-id="e1dbe-108">Narzędzia programistyczne WCF</span><span class="sxs-lookup"><span data-stu-id="e1dbe-108">The WCF Developer Tools</span></span>  
 [<span data-ttu-id="e1dbe-109">Szablony programu Visual Studio na potrzeby programu WCF</span><span class="sxs-lookup"><span data-stu-id="e1dbe-109">WCF Visual Studio Templates</span></span>](wcf-vs-templates.md)  
  
 <span data-ttu-id="e1dbe-110">Można użyć wstępnie zdefiniowanych szablonów projektu i elementów programu Visual Studio w programie Visual Studio, aby szybko utworzyć usługi WCF i otaczające aplikacje.</span><span class="sxs-lookup"><span data-stu-id="e1dbe-110">You can use the predefined Visual Studio project and item templates in Visual Studio to quickly build WCF services and surrounding applications.</span></span>  
  
 [<span data-ttu-id="e1dbe-111">Host usługi WCF (WcfSvcHost.exe)</span><span class="sxs-lookup"><span data-stu-id="e1dbe-111">WCF Service Host (WcfSvcHost.exe)</span></span>](wcf-service-host-wcfsvchost-exe.md)  
  
 <span data-ttu-id="e1dbe-112">WCF Service Auto Host (WcfSvcHost.exe) umożliwia uruchomienie debugera programu Visual Studio (F5), aby automatycznie hostować i testować zaimplementowana usługa.</span><span class="sxs-lookup"><span data-stu-id="e1dbe-112">The WCF Service Auto Host (WcfSvcHost.exe) allows you to launch the Visual Studio debugger (F5) to automatically host and test a service you have implemented.</span></span> <span data-ttu-id="e1dbe-113">Następnie można przetestować usługę przy użyciu klienta testowego WCF (wcfTestClient.exe) lub własnego klienta, aby znaleźć i naprawić wszelkie potencjalne błędy.</span><span class="sxs-lookup"><span data-stu-id="e1dbe-113">You can then test the service using the WCF Test Client (wcfTestClient.exe) or your own client to find and fix any potential errors.</span></span>  
  
 [<span data-ttu-id="e1dbe-114">Testowy klient WCF (WcfTestClient.exe)</span><span class="sxs-lookup"><span data-stu-id="e1dbe-114">WCF Test Client (WcfTestClient.exe)</span></span>](wcf-test-client-wcftestclient-exe.md)  
  
 <span data-ttu-id="e1dbe-115">WCF Test Client (WcfTestClient.exe) to narzędzie GUI, które umożliwia wprowadzanie parametrów dowolnego typu, przesyłanie tego danych wejściowych do usługi i wyświetlanie odpowiedzi, którą usługa wysyła z powrotem.</span><span class="sxs-lookup"><span data-stu-id="e1dbe-115">WCF Test Client (WcfTestClient.exe) is a GUI tool that allows you to input parameters of arbitrary types, submit that input to the service, and view the response the service sends back.</span></span> <span data-ttu-id="e1dbe-116">Zapewnia bezproblemowe testowanie usług w połączeniu z auto hostem usługi WCF.</span><span class="sxs-lookup"><span data-stu-id="e1dbe-116">It provides a seamless service testing experience when combined with WCF Service Auto Host.</span></span>  
  
 [<span data-ttu-id="e1dbe-117">Generowanie klas typów danych z kodu XML</span><span class="sxs-lookup"><span data-stu-id="e1dbe-117">Generating Data Type Classes from XML</span></span>](generating-data-type-classes-from-xml.md)  
  
 <span data-ttu-id="e1dbe-118">Dane XML przechowywane w schowku można wkleić na stronę kodową.</span><span class="sxs-lookup"><span data-stu-id="e1dbe-118">XML data stored in the clipboard can be pasted into a code page.</span></span> <span data-ttu-id="e1dbe-119">Klasy zdefiniowane w danych zostaną przekonwertowane na typy kodu.</span><span class="sxs-lookup"><span data-stu-id="e1dbe-119">The classes defined in the data will be converted to code types.</span></span>  
  
## <a name="using-the-tools-without-administrator-privilege"></a><span data-ttu-id="e1dbe-120">Korzystanie z narzędzi bez uprawnień administratora</span><span class="sxs-lookup"><span data-stu-id="e1dbe-120">Using the Tools without Administrator privilege</span></span>  
 <span data-ttu-id="e1dbe-121">Aby umożliwić użytkownikom bez uprawnień administratora tworzenie usług WCF, acl (Listahttp://+:8731/Design_Time_Addresseskontroli dostępu) jest tworzony dla obszaru nazw " " " podczas instalacji programu Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="e1dbe-121">To enable users without administrator privilege to develop WCF services, an ACL (Access Control List) is created for the namespace "http://+:8731/Design_Time_Addresses" during the installation of Visual Studio.</span></span> <span data-ttu-id="e1dbe-122">Listy ACL jest ustawiona na (UI), który obejmuje wszystkich użytkowników interaktywnych zalogowanych do komputera.</span><span class="sxs-lookup"><span data-stu-id="e1dbe-122">The ACL is set to (UI), which includes all interactive users logged on to the machine.</span></span> <span data-ttu-id="e1dbe-123">Administratorzy mogą dodawać lub usuwać użytkowników z tej listy ACL lub otwierać dodatkowe porty. Ta acl umożliwia WCF lub WF szablonów do wysyłania i odbierania danych w konfiguracji domyślnej.</span><span class="sxs-lookup"><span data-stu-id="e1dbe-123">Administrators can add or remove users from this ACL, or open additional ports.This ACL enables WCF or WF templates to send and receive data in their default configuration.</span></span> <span data-ttu-id="e1dbe-124">Umożliwia również użytkownikom korzystanie z automatycznego hosta usługi WCF (wcfSvcHost.exe) bez przyznania im uprawnień administratora.</span><span class="sxs-lookup"><span data-stu-id="e1dbe-124">It also enables users to use the WCF Service Auto Host (wcfSvcHost.exe) without granting them administrator privileges.</span></span>  
  
 <span data-ttu-id="e1dbe-125">Dostęp można modyfikować za pomocą narzędzia Netsh.exe w systemie Windows Vista w obszarze podwyższonego poziomu konta administratora.</span><span class="sxs-lookup"><span data-stu-id="e1dbe-125">You can modify access using the Netsh.exe tool in Windows Vista under the elevated administrator account.</span></span> <span data-ttu-id="e1dbe-126">Poniżej przedstawiono przykład użycia programu Netsh.exe.</span><span class="sxs-lookup"><span data-stu-id="e1dbe-126">The following is an example of using Netsh.exe.</span></span>  
  
```console  
netsh http add urlacl url=http://+:8001/MyService user=<domain>\<user>  
```  
  
 <span data-ttu-id="e1dbe-127">Aby uzyskać więcej informacji na temat programu Netsh.exe, zobacz [Jak korzystać z przełączników narzędzia Netsh.exe i wiersza polecenia](https://docs.microsoft.com/previous-versions/tn-archive/bb490939(v=technet.10)).</span><span class="sxs-lookup"><span data-stu-id="e1dbe-127">For more information about Netsh.exe, see [How to Use the Netsh.exe Tool and Command-Line Switches](https://docs.microsoft.com/previous-versions/tn-archive/bb490939(v=technet.10)).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e1dbe-128">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="e1dbe-128">See also</span></span>

- [<span data-ttu-id="e1dbe-129">Szablony programu Visual Studio na potrzeby programu WCF</span><span class="sxs-lookup"><span data-stu-id="e1dbe-129">WCF Visual Studio Templates</span></span>](wcf-vs-templates.md)
- [<span data-ttu-id="e1dbe-130">Host usługi WCF (WcfSvcHost.exe)</span><span class="sxs-lookup"><span data-stu-id="e1dbe-130">WCF Service Host (WcfSvcHost.exe)</span></span>](wcf-service-host-wcfsvchost-exe.md)
- [<span data-ttu-id="e1dbe-131">Testowy klient WCF (WcfTestClient.exe)</span><span class="sxs-lookup"><span data-stu-id="e1dbe-131">WCF Test Client (WcfTestClient.exe)</span></span>](wcf-test-client-wcftestclient-exe.md)
