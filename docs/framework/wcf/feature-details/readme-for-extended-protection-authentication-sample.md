---
title: Plik ReadMe dla uwierzytelniania na potrzeby zabezpieczeń rozszerzonych — przykład
ms.date: 03/30/2017
ms.assetid: 80bf2e97-398d-4db5-9040-d96478a2ccab
ms.openlocfilehash: 9b0a3535282a1fcc1103651f5601459e80d3d8d4
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/09/2020
ms.locfileid: "84601104"
---
# <a name="readme-for-extended-protection-authentication-sample"></a><span data-ttu-id="a218f-102">Plik ReadMe dla uwierzytelniania na potrzeby zabezpieczeń rozszerzonych — przykład</span><span class="sxs-lookup"><span data-stu-id="a218f-102">ReadMe for Extended Protection Authentication Sample</span></span>

<span data-ttu-id="a218f-103">Ochrona rozszerzona to inicjatywa zabezpieczeń chroniąca przed atakami typu man-in-the-Middle (MITM), w których osoba atakująca ("man-in-the-middle") przechwytuje poświadczenia klienta i używa ich do uzyskiwania dostępu do zabezpieczonych zasobów na zamierzonym serwerze klienta.</span><span class="sxs-lookup"><span data-stu-id="a218f-103">Extended Protection is a security initiative to protect against man-in-the-middle (MITM) attacks, in which an attacker (the "man-in-the-middle") intercepts a client’s credentials and uses them to access secure resources on the client’s intended server.</span></span>

<span data-ttu-id="a218f-104">Aby uzyskać więcej informacji, zobacz [Ochrona rozszerzona uwierzytelniania przegląd](extended-protection-for-authentication-overview.md).</span><span class="sxs-lookup"><span data-stu-id="a218f-104">For more information, see [Extended Protection for Authentication Overview](extended-protection-for-authentication-overview.md).</span></span>

> [!NOTE]
> <span data-ttu-id="a218f-105">Ten przykład działa tylko w przypadku hostowania w usługach IIS.</span><span class="sxs-lookup"><span data-stu-id="a218f-105">This sample only works when hosted on IIS.</span></span> <span data-ttu-id="a218f-106">Nie działa na serwerze deweloperskim programu Visual Studio, ponieważ nie obsługuje protokołu HTTPS.</span><span class="sxs-lookup"><span data-stu-id="a218f-106">It does not work on Visual Studio Development Server because that does not support HTTPS.</span></span>

## <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="a218f-107">Aby skonfigurować, skompilować i uruchomić przykład</span><span class="sxs-lookup"><span data-stu-id="a218f-107">To Set Up, Build, and Run the Sample</span></span>

1. <span data-ttu-id="a218f-108">Zainstaluj usługi IIS na maszynie za pomocą apletu Dodaj/Usuń programy — > funkcje systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="a218f-108">Install IIS on the machine from Add/Remove Programs -> Windows Features.</span></span>

2. <span data-ttu-id="a218f-109">Włącz uwierzytelnianie systemu Windows w funkcjach systemu Windows: Internet Information Services > World Wide Web Services — > zabezpieczenia-> uwierzytelniania systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="a218f-109">Turn on Windows Authentication in Windows features: Internet Information Services -> World Wide Web Services -> Security -> Windows Authentication.</span></span>

3. <span data-ttu-id="a218f-110">Włącz aktywację HTTP w funkcjach systemu Windows: Microsoft .NET Framework 3.5.1-> Windows Communication Foundation Aktywacja HTTP.</span><span class="sxs-lookup"><span data-stu-id="a218f-110">Turn on HTTP Activation in Windows features: Microsoft .NET Framework 3.5.1 -> Windows Communication Foundation HTTP Activation.</span></span>

4. <span data-ttu-id="a218f-111">Ten przykład wymaga od klienta ustanowienia bezpiecznego kanału z serwerem i dlatego wymaga obecności certyfikatu serwera, który można zainstalować z Menedżera Internet Information Services (IIS).</span><span class="sxs-lookup"><span data-stu-id="a218f-111">This sample requires the client to establish a secure channel with the server and so it requires the presence of a server certificate which can be installed from Internet Information Services (IIS) Manager.</span></span>

    1. <span data-ttu-id="a218f-112">Otwórz Menedżera usług IIS — > certyfikaty serwera (z karty Widok funkcji).</span><span class="sxs-lookup"><span data-stu-id="a218f-112">Open the IIS manager -> Server certificates (from the feature view tab).</span></span>

    2. <span data-ttu-id="a218f-113">Na potrzeby testowania tego przykładu można utworzyć certyfikat z podpisem własnym.</span><span class="sxs-lookup"><span data-stu-id="a218f-113">For the purpose of testing this sample, you can create a self-signed certificate.</span></span> <span data-ttu-id="a218f-114">(Jeśli nie chcesz, aby program Internet Explorer monitował o certyfikat, który nie jest zabezpieczony, możesz go zainstalować w magazynie głównego urzędu certyfikacji zaufanych certyfikatów).</span><span class="sxs-lookup"><span data-stu-id="a218f-114">(If you don’t want Internet Explorer to prompt you about the certificate not being secure, you can install it in the Trusted Certificate Root authority store).</span></span>

5. <span data-ttu-id="a218f-115">Przejdź do okienka Akcje dla domyślnej witryny sieci Web.</span><span class="sxs-lookup"><span data-stu-id="a218f-115">Go to the Actions pane for the Default Web site.</span></span> <span data-ttu-id="a218f-116">Kliknij pozycję Edytuj powiązania > lokacji.</span><span class="sxs-lookup"><span data-stu-id="a218f-116">Click Edit Site -> Bindings.</span></span> <span data-ttu-id="a218f-117">Dodaj protokół HTTPS jako typ, jeśli nie jest jeszcze obecny, z numerem portu 443 i przypisz certyfikat SSL utworzony w powyższym kroku.</span><span class="sxs-lookup"><span data-stu-id="a218f-117">Add HTTPS as a type if it is not already present, with port number 443, and assign the SSL certificate created in the above step.</span></span>

6. <span data-ttu-id="a218f-118">Tworzenie usługi.</span><span class="sxs-lookup"><span data-stu-id="a218f-118">Build the service.</span></span> <span data-ttu-id="a218f-119">Spowoduje to utworzenie katalogu wirtualnego w usługach IIS (z akcji po kompilacji określonej we właściwościach projektu) i skopiowanie plików DLL, svc i konfiguracji, zgodnie z wymaganiami, aby usługa była hostowana w sieci Web.</span><span class="sxs-lookup"><span data-stu-id="a218f-119">This creates a virtual directory in IIS for you (from the post build action specified in the project properties) and copies the dll, .svc and config files as needed for a service to be Web hosted.</span></span>

7. <span data-ttu-id="a218f-120">Otwórz Menedżera usług IIS.</span><span class="sxs-lookup"><span data-stu-id="a218f-120">Open the IIS Manager.</span></span> <span data-ttu-id="a218f-121">Kliknij prawym przyciskiem myszy katalog wirtualny (Kiedy), który został utworzony w poprzednim kroku, a następnie wybierz polecenie Konwertuj na aplikację.</span><span class="sxs-lookup"><span data-stu-id="a218f-121">Right-click the virtual directory (ExtendedProtection) that you created in the previous step and select Convert to Application.</span></span>

8. <span data-ttu-id="a218f-122">Otwórz moduł uwierzytelniania w Menedżerze usług IIS dla tego katalogu wirtualnego i Włącz uwierzytelnianie systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="a218f-122">Open the Authentication module in IIS Manager for this virtual directory and enable Windows Authentication.</span></span>

9. <span data-ttu-id="a218f-123">Otwórz ustawienia zaawansowane uwierzytelniania systemu Windows dla tego katalogu wirtualnego i ustaw je na wymagane, ponieważ w przykładzie, odpowiednie ustawienie kiedy jest ustawione na zawsze.</span><span class="sxs-lookup"><span data-stu-id="a218f-123">Open the Advanced Settings for Windows Authentication for this virtual directory and set it to Required, since, in the sample, the corresponding ExtendedProtection setting is set to Always.</span></span>

10. <span data-ttu-id="a218f-124">Usługę można przetestować, uzyskując dostęp do adresu URL z okna przeglądarki.</span><span class="sxs-lookup"><span data-stu-id="a218f-124">You can test the service by accessing the URL from a browser window.</span></span> <span data-ttu-id="a218f-125">Jeśli chcesz uzyskać dostęp do tego adresu URL z wielu maszyn, upewnij się, że Zapora jest otwarta dla wszystkich przychodzących połączeń HTTP i HTTPS.</span><span class="sxs-lookup"><span data-stu-id="a218f-125">If you want to access this URL from a cross machine, make sure that the firewall is opened for all incoming HTTP and HTTPS connections.</span></span>

11. <span data-ttu-id="a218f-126">Otwórz plik konfiguracji klienta i podaj pełną nazwę komputera dla \<client>  -  \<endpoint> atrybutu-Address, zastępując ciąg \<full_machine_name> .</span><span class="sxs-lookup"><span data-stu-id="a218f-126">Open the client config file and provide a full machine name for the \<client> - \<endpoint> - address attribute, replacing \<full_machine_name>.</span></span>

12. <span data-ttu-id="a218f-127">Uruchom klienta programu.</span><span class="sxs-lookup"><span data-stu-id="a218f-127">Run the client.</span></span> <span data-ttu-id="a218f-128">Klient komunikuje się z usługą, ustanawiając bezpieczny kanał i używając rozszerzonej ochrony w ramach okładek.</span><span class="sxs-lookup"><span data-stu-id="a218f-128">The client communicates to the service by establishing a secure channel and using extended protection under the covers.</span></span>
