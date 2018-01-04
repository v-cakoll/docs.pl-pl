---
title: "Plik ReadMe dla uwierzytelniania na potrzeby zabezpieczeń rozszerzonych — przykład"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 80bf2e97-398d-4db5-9040-d96478a2ccab
caps.latest.revision: "3"
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.workload: dotnet
ms.openlocfilehash: 78e787c129c0161e8730472124ee4162e2d1ba9d
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="readme-for-extended-protection-authentication-sample"></a><span data-ttu-id="95254-102">Plik ReadMe dla uwierzytelniania na potrzeby zabezpieczeń rozszerzonych — przykład</span><span class="sxs-lookup"><span data-stu-id="95254-102">ReadMe for Extended Protection Authentication Sample</span></span>
<span data-ttu-id="95254-103">Ochrona rozszerzona jest inicjatywą zabezpieczeń do ochrony przed man-in--middle (MITM) ataków, w których osoba atakująca ("man-in--middle") przechwytuje poświadczenia klienta i używa ich do uzyskiwania dostępu bezpiecznych zasobów na serwerze danego klienta.</span><span class="sxs-lookup"><span data-stu-id="95254-103">Extended Protection is a security initiative to protect against man-in-the-middle (MITM) attacks, in which an attacker (the "man-in-the-middle") intercepts a client’s credentials and uses them to access secure resources on the client’s intended server.</span></span>  
  
 <span data-ttu-id="95254-104">Aby uzyskać więcej informacji, zobacz [ochrona rozszerzona na potrzeby uwierzytelniania omówienie](../../../../docs/framework/wcf/feature-details/extended-protection-for-authentication-overview.md).</span><span class="sxs-lookup"><span data-stu-id="95254-104">For more information, see [Extended Protection for Authentication Overview](../../../../docs/framework/wcf/feature-details/extended-protection-for-authentication-overview.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="95254-105">W tym przykładzie działa tylko w przypadku, gdy hostowanych w usługach IIS.</span><span class="sxs-lookup"><span data-stu-id="95254-105">This sample only works when hosted on IIS.</span></span> <span data-ttu-id="95254-106">On nie działać na serwera wdrożeniowego Visual Studio, ponieważ nie obsługuje protokołu HTTPS.</span><span class="sxs-lookup"><span data-stu-id="95254-106">It does not work on Visual Studio Development Server because that does not support HTTPS.</span></span>  
  
## <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="95254-107">Aby skonfigurować, kompilacji, a następnie uruchom próbki</span><span class="sxs-lookup"><span data-stu-id="95254-107">To Set Up, Build, and Run the Sample</span></span>  
  
1.  <span data-ttu-id="95254-108">Zainstaluj usługę IIS na komputerze z apletu Dodaj/Usuń programy -> Funkcje systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="95254-108">Install IIS on the machine from Add/Remove Programs -> Windows Features.</span></span>  
  
2.  <span data-ttu-id="95254-109">Włącz uwierzytelnianie systemu Windows w funkcji systemu Windows: Internetowe usługi informacyjne -> usługi sieci World Wide Web -> Zabezpieczenia -> uwierzytelniania systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="95254-109">Turn on Windows Authentication in Windows features: Internet Information Services -> World Wide Web Services -> Security -> Windows Authentication.</span></span>  
  
3.  <span data-ttu-id="95254-110">Włącz aktywację HTTP w funkcji systemu Windows: Microsoft .NET Framework 3.5.1 -> Aktywacja HTTP programu Windows Communication Foundation.</span><span class="sxs-lookup"><span data-stu-id="95254-110">Turn on HTTP Activation in Windows features: Microsoft .NET Framework 3.5.1 -> Windows Communication Foundation HTTP Activation.</span></span>  
  
4.  <span data-ttu-id="95254-111">W tym przykładzie wymaga klienta do ustanowienia bezpiecznego kanału z serwerem i dlatego wymaga obecności certyfikat serwera, które można zainstalować z programu Internet Information Services (IIS) Manager.</span><span class="sxs-lookup"><span data-stu-id="95254-111">This sample requires the client to establish a secure channel with the server and so it requires the presence of a server certificate which can be installed from Internet Information Services (IIS) Manager.</span></span>  
  
    1.  <span data-ttu-id="95254-112">Otwórz Menedżera usług IIS -> certyfikatów serwera (na karcie Widok funkcji).</span><span class="sxs-lookup"><span data-stu-id="95254-112">Open the IIS manager -> Server certificates (from the feature view tab).</span></span>  
  
    2.  <span data-ttu-id="95254-113">Na potrzeby testowania w tym przykładzie, można utworzyć certyfikatu z podpisem własnym.</span><span class="sxs-lookup"><span data-stu-id="95254-113">For the purpose of testing this sample, you can create a self-signed certificate.</span></span> <span data-ttu-id="95254-114">(Jeśli nie chcesz, aby program Internet Explorer będzie wyświetlany monit o certyfikat nie jest bezpieczne, można zainstalować go w magazynie zaufanego certyfikatu głównego urzędu).</span><span class="sxs-lookup"><span data-stu-id="95254-114">(If you don’t want Internet Explorer to prompt you about the certificate not being secure, you can install it in the Trusted Certificate Root authority store).</span></span>  
  
5.  <span data-ttu-id="95254-115">Przejdź do okienka Akcje dla domyślnej witryny sieci Web.</span><span class="sxs-lookup"><span data-stu-id="95254-115">Go to the Actions pane for the Default Web site.</span></span> <span data-ttu-id="95254-116">Kliknij przycisk Edytuj lokacji -> powiązania.</span><span class="sxs-lookup"><span data-stu-id="95254-116">Click Edit Site -> Bindings.</span></span> <span data-ttu-id="95254-117">Dodaj HTTPS jako typ, jeśli nie jest już istnieje z numerem portu 443 i przypisz certyfikat SSL utworzony w kroku powyżej.</span><span class="sxs-lookup"><span data-stu-id="95254-117">Add HTTPS as a type if it is not already present, with port number 443, and assign the SSL certificate created in the above step.</span></span>  
  
6.  <span data-ttu-id="95254-118">Tworzenie usługi.</span><span class="sxs-lookup"><span data-stu-id="95254-118">Build the service.</span></span> <span data-ttu-id="95254-119">Tworzy katalog wirtualny w usługach IIS (z akcji kompilacji po określonej we właściwościach projektu) i kopiuje pliki dll, SVC i config zgodnie z potrzebami dla usługi, aby być hostowana w sieci Web.</span><span class="sxs-lookup"><span data-stu-id="95254-119">This creates a virtual directory in IIS for you (from the post build action specified in the project properties) and copies the dll, .svc and config files as needed for a service to be Web hosted.</span></span>  
  
7.  <span data-ttu-id="95254-120">Otwórz Menedżera usług IIS.</span><span class="sxs-lookup"><span data-stu-id="95254-120">Open the IIS Manager.</span></span> <span data-ttu-id="95254-121">Kliknij prawym przyciskiem myszy katalogu wirtualnego (ochrona rozszerzona), który został utworzony w poprzednim kroku, a następnie wybierz konwersji do aplikacji.</span><span class="sxs-lookup"><span data-stu-id="95254-121">Right-click the virtual directory (ExtendedProtection) that you created in the previous step and select Convert to Application.</span></span>  
  
8.  <span data-ttu-id="95254-122">Otwórz moduł uwierzytelniania w Menedżerze usług IIS dla tego katalogu wirtualnego, a następnie włączyć uwierzytelnianie systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="95254-122">Open the Authentication module in IIS Manager for this virtual directory and enable Windows Authentication.</span></span>  
  
9. <span data-ttu-id="95254-123">Otwórz Zaawansowane ustawienia dla uwierzytelniania systemu Windows dla tego katalogu wirtualnego i ustaw ją na wymagane, ponieważ w przykładzie odpowiednie ustawienie Ochrona rozszerzona ma wartość Always.</span><span class="sxs-lookup"><span data-stu-id="95254-123">Open the Advanced Settings for Windows Authentication for this virtual directory and set it to Required, since, in the sample, the corresponding ExtendedProtection setting is set to Always.</span></span>  
  
10. <span data-ttu-id="95254-124">Można testować usługę, uzyskując dostęp do adresu URL z okna przeglądarki.</span><span class="sxs-lookup"><span data-stu-id="95254-124">You can test the service by accessing the URL from a browser window.</span></span> <span data-ttu-id="95254-125">Aby uzyskać dostęp do tego adresu URL z krzyżowego maszyny, upewnij się, że zapory jest otwarty dla wszystkich połączeń przychodzących HTTP i HTTPS.</span><span class="sxs-lookup"><span data-stu-id="95254-125">If you want to access this URL from a cross machine, make sure that the firewall is opened for all incoming HTTP and HTTPS connections.</span></span>  
  
11. <span data-ttu-id="95254-126">Otwórz plik konfiguracji klienta i podaj nazwę maszyny pełne \<klienta >- \<punktu końcowego > — atrybut adresu, zastępując << full_machine_name >>.</span><span class="sxs-lookup"><span data-stu-id="95254-126">Open the client config file and provide a full machine name for the \<client> - \<endpoint> - address attribute, replacing <<full_machine_name>>.</span></span>  
  
12. <span data-ttu-id="95254-127">Uruchom klienta.</span><span class="sxs-lookup"><span data-stu-id="95254-127">Run the client.</span></span> <span data-ttu-id="95254-128">Klient komunikuje się z usługą ustanowienie bezpiecznego kanału i używając ochrona rozszerzona w tle.</span><span class="sxs-lookup"><span data-stu-id="95254-128">The client communicates to the service by establishing a secure channel and using extended protection under the covers.</span></span>
