---
title: Zmiany w uwierzytelnianiu NTLM dla HttpWebRequest w wersji 3.5 z dodatkiem SP1
ms.date: 03/30/2017
ms.assetid: 8bf0b428-5a21-4299-8d6e-bf8251fd978a
ms.openlocfilehash: 388e6dc648e1fd68e24a852cb08de107f09f9c9f
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "64754880"
---
# <a name="changes-to-ntlm-authentication-for-httpwebrequest-in-version-35-sp1"></a>Zmiany w uwierzytelnianiu NTLM dla HttpWebRequest w wersji 3.5 z dodatkiem SP1

W programie .NET Framework w wersji 3.5 z dodatku SP1 i <xref:System.Net.HttpWebRequest>nowszych wprowadzono zmiany zabezpieczeń, które wpływają na sposób obsługi zintegrowanego uwierzytelniania systemu Windows przez programy ,, <xref:System.Net.HttpListener> <xref:System.Net.Security.NegotiateStream>i powiązane klasy w System.Net obszarze nazw. Te zmiany mogą mieć wpływ na aplikacje, które używają tych klas do tworzenia żądań sieci web i odbierania odpowiedzi, w których używane jest zintegrowane uwierzytelnianie systemu Windows oparte na NTLM. Ta zmiana może mieć wpływ na serwery sieci Web i aplikacje klienckie skonfigurowane do używania zintegrowanego uwierzytelniania systemu Windows.

## <a name="overview"></a>Omówienie

Projekt zintegrowanego uwierzytelniania systemu Windows pozwala na niektóre odpowiedzi poświadczeń, które mają być uniwersalne, co oznacza, że mogą być ponownie używane lub przekazywane dalej. Jeśli ta określona funkcja projektowania nie jest potrzebna, protokoły uwierzytelniania powinny zawierać określone informacje o obiektach docelowych, a także informacje specyficzne dla kanału. Usługi mogą następnie zapewnić rozszerzoną ochronę, aby upewnić się, że odpowiedzi na poświadczenia zawierają informacje specyficzne dla usługi, takie jak nazwa główna usługi (SPN). Dzięki tym informacjom w wymianie poświadczeń usługi są w stanie lepiej chronić przed złośliwym użyciem odpowiedzi poświadczeń, które mogły zostać uzyskane nieprawidłowo.

Wiele składników <xref:System.Net> w <xref:System.Net.Security> przestrzeniach nazw i obszarach nazw wykonuje zintegrowane uwierzytelnianie systemu Windows w imieniu aplikacji wywołującej. W tej sekcji opisano zmiany składników System.Net, aby dodać rozszerzoną ochronę podczas korzystania ze zintegrowanego uwierzytelniania systemu Windows.

## <a name="changes"></a>Zmiany

Proces uwierzytelniania NTLM używany ze zintegrowanym uwierzytelnianiem systemu Windows obejmuje wyzwanie wydane przez komputer docelowy i odesłane z powrotem do komputera klienckiego. Gdy komputer odbiera wyzwanie, które sam wygenerował, uwierzytelnianie zakończy się niepowodzeniem, chyba że połączenie jest połączeniem zwrotnym pętli (na przykład adres IPv4 127.0.0.1).

Podczas uzyskiwania dostępu do usługi uruchomionej na wewnętrznym serwerze sieci Web `http://contoso/service` `https://contoso/service`często uzyskuje się dostęp do usługi przy użyciu adresu URL podobnego do lub . Nazwa "contoso" często nie jest nazwą komputera, na którym jest wdrażana usługa. Obsługa <xref:System.Net> i powiązane obszary nazw przy użyciu usługi Active Directory, DNS, NetBIOS, pliku hosts komputera lokalnego (na przykład windows\system32\drivers\etc\hosts) lub pliku lmhosts komputera lokalnego (zazwyczaj windows\system32\drivers\etc\lmhosts, na przykład) w celu rozpoznawania nazw adresów. Nazwa "contoso" jest rozpoznawana, tak aby żądania wysyłane do "contoso" były wysyłane do odpowiedniego komputera serwera.

Po skonfigurowaniu dla dużych wdrożeń jest również wspólne dla pojedynczego serwera wirtualnego nazwa, które mają być podane do wdrożenia z podstawowych nazw komputerów nigdy nie używane przez aplikacje klienckie i użytkowników końcowych. Na przykład można wywołać `www.contoso.com`serwer , ale w sieci wewnętrznej po prostu użyć "contoso". Ta nazwa jest nazywana nagłówkiem hosta w żądaniu sieci web klienta. Zgodnie z protokołem HTTP pole Nagłówek żądania hosta określa hosta internetowego i numer portu żądanego zasobu. Te informacje są uzyskiwane z oryginalnego identyfikatora URI podanego przez użytkownika lub zasobu odsyłającego (zazwyczaj adresu URL HTTP). W programie .NET Framework w wersji 4 te informacje <xref:System.Net.HttpWebRequest.Host%2A> mogą być również ustawiane przez klienta przy użyciu nowej właściwości.

Klasa <xref:System.Net.AuthenticationManager> steruje zarządzanych składników uwierzytelniania ("moduły"), które są używane przez <xref:System.Net.WebRequest> klasy pochodne <xref:System.Net.WebClient> i klasy. Klasa <xref:System.Net.AuthenticationManager> udostępnia właściwość, która <xref:System.Net.AuthenticationManager.CustomTargetNameDictionary%2A?displayProperty=nameWithType> udostępnia obiekt, indeksowane przez ciąg URI, dla aplikacji do dostarczania niestandardowego ciągu SPN, który ma być używany podczas uwierzytelniania.

Wersja 3.5 SP1 teraz domyślnie określa nazwę hosta używanego w adresie URL żądania w spn <xref:System.Net.AuthenticationManager.CustomTargetNameDictionary%2A> w NTLM (NT LAN Manager) wymiany uwierzytelniania, gdy właściwość nie jest ustawiona. Nazwa hosta używana w adresie URL żądania może <xref:System.Net.HttpRequestHeader?displayProperty=nameWithType> się różnić od nagłówka hosta określonego w żądaniu klienta. Nazwa hosta używana w adresie URL żądania może różnić się od rzeczywistej nazwy hosta serwera, nazwy komputera serwera, adresu IP komputera lub adresu sprzężenia zwrotnego. W takich przypadkach system Windows zakończy się niepowodzeniem żądania uwierzytelniania. Aby rozwiązać ten problem, musimy powiadomić system Windows, że nazwa hosta używana w adresie URL żądania w żądaniu klienta ("contoso", na przykład) jest w rzeczywistości alternatywną nazwą komputera lokalnego.

Istnieje kilka możliwych metod dla aplikacji serwera, aby obejść tę zmianę. Zalecane podejście jest mapowanie nazwy hosta używane `BackConnectionHostNames` w adresie URL żądania do klucza w rejestrze na serwerze. Klucz `BackConnectionHostNames` rejestru jest zwykle używany do mapowania nazwy hosta na adres sprzężenia zwrotnego. Kroki są wymienione poniżej.

Aby określić nazwy hostów mapowane na adres sprzężenia zwrotnego i mogą łączyć się z witrynami sieci Web na komputerze lokalnym, wykonaj następujące kroki:

1. Kliknij przycisk Start, kliknij pozycję Uruchom, wpisz polecenie regedit, a następnie kliknij przycisk OK.

2. W Edytorze rejestru znajdź, a następnie kliknij następujący klucz rejestru:

    `HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Control\Lsa\MSV1_0`

3. Kliknij prawym przyciskiem myszy MSV1_0, wskaż polecenie Nowy, a następnie kliknij polecenie Wartość wielostrunowa.

4. Wpisz `BackConnectionHostNames`, a następnie naciśnij klawisz ENTER.

5. Kliknij prawym `BackConnectionHostNames`przyciskiem myszy , a następnie kliknij polecenie Modyfikuj.

6. W polu Dane wartości wpisz nazwę hosta lub nazwy hosta witryn (nazwę hosta używaną w adresie URL żądania), które znajdują się na komputerze lokalnym, a następnie kliknij przycisk OK.

7. Zamknij Edytor rejestru, a następnie uruchom ponownie usługę IISAdmin i uruchom usługę IISReset.

Mniej bezpieczne obejście jest wyłączenie sprawdzania pętli z <https://support.microsoft.com/kb/896861>powrotem, jak opisano w . Spowoduje to wyłączenie ochrony przed atakami odbicia. Dlatego lepiej jest ograniczyć zestaw alternatywnych nazw tylko do tych, których oczekujesz, że maszyna będzie faktycznie używana.

## <a name="see-also"></a>Zobacz też

- <xref:System.Net.AuthenticationManager.CustomTargetNameDictionary%2A?displayProperty=nameWithType>
- <xref:System.Net.HttpRequestHeader?displayProperty=nameWithType>
- <xref:System.Net.HttpWebRequest.Host%2A?displayProperty=nameWithType>
