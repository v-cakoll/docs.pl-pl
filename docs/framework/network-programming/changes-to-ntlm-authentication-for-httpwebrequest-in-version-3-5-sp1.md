---
title: Zmiany w uwierzytelnianiu NTLM dla HttpWebRequest w wersji 3.5 z dodatkiem SP1
ms.date: 03/30/2017
ms.assetid: 8bf0b428-5a21-4299-8d6e-bf8251fd978a
ms.openlocfilehash: 0105cc762696c54a65cd06b3ffcb5fb4c8530a41
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59216720"
---
# <a name="changes-to-ntlm-authentication-for-httpwebrequest-in-version-35-sp1"></a>Zmiany w uwierzytelnianiu NTLM dla HttpWebRequest w wersji 3.5 z dodatkiem SP1
Zmiany zabezpieczeń zostały wprowadzone w .NET Framework w wersji 3.5 z dodatkiem SP1 i później, wpływają na Windows jak zintegrowane uwierzytelnianie jest obsługiwane przez <xref:System.Net.HttpWebRequest>, <xref:System.Net.HttpListener>, <xref:System.Net.Security.NegotiateStream>, i pokrewne klasy w przestrzeni nazw System.Net. Te zmiany mogą mieć wpływ na aplikacje, które używają tych klas do żądań sieci web i odbierania odpowiedzi, gdy jest używane zintegrowane uwierzytelnianie Windows oparte na NTLM. Ta zmiana może wpłynąć na serwerach sieci web i aplikacji klienckich, które są skonfigurowane do korzystania ze zintegrowanego uwierzytelniania Windows.  
  
## <a name="overview"></a>Omówienie  
 Projekt zintegrowane uwierzytelnianie Windows umożliwia pewne odpowiedzi poświadczeń jako uniwersalny, co oznacza, mogą być ponownie używane lub przesyłane dalej. Jeśli ta funkcja konkretnego projektu nie jest wymagana, protokoły uwierzytelniania powinien mieć docelowy szczegółowe informacje, a także informacje określonego kanału. Usługi mogą udzielić im ochrona rozszerzona, aby upewnić się, że poświadczenie odpowiedzi zawiera usługi szczegółowe informacje, takie jak nazwy głównej nazwy usługi (SPN). Dzięki tym informacjom wymianę poświadczeń usługi mają możliwość zapewnienia lepszej ochrony przed złośliwym korzystaniem z odpowiedzi na poświadczenie, które może być nieprawidłowo uzyskany.  
  
 Wiele składników w <xref:System.Net> i <xref:System.Net.Security> przestrzenie nazw wykonać zintegrowane uwierzytelnianie Windows w imieniu aplikacji wywołującej. W tej sekcji opisano zmiany w przestrzeni nazw System.Net składników można dodawać ochronę rozszerzoną ich używane zintegrowane uwierzytelnianie Windows.  
  
## <a name="changes"></a>Zmiany  
 Proces uwierzytelniania NTLM, które są używane z uwierzytelnianiem zintegrowanym Windows zawiera żądanie wystawiony przez komputer docelowy i wysyłane z powrotem do komputera klienckiego. Gdy komputer otrzyma wezwanie on sam wygenerowany, uwierzytelnianie zakończy się niepowodzeniem, chyba że połączenie jest pętlą Wstecz (adres IPv4 127.0.0.1, na przykład).  
  
 Podczas uzyskiwania dostępu do usługi uruchomionej na wewnętrznym serwerze sieci Web, są często uzyskać dostępu do usługi przy użyciu adresu URL, które są podobne do `http://contoso/service` lub `https://contoso/service`. Nazwy "contoso" nie jest często nazwę komputera komputera, na którym została wdrożona usługa. <xref:System.Net> Pokrewne obszary nazw obsługi za pomocą protokołu NetBIOS usługi Active Directory, DNS, hosty komputera lokalnego pliku (zazwyczaj WINDOWS\system32\drivers\etc\hosts, na przykład) lub lmhosts komputera lokalnego pliku (zazwyczaj WINDOWS\system32\ drivers\etc\lmhosts, na przykład) do rozpoznawania nazw na adresy. Nazwy "contoso" zostanie rozwiązany, tak aby żądania wysyłane na "contoso" są wysyłane do odpowiedniego serwera.  
  
 W przypadku skonfigurowania w przypadku dużych wdrożeń, jest również typowe dla nazwy pojedynczego serwera wirtualnego, należy podać do wdrożenia z podstawowej nazwy maszyn nigdy używane przez aplikacje klienckie i użytkowników końcowych. Na przykład może wywołać serwera `www.contoso.com`, ale w wewnętrznej sieci po prostu użyć "contoso". Ta nazwa nosi nazwę nagłówka hosta w żądaniu klienta sieci web. Określone przez protokół HTTP pole Host w nagłówku żądania określa Internetu hosta i portu numer żądanych zasobów. Te informacje są uzyskiwane z oryginalnego identyfikatora URI, podane przez użytkownika lub odwołuje się do innych zasobów (zwykle adres HTTP URL). W programie .NET Framework w wersji 4, te informacje można również ustawić przez klienta za pomocą nowego <xref:System.Net.HttpWebRequest.Host%2A> właściwości.  
  
 <xref:System.Net.AuthenticationManager> Klasy kontrolki składników zarządzanych uwierzytelniania ("moduły"), które są używane przez <xref:System.Net.WebRequest> klas pochodnych i <xref:System.Net.WebClient> klasy. <xref:System.Net.AuthenticationManager> Klasy zawiera właściwości, która udostępnia <xref:System.Net.AuthenticationManager.CustomTargetNameDictionary%2A?displayProperty=nameWithType> obiektu indeksowane przez ciąg identyfikatora URI, dla aplikacji, aby podać niestandardowy ciąg nazwy SPN, który ma być używany podczas uwierzytelniania.  
  
 W wersji 3.5 z dodatkiem SP1, teraz używane wartości domyślne do określania nazwy hosta w adresie URL żądania w głównej nazwy usługi w uwierzytelnianiu NTLM (NT LAN Manager) programu exchange, kiedy <xref:System.Net.AuthenticationManager.CustomTargetNameDictionary%2A> nie ustawiono właściwości. Nazwa hosta używana w adresie URL żądania może różnić się od nagłówka hosta określona w <xref:System.Net.HttpRequestHeader?displayProperty=nameWithType> w żądaniu klienta. Nazwa hosta używana w adresie URL żądania może różnić się od aktualną nazwą hosta serwera, nazwę komputera serwera, adres IP tego komputera lub adres sprzężenia zwrotnego. W takich przypadkach Windows zakończy się niepowodzeniem żądania uwierzytelniania. Aby rozwiązać ten problem, musimy powiadomić Windows, nazwa hosta używana w adresie URL żądania w kliencie żądania ("contoso", na przykład) jest faktycznie alternatywną nazwę komputera lokalnego.  
  
 Istnieje kilka możliwych metod dla aplikacji serwera obejść tę zmianę. Zalecanym podejściem jest mapowanie nazwy hosta, używany w adresie URL żądania, aby `BackConnectionHostNames` klucza w rejestrze na serwerze. `BackConnectionHostNames` Klucz rejestru zwykle są używane do mapowania nazwy hosta na adres sprzężenia zwrotnego. Poniżej przedstawiono kroki.  
  
 Aby określić nazwy hostów, które są mapowane na adres sprzężenia zwrotnego i można połączyć się z witryny sieci Web na komputerze lokalnym, wykonaj następujące kroki:  
  
 1. Kliknij przycisk Start, kliknij przycisk Uruchom, wpisz wyrażenie regedit i kliknij przycisk OK.  
  
 2. W Edytorze rejestru Znajdź, a następnie kliknij przycisk następujący klucz rejestru:  
  
 `HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Control\Lsa\MSV1_0`  
  
 3. Kliknij prawym przyciskiem myszy MSV1_0, wskaż polecenie Nowy, a następnie kliknij wartość ciągu wielokrotnego.  
  
 4. Typ `BackConnectionHostNames`, a następnie naciśnij klawisz ENTER.  
  
 5. Kliknij prawym przyciskiem myszy `BackConnectionHostNames`, a następnie kliknij polecenie Modyfikuj.  
  
 6. W polu dane wartości wpisz nazwę hosta lub nazwy hostów dla witryny (nazwa hosta używany w adresie URL żądania), które znajdują się na komputerze lokalnym, a następnie kliknij przycisk OK.  
  
 7. Zamknij Edytor rejestru, a następnie ponownie uruchom usługę IISAdmin i uruchom polecenie IISReset.  
  
 Mniej bezpieczna opcja pracy około jest wyłączenie sprawdzania wstecz pętli, zgodnie z opisem w <https://support.microsoft.com/kb/896861>. Powoduje to wyłączenie ochrony przed atakami odbicia. Dlatego lepiej jest ograniczyć zestaw alternatywnych nazw tylko te, które oczekują maszynę aby rzeczywiście używane.  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Net.AuthenticationManager.CustomTargetNameDictionary%2A?displayProperty=nameWithType>
- <xref:System.Net.HttpRequestHeader?displayProperty=nameWithType>
- <xref:System.Net.HttpWebRequest.Host%2A?displayProperty=nameWithType>
