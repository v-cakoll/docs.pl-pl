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
# <a name="findprivatekey-sample"></a>Przykładowe FindPrivateKey

Może być trudne znaleźć lokalizację i nazwę pliku klucza prywatnego skojarzonego z certyfikatem X.509 określonej w magazynie certyfikatów. Narzędzie FindPrivateKey.exe ułatwia ten proces.

> [!IMPORTANT]
> FindPrivateKey to przykład, który musi być skompilowany przed ich użyciem. Zobacz [Aby skompilować projekt FindPrivateKey](#to-build-the-findprivatekey-project) sekcji, aby uzyskać instrukcje dotyczące sposobu tworzenia narzędzia FindPrivateKey.

Certyfikaty X.509 są instalowane przez administratora lub dowolnego użytkownika na maszynie. Jednak certyfikat mogą być używane przez usługę uruchomiony przy użyciu innego konta. Na przykład konto Usługa sieciowa.

To konto może nie mieć dostępu do pliku klucza prywatnego, ponieważ certyfikat nie został zainstalowany przez nią pierwotnie. FindPrivateKey udostępnia lokalizację pliku klucza prywatnego danego certyfikatu X.509. Można dodać uprawnienia lub usunąć uprawnienia do tego pliku, znając lokalizację certyfikatów X.509 określonego pliku klucza prywatnego.

Przykłady, które korzystają z certyfikatów do zabezpieczenia za pomocą narzędzia FindPrivateKey w *pliku Setup.bat* pliku. Po znalezieniu pliku klucza prywatnego można użyć innych narzędzi takich jak *Cacls.exe* można ustawić odpowiednie uprawnienia dostępu do pliku.

Podczas uruchamiania usługi Windows Communication Foundation (WCF) przy użyciu konta użytkownika, takie jak hostowanie Samoobsługowe pliku wykonywalnego, upewnij się, że konto użytkownika ma dostęp tylko do odczytu do pliku. Podczas uruchamiania usługi WCF w obszarze usługi Internet Information Services (IIS) domyślne konta, które usługa będzie uruchamiana to usługa sieciowa w usługach IIS 7 i wcześniejsze wersje lub tożsamość puli aplikacji usług IIS 7.5 i nowsze wersje. Aby uzyskać więcej informacji, zobacz [tożsamości puli aplikacji](/iis/manage/configuring-security/application-pool-identities).

## <a name="examples"></a>Przykłady

Podczas uzyskiwania dostępu do certyfikatu, dla którego proces nie ma uprawnień odczytu, zobaczysz komunikat o wyjątku podobny do poniższego przykładu:

```
System.ArgumentException was unhandled
Message="The certificate 'CN=localhost' must have a private key that is capable of key exchange.  The process must have access rights for the private key."
Source="System.ServiceModel"
```

W takim przypadku służy narzędzie FindPrivateKey można znaleźć pliku klucza prywatnego, a następnie ustaw dostępu prawa dla procesu, czy usługa jest uruchomiona w obszarze. Na przykład można to zrobić za pomocą narzędzia Cacls.exe jak pokazano w poniższym przykładzie:

```
cacls.exe "C:\Documents and Settings\All Users\Application Data\Microsoft\Crypto\RSA\MachineKeys\8aeda5eb81555f14f8f9960745b5a40d_38f7de48-5ee9-452d-8a5a-92789d7110b1" /E /G "NETWORK SERVICE":R
```

#### <a name="to-build-the-findprivatekey-project"></a>Aby skompilować projekt FindPrivateKey

Aby pobrać projekt, odwiedź stronę [Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) przykłady dla programu .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459).

1. Otwórz [!INCLUDE[fileExplorer](../../../../includes/fileexplorer-md.md)] i przejdź do *WF_WCF_Samples\WCF\Setup\FindPrivateKey\CS* folder na lokalizację katalogu, w którym zainstalowano próbki.

2. Kliknij dwukrotnie ikonę pliku SLN, można otworzyć pliku w programie Visual Studio.

3. W **kompilacji** menu, wybierz opcję **Kompiluj ponownie rozwiązanie**.

4. Tworzenie rozwiązania generuje plik: FindPrivateKey.exe.

## <a name="conventionscommand-line-entries"></a>Konwencje — wpisy wiersza polecenia

 "[*opcji*]" reprezentuje opcjonalny zestaw parametrów.

 "{*opcji*}" reprezentuje obowiązkowe zestaw parametrów.

 "*opcja 1* &#124; *option2*"reprezentuje wybór między Ustawia opcje.

 "\<*wartość*>" reprezentuje należy podać wartość parametru.

## <a name="usage"></a>Użycie

```
FindPrivateKey <storeName> <storeLocation> [{ {-n <subjectName>} | {-t <thumbprint>} } [-f | -d | -a]]
```

Gdzie:

```
       <subjectName> The subject name of the certificate
       <thumbprint>  The thumbprint of the certificate (You can use the Certmgr.exe tool to find this)
       -f            output file name only
       -d            output directory only
       -a            output absolute file name
```

Jeśli nie zostały podane parametry w wierszu polecenia, wyświetlany jest ten tekst pomocy.

## <a name="examples"></a>Przykłady

W tym przykładzie znajdzie pliku certyfikatu z nazwą podmiotu "CN = host_lokalny", w magazynie osobistym bieżącego użytkownika.

```
FindPrivateKey My CurrentUser -n "CN=localhost"
```

W tym przykładzie znajdzie pliku certyfikatu z nazwą podmiotu "CN = host_lokalny", w osobistych przechowywać bieżącego użytkownika i dane wyjściowe pełną ścieżką.

```
FindPrivateKey My CurrentUser -n "CN=localhost" -a
```

W tym przykładzie znajdzie nazwę certyfikatu z odciskiem palca "03 33 98 63 d0 47 e7 48 71 33 62 64 76 5c 4c 9d 42 1 d 6b 52", w magazynie osobistym komputera lokalnego.

```
FindPrivateKey My LocalMachine -t "03 33 98 63 d0 47 e7 48 71 33 62 64 76 5c 4c 9d 42 1d 6b 52"
```
