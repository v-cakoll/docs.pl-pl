---
title: Przykład FindPrivateKey — WCF
ms.date: 12/04/2017
helpviewer_keywords:
- FindPrivateKey
ms.assetid: 16b54116-0ceb-4413-af0c-753bb2a785a6
ms.openlocfilehash: 4ba4316489c1494da9421bea5c513e44c6eb50a7
ms.sourcegitcommit: 005980b14629dfc193ff6cdc040800bc75e0a5a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/14/2019
ms.locfileid: "70989884"
---
# <a name="findprivatekey-sample"></a>Przykład FindPrivateKey

Znalezienie lokalizacji i nazwy pliku klucza prywatnego skojarzonego z konkretnym certyfikatem X. 509 w magazynie certyfikatów może być trudne. Narzędzie FindPrivateKey. exe ułatwia ten proces.

> [!IMPORTANT]
> FindPrivateKey to przykład, który należy skompilować przed użyciem. Aby uzyskać instrukcje dotyczące sposobu kompilowania narzędzia FindPrivateKey, zobacz sekcję [Aby utworzyć projekt FindPrivateKey](#to-build-the-findprivatekey-project) .

Certyfikaty X. 509 są instalowane przez administratora lub dowolnego użytkownika na komputerze. Jednak dostęp do certyfikatu może uzyskać usługa działająca przy użyciu innego konta. Na przykład konto usługi sieciowej.

To konto może nie mieć dostępu do pliku klucza prywatnego, ponieważ certyfikat nie został pierwotnie zainstalowany. Narzędzie FindPrivateKey udostępnia lokalizację danego pliku klucza prywatnego certyfikatu X. 509. Możesz dodać uprawnienia lub usunąć uprawnienia do tego pliku, gdy znasz lokalizację określonego pliku klucza prywatnego certyfikatu X. 509.

Przykłady używające certyfikatów do zabezpieczeń używają narzędzia FindPrivateKey w pliku *Setup. bat* . Po znalezieniu pliku klucza prywatnego można użyć innych narzędzi, takich jak *cacls. exe* , aby ustawić odpowiednie prawa dostępu do pliku.

Podczas uruchamiania usługi Windows Communication Foundation (WCF) w ramach konta użytkownika, takiego jak samoobsługowy plik wykonywalny, upewnij się, że konto użytkownika ma dostęp tylko do odczytu do pliku. Podczas uruchamiania usługi WCF w obszarze Internet Information Services (IIS) domyślne konta, na których działa usługa, to usługa sieciowa w usługach IIS w wersji 7 lub starszej lub tożsamość puli aplikacji w usługach IIS 7,5 i nowszych. Aby uzyskać więcej informacji, zobacz [tożsamość puli aplikacji](/iis/manage/configuring-security/application-pool-identities).

## <a name="examples"></a>Przykłady

Podczas uzyskiwania dostępu do certyfikatu, dla którego proces nie ma uprawnień do odczytu, zobaczysz komunikat o wyjątku podobny do następującego:

```output
System.ArgumentException was unhandled
Message="The certificate 'CN=localhost' must have a private key that is capable of key exchange.  The process must have access rights for the private key."
Source="System.ServiceModel"
```

W takim przypadku należy użyć narzędzia FindPrivateKey, aby znaleźć plik klucza prywatnego, a następnie ustawić prawo dostępu dla procesu, w którym działa usługa. Można to zrobić na przykład za pomocą narzędzia Cacls. exe, jak pokazano w następującym przykładzie:

```console
cacls.exe "C:\Documents and Settings\All Users\Application Data\Microsoft\Crypto\RSA\MachineKeys\8aeda5eb81555f14f8f9960745b5a40d_38f7de48-5ee9-452d-8a5a-92789d7110b1" /E /G "NETWORK SERVICE":R
```

#### <a name="to-build-the-findprivatekey-project"></a>Aby skompilować projekt FindPrivateKey

Aby pobrać projekt, odwiedź [przykłady Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) dla .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459).

1. Otwórz Eksploratora plików i przejdź do folderu *WF_WCF_Samples\WCF\Setup\FindPrivateKey\CS* w lokalizacji katalogu, w której zainstalowano przykład.

2. Kliknij dwukrotnie ikonę pliku. sln, aby otworzyć plik w programie Visual Studio.

3. W menu **kompilacja** wybierz opcję **Kompiluj ponownie rozwiązanie**.

4. Kompilowanie rozwiązania spowoduje wygenerowanie pliku: FindPrivateKey.exe.

## <a name="conventionscommand-line-entries"></a>Konwencje — wpisy wiersza polecenia

 "[*opcja*]" reprezentuje opcjonalny zestaw parametrów.

 "{*Option*}" reprezentuje obowiązkowy zestaw parametrów.

 "*opcja1* &#124; *opcja2*" reprezentuje wybór między zestawami opcji.

 "\<*wartość*>" reprezentuje wartość parametru, która ma zostać wprowadzona.

## <a name="usage"></a>Użycie

```console
FindPrivateKey <storeName> <storeLocation> [{ {-n <subjectName>} | {-t <thumbprint>} } [-f | -d | -a]]
```

Gdzie:

| Parametr         | Opis                                                                       |
|-----------------|-----------------------------------------------------------------------------------|
| `<subjectName>` | Nazwa podmiotu certyfikatu                                               |
| `<thumbprint>`  | Odcisk palca certyfikatu (można go znaleźć za pomocą narzędzia certmgr. exe) |
| `-f`            | tylko nazwa pliku wyjściowego                                                             |
| `-d`            | tylko katalog wyjściowy                                                             |
| `-a`            | niepełna nazwa pliku wyjściowego                                                         |

Jeśli w wierszu polecenia nie określono żadnych parametrów, zostanie wyświetlony tekst pomocy z tymi informacjami.

## <a name="examples"></a>Przykłady

Ten przykład umożliwia znalezienie nazwy pliku certyfikatu z nazwą podmiotu "CN = localhost" w magazynie osobistym bieżącego użytkownika.

```console
FindPrivateKey My CurrentUser -n "CN=localhost"
```

Ten przykład umożliwia znalezienie nazwy pliku certyfikatu z nazwą podmiotu "CN = localhost" w magazynie osobistym bieżącego użytkownika i wyjściem pełnej ścieżki katalogu.

```console
FindPrivateKey My CurrentUser -n "CN=localhost" -a
```

W tym przykładzie znajduje się nazwa pliku certyfikatu z odciskiem palca "03 33 98 63 d0 47 E7 48 71 33 62 64 76 5c 4C 9d 42 1D 6B 52" w magazynie osobistym komputera lokalnego.

```console
FindPrivateKey My LocalMachine -t "03 33 98 63 d0 47 e7 48 71 33 62 64 76 5c 4c 9d 42 1d 6b 52"
```
