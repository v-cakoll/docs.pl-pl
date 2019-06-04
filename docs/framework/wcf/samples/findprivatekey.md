---
title: Przykładowy FindPrivateKey — WCF
ms.date: 12/04/2017
helpviewer_keywords:
- FindPrivateKey
ms.assetid: 16b54116-0ceb-4413-af0c-753bb2a785a6
ms.openlocfilehash: b89d135d7412f10cb9de1e4bda1aaab14b29cbf0
ms.sourcegitcommit: 155012a8a826ee8ab6aa49b1b3a3b532e7b7d9bd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2019
ms.locfileid: "66490769"
---
# <a name="findprivatekey-sample"></a>Przykładowe FindPrivateKey

Może być trudne do znalezienia lokalizację i nazwę pliku klucza prywatnego skojarzonego z certyfikatem X.509 określonych w magazynie certyfikatów. Narzędzie FindPrivateKey.exe ułatwia ten proces.

> [!IMPORTANT]
> FindPrivateKey znajduje się przykładowy, który ma zostać skompilowany przed ich użyciem. Zobacz [do skompilowania projektu FindPrivateKey](#to-build-the-findprivatekey-project) sekcję, aby uzyskać instrukcje dotyczące sposobu narzędzie FindPrivateKey kompilacji.

Certyfikaty X.509 są instalowane przez administratora lub każdego użytkownika na maszynie. Jednak certyfikat może zostać oceniony przez Usługa uruchomiona przy użyciu innego konta. Na przykład konto Usługa sieciowa.

To konto może nie mieć dostępu do pliku klucza prywatnego, ponieważ certyfikat nie został zainstalowany przez niego pierwotnie. Narzędzie FindPrivateKey zapewnia lokalizacji pliku klucza prywatnego danego certyfikatu X.509. Można dodać uprawnienia lub usunąć uprawnienia do tego pliku, po znać lokalizację pliku klucza prywatnego określonego certyfikaty X.509.

Przykłady, które korzystają z certyfikatów do zabezpieczenia przy użyciu narzędzia FindPrivateKey w *Setup.bat* pliku. Po znalezieniu pliku klucza prywatnego można użyć innych narzędzi, takich jak *Cacls.exe* można ustawić odpowiednie uprawnienia dostępu do pliku.

Podczas uruchamiania usługi Windows Communication Foundation (WCF) w ramach konta użytkownika, takie jak własnego pliku wykonywalnego, upewnij się, że konto użytkownika ma dostęp tylko do odczytu do pliku. Podczas uruchamiania usługi WCF w ramach usługi Internet Information Services (IIS) domyślnych kont, które usługa będzie uruchamiana to usługa sieciowa w usługach IIS 7 i starszych wersji lub tożsamość puli aplikacji usług IIS 7.5 i nowsze wersje. Aby uzyskać więcej informacji, zobacz [tożsamości puli aplikacji](/iis/manage/configuring-security/application-pool-identities).

## <a name="examples"></a>Przykłady

Podczas uzyskiwania dostępu do certyfikatu, dla którego ten proces nie ma uprawnień odczytu, zostanie wyświetlony komunikat wyjątku, które jest podobny do poniższego przykładu:

```
System.ArgumentException was unhandled
Message="The certificate 'CN=localhost' must have a private key that is capable of key exchange.  The process must have access rights for the private key."
Source="System.ServiceModel"
```

W takiej sytuacji narzędzie FindPrivateKey można znaleźć pliku klucza prywatnego, a następnie ustaw dostęp bezpośrednio do procesu, który jest uruchamiany przez usługę. Na przykład można to zrobić za pomocą narzędzia Cacls.exe jak pokazano w poniższym przykładzie:

```
cacls.exe "C:\Documents and Settings\All Users\Application Data\Microsoft\Crypto\RSA\MachineKeys\8aeda5eb81555f14f8f9960745b5a40d_38f7de48-5ee9-452d-8a5a-92789d7110b1" /E /G "NETWORK SERVICE":R
```

#### <a name="to-build-the-findprivatekey-project"></a>Aby skompilować projekt FindPrivateKey

Aby pobrać projektu, odwiedź stronę [Windows Communication Foundation (WCF) i przykłady Windows Workflow Foundation (WF) dla platformy .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459).

1. Otwórz Eksplorator plików i przejdź do *WF_WCF_Samples\WCF\Setup\FindPrivateKey\CS* folderze lokalizację katalogu, w którym zainstalowano próbki.

2. Kliknij dwukrotnie ikonę pliku .sln, aby otworzyć go w programie Visual Studio.

3. W **kompilacji** menu, wybierz opcję **Kompiluj rozwiązanie**.

4. Skompilować rozwiązanie generuje plik: FindPrivateKey.exe.

## <a name="conventionscommand-line-entries"></a>Konwencje — wpisy wiersza polecenia

 "[*opcji*]" reprezentuje opcjonalny zestaw parametrów.

 "{*opcji*}" reprezentuje zestaw parametrów obowiązkowych.

 "*opcja1* &#124; *opcja2*" reprezentuje wybór między zestawami opcji.

 "\<*wartość*>" reprezentuje wartość parametru, który ma zostać nawiązane.

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

Jeśli nie określono żadnych parametrów w wierszu polecenia, wyświetlany jest ten tekst pomocy.

## <a name="examples"></a>Przykłady

W tym przykładzie wyszukuje nazwy pliku certyfikatu, z nazwą podmiotu "CN = localhost", w magazynie osobistym bieżącego użytkownika.

```
FindPrivateKey My CurrentUser -n "CN=localhost"
```

W tym przykładzie wyszukuje nazwy pliku certyfikatu, z nazwą podmiotu "CN = localhost", należy w osobistego przechowywać bieżącego użytkownika i danych wyjściowych pełną ścieżką.

```
FindPrivateKey My CurrentUser -n "CN=localhost" -a
```

W tym przykładzie wyszukuje nazwę pliku certyfikatu z odciskiem palca "03 33 98 63 d0 47 e7 48 71 33 62 64 76 5c 4c 9d 42, 1 d 6b 52", w magazynie osobistym komputera lokalnego.

```
FindPrivateKey My LocalMachine -t "03 33 98 63 d0 47 e7 48 71 33 62 64 76 5c 4c 9d 42 1d 6b 52"
```
