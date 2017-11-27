---
title: FindPrivateKey
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: FindPrivateKey
ms.assetid: 16b54116-0ceb-4413-af0c-753bb2a785a6
caps.latest.revision: "14"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: c1ff00bead6130601070ac94686ee9622a6fe218
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="findprivatekey"></a><span data-ttu-id="a792f-102">FindPrivateKey</span><span class="sxs-lookup"><span data-stu-id="a792f-102">FindPrivateKey</span></span>
<span data-ttu-id="a792f-103">Może być trudne znaleźć lokalizację i nazwę pliku klucza prywatnego skojarzonego z certyfikatem X.509 określonej w magazynie certyfikatów.</span><span class="sxs-lookup"><span data-stu-id="a792f-103">It can be difficult to find the location and name of the private key file associated with a specific X.509 certificate in the certificate store.</span></span> <span data-ttu-id="a792f-104">Narzędzie FindPrivateKey.exe ułatwia ten proces.</span><span class="sxs-lookup"><span data-stu-id="a792f-104">The FindPrivateKey.exe tool facilitates this process.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="a792f-105">FindPrivateKey to przykład, który musi być skompilowany przed ich użyciem.</span><span class="sxs-lookup"><span data-stu-id="a792f-105">FindPrivateKey is a sample that needs to be compiled prior to use.</span></span> <span data-ttu-id="a792f-106">Zobacz "Aby skompilować projekt FindPrivateKey" poniższą sekcję, aby uzyskać instrukcje na temat sposobu FindPrivateKey narzędzie kompilacji.</span><span class="sxs-lookup"><span data-stu-id="a792f-106">See the "To build the FindPrivateKey project" section below for instructions on how to build the FindPrivateKey tool.</span></span>  
  
 <span data-ttu-id="a792f-107">Certyfikaty X.509 są instalowane przez administratora lub dowolnego użytkownika na maszynie.</span><span class="sxs-lookup"><span data-stu-id="a792f-107">X.509 certificates are installed by an Administrator or any user in the machine.</span></span> <span data-ttu-id="a792f-108">Jednak certyfikat mogą być używane przez usługę uruchomiony przy użyciu innego konta (na przykład ASPNET na [!INCLUDE[wxp](../../../../includes/wxp-md.md)] lub konta usługi SIECIOWEJ na [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)]).</span><span class="sxs-lookup"><span data-stu-id="a792f-108">However the certificate may be accessed by a service running under a different account (for example, the ASPNET on [!INCLUDE[wxp](../../../../includes/wxp-md.md)] or the NETWORK SERVICE accounts on [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)]).</span></span>  
  
 <span data-ttu-id="a792f-109">To konto może nie mieć dostępu do pliku klucza prywatnego, ponieważ certyfikat nie został zainstalowany przez nią pierwotnie.</span><span class="sxs-lookup"><span data-stu-id="a792f-109">This account may not have access to the private key file because the certificate was not installed by it originally.</span></span> <span data-ttu-id="a792f-110">FindPrivateKey udostępnia lokalizację pliku klucza prywatnego danego certyfikatu X.509.</span><span class="sxs-lookup"><span data-stu-id="a792f-110">The FindPrivateKey tool gives you the location of a given X.509 Certificate's private key file.</span></span> <span data-ttu-id="a792f-111">Można dodać uprawnienia lub usunąć uprawnienia do tego pliku, znając lokalizację certyfikatów X.509 określonego pliku klucza prywatnego.</span><span class="sxs-lookup"><span data-stu-id="a792f-111">You can add permissions or remove permissions to this file once you know the location of the particular X.509 certificates' private key file.</span></span>  
  
 <span data-ttu-id="a792f-112">Przykłady, które korzystają z certyfikatów do zabezpieczenia narzędzie FindPrivateKey w pliku Setup.bat pliku.</span><span class="sxs-lookup"><span data-stu-id="a792f-112">The samples that use certificates for security use the FindPrivateKey tool in the Setup.bat file.</span></span> <span data-ttu-id="a792f-113">Po można odnaleźć pliku klucza prywatnego można użyć innych narzędzi, takich jak Cacls.exe, aby ustawić odpowiednie uprawnienia dostępu do pliku.</span><span class="sxs-lookup"><span data-stu-id="a792f-113">Once the private key file has been found you can use other tools such as Cacls.exe to set the appropriate access rights onto the file.</span></span>  
  
 <span data-ttu-id="a792f-114">Podczas uruchamiania [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] usługi przy użyciu konta użytkownika, takie jak hostowanie Samoobsługowe pliku wykonywalnego, upewnij się, że konto użytkownika ma dostęp tylko do odczytu do pliku.</span><span class="sxs-lookup"><span data-stu-id="a792f-114">When running a [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] service under a user account, such as a self-hosted executable, ensure that the user account has read-only access to the file.</span></span> <span data-ttu-id="a792f-115">Podczas uruchamiania [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] usługi w obszarze Internet Information Services (IIS) domyślne konta, które usługa będzie uruchamiana są ASPNET na [!INCLUDE[wxp](../../../../includes/wxp-md.md)] lub NETWORK SERVICE w [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)], które domyślnie nie mają dostępu do pliku klucza prywatnego.</span><span class="sxs-lookup"><span data-stu-id="a792f-115">When running a [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] service under Internet Information Services (IIS) the default accounts that the service runs under are the ASPNET on [!INCLUDE[wxp](../../../../includes/wxp-md.md)] or the NETWORK SERVICE on [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)], which by default do not have access to the private key file.</span></span>  
  
## <a name="examples"></a><span data-ttu-id="a792f-116">Przykłady</span><span class="sxs-lookup"><span data-stu-id="a792f-116">Examples</span></span>  
 <span data-ttu-id="a792f-117">Podczas uzyskiwania dostępu do certyfikatu, dla którego proces nie ma uprawnień odczytu, zobaczysz komunikat o wyjątku podobny do poniższego przykładu.</span><span class="sxs-lookup"><span data-stu-id="a792f-117">When accessing a certificate for which the process does not have read privilege, you see an exception message similar to the following example.</span></span>  
  
```  
System.ArgumentException was unhandled  
Message="The certificate 'CN=localhost' must have a private key that is capable of key exchange.  The process must have access rights for the private key."  
Source="System.ServiceModel"  
```  
  
 <span data-ttu-id="a792f-118">W takim przypadku należy użyć narzędzia FindPrivateKey można znaleźć pliku klucza prywatnego, a następnie ustaw dostępu dla procesu, czy usługa jest uruchomiona w obszarze odpowiedni.</span><span class="sxs-lookup"><span data-stu-id="a792f-118">When this occurs use the FindPrivateKey tool to find the private key file and then set the access right for the process that the service is running under.</span></span> <span data-ttu-id="a792f-119">Na przykład można to zrobić za pomocą narzędzia Cacls.exe jak pokazano w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="a792f-119">For example, this can be done with the Cacls.exe tool as shown in the following example.</span></span>  
  
```  
cacls.exe "C:\Documents and Settings\All Users\Application Data\Microsoft\Crypto\RSA\MachineKeys\8aeda5eb81555f14f8f9960745b5a40d_38f7de48-5ee9-452d-8a5a-92789d7110b1" /E /G "NETWORK SERVICE":R  
```  
  
#### <a name="to-build-the-findprivatekey-project"></a><span data-ttu-id="a792f-120">Aby skompilować projekt FindPrivateKey</span><span class="sxs-lookup"><span data-stu-id="a792f-120">To build the FindPrivateKey project</span></span>  
  
1.  <span data-ttu-id="a792f-121">Otwórz [!INCLUDE[fileExplorer](../../../../includes/fileexplorer-md.md)] i przejdź do podkatalogu specyficzne dla języka w obszarze na lokalizację katalogu, w którym zainstalowano próbki.</span><span class="sxs-lookup"><span data-stu-id="a792f-121">Open [!INCLUDE[fileExplorer](../../../../includes/fileexplorer-md.md)] and navigate to the language-specific subdirectory under the directory location where you installed the sample.</span></span>  
  
2.  <span data-ttu-id="a792f-122">Kliknij dwukrotnie ikonę pliku SLN, można otworzyć pliku w programie Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="a792f-122">Double-click the .sln file icon to open the file in Visual Studio.</span></span>  
  
3.  <span data-ttu-id="a792f-123">W **kompilacji** menu, wybierz opcję **Kompiluj ponownie rozwiązanie**.</span><span class="sxs-lookup"><span data-stu-id="a792f-123">In the **Build** menu, select **Rebuild Solution**.</span></span> <span data-ttu-id="a792f-124">Pliki programu klienta są przeznaczone do client\bin i pliki programu usługi są przeznaczone do service\bin.</span><span class="sxs-lookup"><span data-stu-id="a792f-124">The client program files are built to client\bin and the service program files are built to service\bin.</span></span>  
  
4.  <span data-ttu-id="a792f-125">Tworzenie rozwiązania generuje plik: FindPrivateKey.exe.</span><span class="sxs-lookup"><span data-stu-id="a792f-125">Building the solution generates the file: FindPrivateKey.exe.</span></span>  
  
## <a name="conventionscommand-line-entries"></a><span data-ttu-id="a792f-126">Konwencje — wpisy wiersza polecenia</span><span class="sxs-lookup"><span data-stu-id="a792f-126">Conventions—Command-Line Entries</span></span>  
 <span data-ttu-id="a792f-127">"[*opcji*]" reprezentuje opcjonalny zestaw parametrów.</span><span class="sxs-lookup"><span data-stu-id="a792f-127">"[*option*]" represents an optional set of parameters.</span></span>  
  
 <span data-ttu-id="a792f-128">"{*opcji*}" reprezentuje obowiązkowe zestaw parametrów.</span><span class="sxs-lookup"><span data-stu-id="a792f-128">"{*option*}" represents a mandatory set of parameters.</span></span>  
  
 <span data-ttu-id="a792f-129">"*opcja 1* &#124; *option2*"reprezentuje wybór między Ustawia opcje.</span><span class="sxs-lookup"><span data-stu-id="a792f-129">"*option1* &#124; *option2*" represents a choice between sets of options.</span></span>  
  
 <span data-ttu-id="a792f-130">"\<*wartość*>" reprezentuje należy podać wartość parametru.</span><span class="sxs-lookup"><span data-stu-id="a792f-130">"\<*value*>" represents a parameter value to be entered.</span></span>  
  
## <a name="usage"></a><span data-ttu-id="a792f-131">Użycie</span><span class="sxs-lookup"><span data-stu-id="a792f-131">Usage</span></span>  
  
```  
FindPrivateKey <storeName> <storeLocation> [{ {-n <subjectName>} | {-t <thumbprint>} } [-f | -d | -a]]  
```  
  
 <span data-ttu-id="a792f-132">Gdzie:</span><span class="sxs-lookup"><span data-stu-id="a792f-132">Where:</span></span>  
  
```  
       <subjectName> The subject name of the certificate  
       <thumbprint>  The thumbprint of the certificate (You can use the Certmgr.exe tool to find this)  
       -f            output file name only  
       -d            output directory only  
       -a            output absolute file name  
```  
  
 <span data-ttu-id="a792f-133">Jeśli nie określono żadnych parametrów w wierszu polecenia, zostanie wyświetlony ten tekst pomocy.</span><span class="sxs-lookup"><span data-stu-id="a792f-133">If no parameters are specified at the command prompt then this help text is displayed.</span></span>  
  
## <a name="examples"></a><span data-ttu-id="a792f-134">Przykłady</span><span class="sxs-lookup"><span data-stu-id="a792f-134">Examples</span></span>  
 <span data-ttu-id="a792f-135">W tym przykładzie znajdzie pliku certyfikatu z nazwą podmiotu "CN = host_lokalny", w magazynie osobistym z bieżącym CurrentUser Moje User.FindPrivateKey - n "CN = localhost".</span><span class="sxs-lookup"><span data-stu-id="a792f-135">This example finds the filename of the certificate with a subject name of "CN=localhost", in the Personal store of the Current User.FindPrivateKey My CurrentUser -n "CN=localhost".</span></span>  
  
 <span data-ttu-id="a792f-136">W tym przykładzie znajdzie pliku certyfikatu z nazwą podmiotu "CN = host_lokalny", w osobistych przechowywać bieżącego i dane wyjściowe pełną ścieżką.</span><span class="sxs-lookup"><span data-stu-id="a792f-136">This example finds the filename of the certificate with a subject name of "CN=localhost", in the Personal store of the Current and output the full directory path.</span></span>  
  
```  
User.FindPrivateKey My CurrentUser -n "CN=localhost" -a  
```  
  
 <span data-ttu-id="a792f-137">W tym przykładzie znajdzie nazwę certyfikatu z odciskiem palca "03 33 98 63 d0 47 e7 48 71 33 62 64 76 5c 4c 9d 42 1 d 6b 52", w magazynie osobistym komputera lokalnego.</span><span class="sxs-lookup"><span data-stu-id="a792f-137">This example finds the filename of the certificate with a thumbprint of "03 33 98 63 d0 47 e7 48 71 33 62 64 76 5c 4c 9d 42 1d 6b 52", in the Personal store of the Local Computer.</span></span>  
  
```  
FindPrivateKey My LocalMachine -t "03 33 98 63 d0 47 e7 48 71 33 62 64 76 5c 4c 9d 42 1d 6b 52" –c  
```  
  
## <a name="see-also"></a><span data-ttu-id="a792f-138">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="a792f-138">See Also</span></span>
