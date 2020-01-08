---
title: Przykład FindPrivateKey
ms.date: 12/04/2017
helpviewer_keywords:
- FindPrivateKey
ms.assetid: 16b54116-0ceb-4413-af0c-753bb2a785a6
ms.openlocfilehash: 0ed1e5e81a5d2f7f3586e5dce306e8244b5ebd48
ms.sourcegitcommit: 30a558d23e3ac5a52071121a52c305c85fe15726
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/25/2019
ms.locfileid: "75346015"
---
# <a name="findprivatekey-sample"></a><span data-ttu-id="8aad0-102">Przykład FindPrivateKey</span><span class="sxs-lookup"><span data-stu-id="8aad0-102">FindPrivateKey sample</span></span>

<span data-ttu-id="8aad0-103">Znalezienie lokalizacji i nazwy pliku klucza prywatnego skojarzonego z konkretnym certyfikatem X. 509 w magazynie certyfikatów może być trudne.</span><span class="sxs-lookup"><span data-stu-id="8aad0-103">It can be difficult to find the location and name of the private key file associated with a specific X.509 certificate in the certificate store.</span></span> <span data-ttu-id="8aad0-104">Narzędzie FindPrivateKey. exe ułatwia ten proces.</span><span class="sxs-lookup"><span data-stu-id="8aad0-104">The FindPrivateKey.exe tool facilitates this process.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="8aad0-105">FindPrivateKey to przykład, który należy skompilować przed użyciem.</span><span class="sxs-lookup"><span data-stu-id="8aad0-105">FindPrivateKey is a sample that needs to be compiled prior to use.</span></span> <span data-ttu-id="8aad0-106">Aby uzyskać instrukcje dotyczące sposobu kompilowania narzędzia FindPrivateKey, zobacz sekcję [Aby utworzyć projekt FindPrivateKey](#to-build-the-findprivatekey-project) .</span><span class="sxs-lookup"><span data-stu-id="8aad0-106">See the [To build the FindPrivateKey project](#to-build-the-findprivatekey-project) section for instructions on how to build the FindPrivateKey tool.</span></span>

<span data-ttu-id="8aad0-107">Certyfikaty X. 509 są instalowane przez administratora lub dowolnego użytkownika na komputerze.</span><span class="sxs-lookup"><span data-stu-id="8aad0-107">X.509 certificates are installed by an Administrator or any user in the machine.</span></span> <span data-ttu-id="8aad0-108">Jednak dostęp do certyfikatu może uzyskać usługa działająca przy użyciu innego konta.</span><span class="sxs-lookup"><span data-stu-id="8aad0-108">However, the certificate may be accessed by a service running under a different account.</span></span> <span data-ttu-id="8aad0-109">Na przykład konto usługi sieciowej.</span><span class="sxs-lookup"><span data-stu-id="8aad0-109">For example, the NETWORK SERVICE account.</span></span>

<span data-ttu-id="8aad0-110">To konto może nie mieć dostępu do pliku klucza prywatnego, ponieważ certyfikat nie został pierwotnie zainstalowany.</span><span class="sxs-lookup"><span data-stu-id="8aad0-110">This account may not have access to the private key file because the certificate was not installed by it originally.</span></span> <span data-ttu-id="8aad0-111">Narzędzie FindPrivateKey udostępnia lokalizację danego pliku klucza prywatnego certyfikatu X. 509.</span><span class="sxs-lookup"><span data-stu-id="8aad0-111">The FindPrivateKey tool gives you the location of a given X.509 Certificate's private key file.</span></span> <span data-ttu-id="8aad0-112">Możesz dodać uprawnienia lub usunąć uprawnienia do tego pliku, gdy znasz lokalizację określonego pliku klucza prywatnego certyfikatu X. 509.</span><span class="sxs-lookup"><span data-stu-id="8aad0-112">You can add permissions or remove permissions to this file once you know the location of the particular X.509 certificates' private key file.</span></span>

<span data-ttu-id="8aad0-113">Przykłady używające certyfikatów do zabezpieczeń używają narzędzia FindPrivateKey w pliku *Setup. bat* .</span><span class="sxs-lookup"><span data-stu-id="8aad0-113">The samples that use certificates for security use the FindPrivateKey tool in the *Setup.bat* file.</span></span> <span data-ttu-id="8aad0-114">Po znalezieniu pliku klucza prywatnego można użyć innych narzędzi, takich jak *cacls. exe* , aby ustawić odpowiednie prawa dostępu do pliku.</span><span class="sxs-lookup"><span data-stu-id="8aad0-114">Once the private key file has been found, you can use other tools such as *Cacls.exe* to set the appropriate access rights onto the file.</span></span>

<span data-ttu-id="8aad0-115">Podczas uruchamiania usługi Windows Communication Foundation (WCF) w ramach konta użytkownika, takiego jak samoobsługowy plik wykonywalny, upewnij się, że konto użytkownika ma dostęp tylko do odczytu do pliku.</span><span class="sxs-lookup"><span data-stu-id="8aad0-115">When running a Windows Communication Foundation (WCF) service under a user account, such as a self-hosted executable, ensure that the user account has read-only access to the file.</span></span> <span data-ttu-id="8aad0-116">Podczas uruchamiania usługi WCF w obszarze Internet Information Services (IIS) domyślne konta, na których działa usługa, to usługa sieciowa w usługach IIS w wersji 7 lub starszej lub tożsamość puli aplikacji w usługach IIS 7,5 i nowszych.</span><span class="sxs-lookup"><span data-stu-id="8aad0-116">When running a WCF service under Internet Information Services (IIS) the default accounts that the service runs under are the NETWORK SERVICE on IIS 7 and earlier versions, or Application Pool Identity on IIS 7.5 and later versions.</span></span> <span data-ttu-id="8aad0-117">Aby uzyskać więcej informacji, zobacz [tożsamość puli aplikacji](/iis/manage/configuring-security/application-pool-identities).</span><span class="sxs-lookup"><span data-stu-id="8aad0-117">For more information, see [Application Pool Identities](/iis/manage/configuring-security/application-pool-identities).</span></span>

## <a name="examples"></a><span data-ttu-id="8aad0-118">Przykłady</span><span class="sxs-lookup"><span data-stu-id="8aad0-118">Examples</span></span>

<span data-ttu-id="8aad0-119">Podczas uzyskiwania dostępu do certyfikatu, dla którego proces nie ma uprawnień do odczytu, zobaczysz komunikat o wyjątku podobny do następującego:</span><span class="sxs-lookup"><span data-stu-id="8aad0-119">When accessing a certificate for which the process doesn't have read privilege, you see an exception message similar to the following example:</span></span>

```output
System.ArgumentException was unhandled
Message="The certificate 'CN=localhost' must have a private key that is capable of key exchange.  The process must have access rights for the private key."
Source="System.ServiceModel"
```

<span data-ttu-id="8aad0-120">W takim przypadku należy użyć narzędzia FindPrivateKey, aby znaleźć plik klucza prywatnego, a następnie ustawić prawo dostępu dla procesu, w którym działa usługa.</span><span class="sxs-lookup"><span data-stu-id="8aad0-120">When this occurs, use the FindPrivateKey tool to find the private key file, and then set the access right for the process that the service is running under.</span></span> <span data-ttu-id="8aad0-121">Można to zrobić na przykład za pomocą narzędzia Cacls. exe, jak pokazano w następującym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="8aad0-121">For example, this can be done with the Cacls.exe tool as shown in the following example:</span></span>

```console
cacls.exe "C:\Documents and Settings\All Users\Application Data\Microsoft\Crypto\RSA\MachineKeys\8aeda5eb81555f14f8f9960745b5a40d_38f7de48-5ee9-452d-8a5a-92789d7110b1" /E /G "NETWORK SERVICE":R
```

#### <a name="to-build-the-findprivatekey-project"></a><span data-ttu-id="8aad0-122">Aby skompilować projekt FindPrivateKey</span><span class="sxs-lookup"><span data-stu-id="8aad0-122">To build the FindPrivateKey project</span></span>

<span data-ttu-id="8aad0-123">Aby pobrać projekt, odwiedź [przykłady Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) dla .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459).</span><span class="sxs-lookup"><span data-stu-id="8aad0-123">To download the project, visit [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459).</span></span>

1. <span data-ttu-id="8aad0-124">Otwórz Eksploratora plików i przejdź do folderu *WF_WCF_Samples \wcf\setup\findprivatekey\cs* w lokalizacji katalogu, w której zainstalowano przykład.</span><span class="sxs-lookup"><span data-stu-id="8aad0-124">Open File Explorer and navigate to the *WF_WCF_Samples\WCF\Setup\FindPrivateKey\CS* folder under the directory location where you installed the sample.</span></span>

2. <span data-ttu-id="8aad0-125">Kliknij dwukrotnie ikonę pliku. sln, aby otworzyć plik w programie Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="8aad0-125">Double-click the .sln file icon to open the file in Visual Studio.</span></span>

3. <span data-ttu-id="8aad0-126">W menu **kompilacja** wybierz opcję **Kompiluj ponownie rozwiązanie**.</span><span class="sxs-lookup"><span data-stu-id="8aad0-126">In the **Build** menu, select **Rebuild Solution**.</span></span>

4. <span data-ttu-id="8aad0-127">Kompilowanie rozwiązania generuje plik: FindPrivateKey. exe.</span><span class="sxs-lookup"><span data-stu-id="8aad0-127">Building the solution generates the file: FindPrivateKey.exe.</span></span>

## <a name="conventionscommand-line-entries"></a><span data-ttu-id="8aad0-128">Konwencje — wpisy wiersza polecenia</span><span class="sxs-lookup"><span data-stu-id="8aad0-128">Conventions—Command-Line entries</span></span>

 <span data-ttu-id="8aad0-129">"[*opcja*]" reprezentuje opcjonalny zestaw parametrów.</span><span class="sxs-lookup"><span data-stu-id="8aad0-129">"[*option*]" represents an optional set of parameters.</span></span>

 <span data-ttu-id="8aad0-130">"{*Option*}" reprezentuje obowiązkowy zestaw parametrów.</span><span class="sxs-lookup"><span data-stu-id="8aad0-130">"{*option*}" represents a mandatory set of parameters.</span></span>

 <span data-ttu-id="8aad0-131">"*opcja1* &#124; *opcja2*" reprezentuje wybór między zestawami opcji.</span><span class="sxs-lookup"><span data-stu-id="8aad0-131">"*option1* &#124; *option2*" represents a choice between sets of options.</span></span>

 <span data-ttu-id="8aad0-132">"\<*wartość*>" reprezentuje wartość parametru, która ma zostać wprowadzona.</span><span class="sxs-lookup"><span data-stu-id="8aad0-132">"\<*value*>" represents a parameter value to be entered.</span></span>

## <a name="usage"></a><span data-ttu-id="8aad0-133">Pomiar</span><span class="sxs-lookup"><span data-stu-id="8aad0-133">Usage</span></span>

```console
FindPrivateKey <storeName> <storeLocation> [{ {-n <subjectName>} | {-t <thumbprint>} } [-f | -d | -a]]
```

<span data-ttu-id="8aad0-134">Gdzie:</span><span class="sxs-lookup"><span data-stu-id="8aad0-134">Where:</span></span>

| <span data-ttu-id="8aad0-135">Parametr</span><span class="sxs-lookup"><span data-stu-id="8aad0-135">Parameter</span></span>         | <span data-ttu-id="8aad0-136">Opis</span><span class="sxs-lookup"><span data-stu-id="8aad0-136">Description</span></span>                                                                       |
|-----------------|-----------------------------------------------------------------------------------|
| `<subjectName>` | <span data-ttu-id="8aad0-137">Nazwa podmiotu certyfikatu</span><span class="sxs-lookup"><span data-stu-id="8aad0-137">The subject name of the certificate</span></span>                                               |
| `<thumbprint>`  | <span data-ttu-id="8aad0-138">Odcisk palca certyfikatu (można go znaleźć za pomocą narzędzia certmgr. exe)</span><span class="sxs-lookup"><span data-stu-id="8aad0-138">The thumbprint of the certificate (You can use the Certmgr.exe tool to find this)</span></span> |
| `-f`            | <span data-ttu-id="8aad0-139">tylko nazwa pliku wyjściowego</span><span class="sxs-lookup"><span data-stu-id="8aad0-139">output file name only</span></span>                                                             |
| `-d`            | <span data-ttu-id="8aad0-140">tylko katalog wyjściowy</span><span class="sxs-lookup"><span data-stu-id="8aad0-140">output directory only</span></span>                                                             |
| `-a`            | <span data-ttu-id="8aad0-141">niepełna nazwa pliku wyjściowego</span><span class="sxs-lookup"><span data-stu-id="8aad0-141">output absolute file name</span></span>                                                         |

<span data-ttu-id="8aad0-142">Jeśli w wierszu polecenia nie określono żadnych parametrów, zostanie wyświetlony tekst pomocy z tymi informacjami.</span><span class="sxs-lookup"><span data-stu-id="8aad0-142">If no parameters are specified at the command prompt, then help text with this information is displayed.</span></span>

## <a name="examples"></a><span data-ttu-id="8aad0-143">Przykłady</span><span class="sxs-lookup"><span data-stu-id="8aad0-143">Examples</span></span>

<span data-ttu-id="8aad0-144">Ten przykład umożliwia znalezienie nazwy pliku certyfikatu z nazwą podmiotu "CN = localhost" w magazynie osobistym bieżącego użytkownika.</span><span class="sxs-lookup"><span data-stu-id="8aad0-144">This example finds the filename of the certificate with a subject name of "CN=localhost", in the Personal store of the Current User.</span></span>

```console
FindPrivateKey My CurrentUser -n "CN=localhost"
```

<span data-ttu-id="8aad0-145">Ten przykład umożliwia znalezienie nazwy pliku certyfikatu z nazwą podmiotu "CN = localhost" w magazynie osobistym bieżącego użytkownika i wyjściem pełnej ścieżki katalogu.</span><span class="sxs-lookup"><span data-stu-id="8aad0-145">This example finds the filename of the certificate with a subject name of "CN=localhost", in the Personal store of the Current User and output the full directory path.</span></span>

```console
FindPrivateKey My CurrentUser -n "CN=localhost" -a
```

<span data-ttu-id="8aad0-146">W tym przykładzie znajduje się nazwa pliku certyfikatu z odciskiem palca "03 33 98 63 d0 47 E7 48 71 33 62 64 76 5c 4C 9d 42 1D 6B 52" w magazynie osobistym komputera lokalnego.</span><span class="sxs-lookup"><span data-stu-id="8aad0-146">This example finds the filename of the certificate with a thumbprint of "03 33 98 63 d0 47 e7 48 71 33 62 64 76 5c 4c 9d 42 1d 6b 52", in the Personal store of the Local Computer.</span></span>

```console
FindPrivateKey My LocalMachine -t "03 33 98 63 d0 47 e7 48 71 33 62 64 76 5c 4c 9d 42 1d 6b 52"
```
