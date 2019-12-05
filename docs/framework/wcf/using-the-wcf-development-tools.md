---
title: Używanie narzędzi deweloperskich programu WCF
ms.date: 03/30/2017
ms.assetid: 054adb87-c244-4d5a-83d1-0b2b44bd454b
ms.openlocfilehash: 59913f4c00c32699d788e2a0244798fc652361be
ms.sourcegitcommit: 32a575bf4adccc901f00e264f92b759ced633379
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/04/2019
ms.locfileid: "74802417"
---
# <a name="using-the-wcf-development-tools"></a><span data-ttu-id="87198-102">Używanie narzędzi deweloperskich programu WCF</span><span class="sxs-lookup"><span data-stu-id="87198-102">Using the WCF Development Tools</span></span>
<span data-ttu-id="87198-103">W tej sekcji opisano narzędzia deweloperskie programu Visual Studio, które mogą pomóc w opracowaniu WCFservice.</span><span class="sxs-lookup"><span data-stu-id="87198-103">This section describes the Visual Studio development tools that can assist you in developing your WCFservice.</span></span>  
  
 <span data-ttu-id="87198-104">Szablony programu Visual Studio można używać jako podstaw do szybkiego tworzenia własnej usługi, a następnie do debugowania i testowania usługi przy użyciu usługi WCF — hosta i klienta testowego WCF.</span><span class="sxs-lookup"><span data-stu-id="87198-104">You can use the Visual Studio templates as a foundation to quickly build your own service, then use WCF Service Auto Host and WCF Test Client to debug and test your service.</span></span> <span data-ttu-id="87198-105">Narzędzia te wspólnie zapewniają szybkie i bezproblemowe cykle debugowania i testowania, a także uniemożliwiają konieczność przekazania do modelu hostingu na wczesnym etapie.</span><span class="sxs-lookup"><span data-stu-id="87198-105">These tools together provide a fast and seamless debug and testing cycle, and preclude the need to commit to a hosting model at an early stage.</span></span>  
 
 > [!NOTE]
 > <span data-ttu-id="87198-106">Począwszy od programu Visual Studio 2017, narzędzia programistyczne WCF nie są instalowane domyślnie.</span><span class="sxs-lookup"><span data-stu-id="87198-106">Starting with Visual Studio 2017, the WCF development tools are not installed by default.</span></span> <span data-ttu-id="87198-107">Aby można było korzystać z tych funkcji, należy upewnić się, że składnik Windows Communication Foundation został wybrany w Instalatorze programu Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="87198-107">In order to use these features, you must ensure the Windows Communication Foundation component is selected in the Visual Studio installer.</span></span>
  
## <a name="the-wcf-developer-tools"></a><span data-ttu-id="87198-108">Narzędzia deweloperskie WCF</span><span class="sxs-lookup"><span data-stu-id="87198-108">The WCF Developer Tools</span></span>  
 [<span data-ttu-id="87198-109">Szablony programu Visual Studio na potrzeby programu WCF</span><span class="sxs-lookup"><span data-stu-id="87198-109">WCF Visual Studio Templates</span></span>](wcf-vs-templates.md)  
  
 <span data-ttu-id="87198-110">Możesz użyć wstępnie zdefiniowanego projektu programu Visual Studio i szablonów elementów w programie Visual Studio, aby szybko tworzyć usługi WCF i otaczające aplikacje.</span><span class="sxs-lookup"><span data-stu-id="87198-110">You can use the predefined Visual Studio project and item templates in Visual Studio to quickly build WCF services and surrounding applications.</span></span>  
  
 [<span data-ttu-id="87198-111">Host usługi WCF (WcfSvcHost.exe)</span><span class="sxs-lookup"><span data-stu-id="87198-111">WCF Service Host (WcfSvcHost.exe)</span></span>](wcf-service-host-wcfsvchost-exe.md)  
  
 <span data-ttu-id="87198-112">Automatyczny Host usługi WCF (WcfSvcHost. exe) umożliwia uruchomienie debugera programu Visual Studio (F5) w celu automatycznego hostowania i testowania wdrożonej usługi.</span><span class="sxs-lookup"><span data-stu-id="87198-112">The WCF Service Auto Host (WcfSvcHost.exe) allows you to launch the Visual Studio debugger (F5) to automatically host and test a service you have implemented.</span></span> <span data-ttu-id="87198-113">Następnie można przetestować usługę przy użyciu klienta testowego WCF (wcfTestClient. exe) lub własnego klienta, aby znaleźć i naprawić wszelkie potencjalne błędy.</span><span class="sxs-lookup"><span data-stu-id="87198-113">You can then test the service using the WCF Test Client (wcfTestClient.exe) or your own client to find and fix any potential errors.</span></span>  
  
 [<span data-ttu-id="87198-114">Testowy klient WCF (WcfTestClient.exe)</span><span class="sxs-lookup"><span data-stu-id="87198-114">WCF Test Client (WcfTestClient.exe)</span></span>](wcf-test-client-wcftestclient-exe.md)  
  
 <span data-ttu-id="87198-115">Klient testowy WCF (WcfTestClient. exe) to narzędzie graficznego interfejsu użytkownika, które umożliwia wprowadzanie parametrów dowolnego typu, przesyłanie tych danych do usługi i wyświetlanie odpowiedzi wysyłanej przez usługę.</span><span class="sxs-lookup"><span data-stu-id="87198-115">WCF Test Client (WcfTestClient.exe) is a GUI tool that allows you to input parameters of arbitrary types, submit that input to the service, and view the response the service sends back.</span></span> <span data-ttu-id="87198-116">Zapewnia bezproblemowe środowisko testowania usług w połączeniu z hostem usługi WCF.</span><span class="sxs-lookup"><span data-stu-id="87198-116">It provides a seamless service testing experience when combined with WCF Service Auto Host.</span></span>  
  
 [<span data-ttu-id="87198-117">Generowanie klas typów danych z kodu XML</span><span class="sxs-lookup"><span data-stu-id="87198-117">Generating Data Type Classes from XML</span></span>](generating-data-type-classes-from-xml.md)  
  
 <span data-ttu-id="87198-118">Dane XML przechowywane w Schowku można wkleić do strony kodowej.</span><span class="sxs-lookup"><span data-stu-id="87198-118">XML data stored in the clipboard can be pasted into a code page.</span></span> <span data-ttu-id="87198-119">Klasy zdefiniowane w danych zostaną przekonwertowane na typy kodu.</span><span class="sxs-lookup"><span data-stu-id="87198-119">The classes defined in the data will be converted to code types.</span></span>  
  
## <a name="using-the-tools-without-administrator-privilege"></a><span data-ttu-id="87198-120">Korzystanie z narzędzi bez uprawnień administratora</span><span class="sxs-lookup"><span data-stu-id="87198-120">Using the Tools without Administrator privilege</span></span>  
 <span data-ttu-id="87198-121">Aby umożliwić użytkownikom bez uprawnień administratora opracowywanie usług WCF, podczas instalacji programu Visual Studio jest tworzona lista kontroli dostępu (Access Control) dla przestrzeni nazw "http://+:8731/Design_Time_Addresses".</span><span class="sxs-lookup"><span data-stu-id="87198-121">To enable users without administrator privilege to develop WCF services, an ACL (Access Control List) is created for the namespace "http://+:8731/Design_Time_Addresses" during the installation of Visual Studio.</span></span> <span data-ttu-id="87198-122">Lista ACL jest ustawiona na (UI), która obejmuje wszystkich użytkowników interakcyjnych zalogowanych na komputerze.</span><span class="sxs-lookup"><span data-stu-id="87198-122">The ACL is set to (UI), which includes all interactive users logged on to the machine.</span></span> <span data-ttu-id="87198-123">Administratorzy mogą dodawać lub usuwać użytkowników z tej listy kontroli dostępu lub otwierać dodatkowe porty. Ta lista ACL umożliwia szablonom programu WCF lub WF wysyłanie i odbieranie danych w konfiguracji domyślnej.</span><span class="sxs-lookup"><span data-stu-id="87198-123">Administrators can add or remove users from this ACL, or open additional ports.This ACL enables WCF or WF templates to send and receive data in their default configuration.</span></span> <span data-ttu-id="87198-124">Umożliwia ona również użytkownikom korzystanie z funkcji Autohost usługi WCF (wcfSvcHost. exe) bez udzielania im uprawnień administratora.</span><span class="sxs-lookup"><span data-stu-id="87198-124">It also enables users to use the WCF Service Auto Host (wcfSvcHost.exe) without granting them administrator privileges.</span></span>  
  
 <span data-ttu-id="87198-125">Dostęp można modyfikować za pomocą narzędzia Netsh. exe w [!INCLUDE[wv](../../../includes/wv-md.md)] na koncie administratora z podwyższonym poziomem uprawnień.</span><span class="sxs-lookup"><span data-stu-id="87198-125">You can modify access using the Netsh.exe tool in [!INCLUDE[wv](../../../includes/wv-md.md)] under the elevated administrator account.</span></span> <span data-ttu-id="87198-126">Poniżej przedstawiono przykład użycia narzędzia Netsh. exe.</span><span class="sxs-lookup"><span data-stu-id="87198-126">The following is an example of using Netsh.exe.</span></span>  
  
```console  
netsh http add urlacl url=http://+:8001/MyService user=<domain>\<user>  
```  
  
 <span data-ttu-id="87198-127">Aby uzyskać więcej informacji na temat narzędzia Netsh. exe, zobacz [jak używać narzędzia Netsh. exe i przełączników wiersza polecenia](https://docs.microsoft.com/previous-versions/tn-archive/bb490939(v=technet.10)).</span><span class="sxs-lookup"><span data-stu-id="87198-127">For more information about Netsh.exe, see [How to Use the Netsh.exe Tool and Command-Line Switches](https://docs.microsoft.com/previous-versions/tn-archive/bb490939(v=technet.10)).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="87198-128">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="87198-128">See also</span></span>

- [<span data-ttu-id="87198-129">Szablony programu Visual Studio na potrzeby programu WCF</span><span class="sxs-lookup"><span data-stu-id="87198-129">WCF Visual Studio Templates</span></span>](wcf-vs-templates.md)
- [<span data-ttu-id="87198-130">Host usługi WCF (WcfSvcHost.exe)</span><span class="sxs-lookup"><span data-stu-id="87198-130">WCF Service Host (WcfSvcHost.exe)</span></span>](wcf-service-host-wcfsvchost-exe.md)
- [<span data-ttu-id="87198-131">Testowy klient WCF (WcfTestClient.exe)</span><span class="sxs-lookup"><span data-stu-id="87198-131">WCF Test Client (WcfTestClient.exe)</span></span>](wcf-test-client-wcftestclient-exe.md)
