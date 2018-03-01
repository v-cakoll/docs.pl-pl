---
title: "Przykładowe FindPrivateKey - WCF"
ms.date: 12/04/2017
ms.prod: .net-framework
ms.technology: dotnet-clr
ms.topic: article
helpviewer_keywords:
- FindPrivateKey
ms.assetid: 16b54116-0ceb-4413-af0c-753bb2a785a6
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 32e1a4a3de01371d67be8d19613b1f29c1ce3c29
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="findprivatekey-sample"></a><span data-ttu-id="87a97-102">Przykładowe FindPrivateKey</span><span class="sxs-lookup"><span data-stu-id="87a97-102">FindPrivateKey sample</span></span>

<span data-ttu-id="87a97-103">Może być trudne znaleźć lokalizację i nazwę pliku klucza prywatnego skojarzonego z certyfikatem X.509 określonej w magazynie certyfikatów.</span><span class="sxs-lookup"><span data-stu-id="87a97-103">It can be difficult to find the location and name of the private key file associated with a specific X.509 certificate in the certificate store.</span></span> <span data-ttu-id="87a97-104">Narzędzie FindPrivateKey.exe ułatwia ten proces.</span><span class="sxs-lookup"><span data-stu-id="87a97-104">The FindPrivateKey.exe tool facilitates this process.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="87a97-105">FindPrivateKey to przykład, który musi być skompilowany przed ich użyciem.</span><span class="sxs-lookup"><span data-stu-id="87a97-105">FindPrivateKey is a sample that needs to be compiled prior to use.</span></span> <span data-ttu-id="87a97-106">Zobacz [Aby skompilować projekt FindPrivateKey](#to-build-the-findprivatekey-project) sekcji, aby uzyskać instrukcje dotyczące sposobu tworzenia narzędzia FindPrivateKey.</span><span class="sxs-lookup"><span data-stu-id="87a97-106">See the [To build the FindPrivateKey project](#to-build-the-findprivatekey-project) section for instructions on how to build the FindPrivateKey tool.</span></span>

<span data-ttu-id="87a97-107">Certyfikaty X.509 są instalowane przez administratora lub dowolnego użytkownika na maszynie.</span><span class="sxs-lookup"><span data-stu-id="87a97-107">X.509 certificates are installed by an Administrator or any user in the machine.</span></span> <span data-ttu-id="87a97-108">Jednak certyfikat mogą być używane przez usługę uruchomiony przy użyciu innego konta.</span><span class="sxs-lookup"><span data-stu-id="87a97-108">However, the certificate may be accessed by a service running under a different account.</span></span> <span data-ttu-id="87a97-109">Na przykład konto Usługa sieciowa.</span><span class="sxs-lookup"><span data-stu-id="87a97-109">For example, the NETWORK SERVICE account.</span></span>

<span data-ttu-id="87a97-110">To konto może nie mieć dostępu do pliku klucza prywatnego, ponieważ certyfikat nie został zainstalowany przez nią pierwotnie.</span><span class="sxs-lookup"><span data-stu-id="87a97-110">This account may not have access to the private key file because the certificate was not installed by it originally.</span></span> <span data-ttu-id="87a97-111">FindPrivateKey udostępnia lokalizację pliku klucza prywatnego danego certyfikatu X.509.</span><span class="sxs-lookup"><span data-stu-id="87a97-111">The FindPrivateKey tool gives you the location of a given X.509 Certificate's private key file.</span></span> <span data-ttu-id="87a97-112">Można dodać uprawnienia lub usunąć uprawnienia do tego pliku, znając lokalizację certyfikatów X.509 określonego pliku klucza prywatnego.</span><span class="sxs-lookup"><span data-stu-id="87a97-112">You can add permissions or remove permissions to this file once you know the location of the particular X.509 certificates' private key file.</span></span>

<span data-ttu-id="87a97-113">Przykłady, które korzystają z certyfikatów do zabezpieczenia za pomocą narzędzia FindPrivateKey w *pliku Setup.bat* pliku.</span><span class="sxs-lookup"><span data-stu-id="87a97-113">The samples that use certificates for security use the FindPrivateKey tool in the *Setup.bat* file.</span></span> <span data-ttu-id="87a97-114">Po znalezieniu pliku klucza prywatnego można użyć innych narzędzi takich jak *Cacls.exe* można ustawić odpowiednie uprawnienia dostępu do pliku.</span><span class="sxs-lookup"><span data-stu-id="87a97-114">Once the private key file has been found, you can use other tools such as *Cacls.exe* to set the appropriate access rights onto the file.</span></span>

<span data-ttu-id="87a97-115">Podczas uruchamiania usługi Windows Communication Foundation (WCF) przy użyciu konta użytkownika, takie jak hostowanie Samoobsługowe pliku wykonywalnego, upewnij się, że konto użytkownika ma dostęp tylko do odczytu do pliku.</span><span class="sxs-lookup"><span data-stu-id="87a97-115">When running a Windows Communication Foundation (WCF) service under a user account, such as a self-hosted executable, ensure that the user account has read-only access to the file.</span></span> <span data-ttu-id="87a97-116">Podczas uruchamiania usługi WCF w obszarze usługi Internet Information Services (IIS) domyślne konta, które usługa będzie uruchamiana to usługa sieciowa w usługach IIS 7 i wcześniejsze wersje lub tożsamość puli aplikacji usług IIS 7.5 i nowsze wersje.</span><span class="sxs-lookup"><span data-stu-id="87a97-116">When running a WCF service under Internet Information Services (IIS) the default accounts that the service runs under are the NETWORK SERVICE on IIS 7 and earlier versions, or Application Pool Identity on IIS 7.5 and later versions.</span></span> <span data-ttu-id="87a97-117">Aby uzyskać więcej informacji, zobacz [tożsamości puli aplikacji](/iis/manage/configuring-security/application-pool-identities).</span><span class="sxs-lookup"><span data-stu-id="87a97-117">For more information, see [Application Pool Identities](/iis/manage/configuring-security/application-pool-identities).</span></span>

## <a name="examples"></a><span data-ttu-id="87a97-118">Przykłady</span><span class="sxs-lookup"><span data-stu-id="87a97-118">Examples</span></span>

<span data-ttu-id="87a97-119">Podczas uzyskiwania dostępu do certyfikatu, dla którego proces nie ma uprawnień odczytu, zobaczysz komunikat o wyjątku podobny do poniższego przykładu:</span><span class="sxs-lookup"><span data-stu-id="87a97-119">When accessing a certificate for which the process doesn't have read privilege, you see an exception message similar to the following example:</span></span>

```
System.ArgumentException was unhandled
Message="The certificate 'CN=localhost' must have a private key that is capable of key exchange.  The process must have access rights for the private key."
Source="System.ServiceModel"
```

<span data-ttu-id="87a97-120">W takim przypadku służy narzędzie FindPrivateKey można znaleźć pliku klucza prywatnego, a następnie ustaw dostępu prawa dla procesu, czy usługa jest uruchomiona w obszarze.</span><span class="sxs-lookup"><span data-stu-id="87a97-120">When this occurs, use the FindPrivateKey tool to find the private key file, and then set the access right for the process that the service is running under.</span></span> <span data-ttu-id="87a97-121">Na przykład można to zrobić za pomocą narzędzia Cacls.exe jak pokazano w poniższym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="87a97-121">For example, this can be done with the Cacls.exe tool as shown in the following example:</span></span>

```
cacls.exe "C:\Documents and Settings\All Users\Application Data\Microsoft\Crypto\RSA\MachineKeys\8aeda5eb81555f14f8f9960745b5a40d_38f7de48-5ee9-452d-8a5a-92789d7110b1" /E /G "NETWORK SERVICE":R
```

#### <a name="to-build-the-findprivatekey-project"></a><span data-ttu-id="87a97-122">Aby skompilować projekt FindPrivateKey</span><span class="sxs-lookup"><span data-stu-id="87a97-122">To build the FindPrivateKey project</span></span>

<span data-ttu-id="87a97-123">Aby pobrać projekt, odwiedź stronę [Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) przykłady dla programu .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459).</span><span class="sxs-lookup"><span data-stu-id="87a97-123">To download the project, visit [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459).</span></span>

1. <span data-ttu-id="87a97-124">Otwórz [!INCLUDE[fileExplorer](../../../../includes/fileexplorer-md.md)] i przejdź do *WF_WCF_Samples\WCF\Setup\FindPrivateKey\CS* folder na lokalizację katalogu, w którym zainstalowano próbki.</span><span class="sxs-lookup"><span data-stu-id="87a97-124">Open [!INCLUDE[fileExplorer](../../../../includes/fileexplorer-md.md)] and navigate to the *WF_WCF_Samples\WCF\Setup\FindPrivateKey\CS* folder under the directory location where you installed the sample.</span></span>

2. <span data-ttu-id="87a97-125">Kliknij dwukrotnie ikonę pliku SLN, można otworzyć pliku w programie Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="87a97-125">Double-click the .sln file icon to open the file in Visual Studio.</span></span>

3. <span data-ttu-id="87a97-126">W **kompilacji** menu, wybierz opcję **Kompiluj ponownie rozwiązanie**.</span><span class="sxs-lookup"><span data-stu-id="87a97-126">In the **Build** menu, select **Rebuild Solution**.</span></span>

4. <span data-ttu-id="87a97-127">Tworzenie rozwiązania generuje plik: FindPrivateKey.exe.</span><span class="sxs-lookup"><span data-stu-id="87a97-127">Building the solution generates the file: FindPrivateKey.exe.</span></span>

## <a name="conventionscommand-line-entries"></a><span data-ttu-id="87a97-128">Konwencje — wpisy wiersza polecenia</span><span class="sxs-lookup"><span data-stu-id="87a97-128">Conventions—Command-Line entries</span></span>

 <span data-ttu-id="87a97-129">"[*opcji*]" reprezentuje opcjonalny zestaw parametrów.</span><span class="sxs-lookup"><span data-stu-id="87a97-129">"[*option*]" represents an optional set of parameters.</span></span>

 <span data-ttu-id="87a97-130">"{*opcji*}" reprezentuje obowiązkowe zestaw parametrów.</span><span class="sxs-lookup"><span data-stu-id="87a97-130">"{*option*}" represents a mandatory set of parameters.</span></span>

 <span data-ttu-id="87a97-131">"*opcja 1* &#124; *option2*"reprezentuje wybór między Ustawia opcje.</span><span class="sxs-lookup"><span data-stu-id="87a97-131">"*option1* &#124; *option2*" represents a choice between sets of options.</span></span>

 <span data-ttu-id="87a97-132">"\<*wartość*>" reprezentuje należy podać wartość parametru.</span><span class="sxs-lookup"><span data-stu-id="87a97-132">"\<*value*>" represents a parameter value to be entered.</span></span>

## <a name="usage"></a><span data-ttu-id="87a97-133">Użycie</span><span class="sxs-lookup"><span data-stu-id="87a97-133">Usage</span></span>

```
FindPrivateKey <storeName> <storeLocation> [{ {-n <subjectName>} | {-t <thumbprint>} } [-f | -d | -a]]
```

<span data-ttu-id="87a97-134">Gdzie:</span><span class="sxs-lookup"><span data-stu-id="87a97-134">Where:</span></span>

```
       <subjectName> The subject name of the certificate
       <thumbprint>  The thumbprint of the certificate (You can use the Certmgr.exe tool to find this)
       -f            output file name only
       -d            output directory only
       -a            output absolute file name
```

<span data-ttu-id="87a97-135">Jeśli nie zostały podane parametry w wierszu polecenia, wyświetlany jest ten tekst pomocy.</span><span class="sxs-lookup"><span data-stu-id="87a97-135">If no parameters are specified at the command prompt, then this help text is displayed.</span></span>

## <a name="examples"></a><span data-ttu-id="87a97-136">Przykłady</span><span class="sxs-lookup"><span data-stu-id="87a97-136">Examples</span></span>

<span data-ttu-id="87a97-137">W tym przykładzie znajdzie pliku certyfikatu z nazwą podmiotu "CN = host_lokalny", w magazynie osobistym bieżącego użytkownika.</span><span class="sxs-lookup"><span data-stu-id="87a97-137">This example finds the filename of the certificate with a subject name of "CN=localhost", in the Personal store of the Current User.</span></span>

```
FindPrivateKey My CurrentUser -n "CN=localhost"
```

<span data-ttu-id="87a97-138">W tym przykładzie znajdzie pliku certyfikatu z nazwą podmiotu "CN = host_lokalny", w osobistych przechowywać bieżącego użytkownika i dane wyjściowe pełną ścieżką.</span><span class="sxs-lookup"><span data-stu-id="87a97-138">This example finds the filename of the certificate with a subject name of "CN=localhost", in the Personal store of the Current User and output the full directory path.</span></span>

```
FindPrivateKey My CurrentUser -n "CN=localhost" -a
```

<span data-ttu-id="87a97-139">W tym przykładzie znajdzie nazwę certyfikatu z odciskiem palca "03 33 98 63 d0 47 e7 48 71 33 62 64 76 5c 4c 9d 42 1 d 6b 52", w magazynie osobistym komputera lokalnego.</span><span class="sxs-lookup"><span data-stu-id="87a97-139">This example finds the filename of the certificate with a thumbprint of "03 33 98 63 d0 47 e7 48 71 33 62 64 76 5c 4c 9d 42 1d 6b 52", in the Personal store of the Local Computer.</span></span>

```
FindPrivateKey My LocalMachine -t "03 33 98 63 d0 47 e7 48 71 33 62 64 76 5c 4c 9d 42 1d 6b 52"
```
