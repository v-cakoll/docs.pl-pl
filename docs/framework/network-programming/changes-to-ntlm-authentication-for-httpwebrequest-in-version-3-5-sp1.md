---
title: Zmiany do uwierzytelniania NTLM dla HttpWebRequest w wersji 3.5 z dodatkiem SP1
ms.date: 03/30/2017
ms.assetid: 8bf0b428-5a21-4299-8d6e-bf8251fd978a
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: f5affc15607ddae76ec90a90928cb42fa0ad49e1
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="changes-to-ntlm-authentication-for-httpwebrequest-in-version-35-sp1"></a>Zmiany do uwierzytelniania NTLM dla HttpWebRequest w wersji 3.5 z dodatkiem SP1
Wprowadzono zmiany zabezpieczeń w .NET Framework w wersji 3.5 z dodatkiem SP1 i później który mają wpływ na sposób zintegrowane z systemem Windows uwierzytelnianie jest obsługiwane przez <xref:System.Net.HttpWebRequest>, <xref:System.Net.HttpListener>, <xref:System.Net.Security.NegotiateStream>, i powiązanych klas w przestrzeni nazw System.Net. Te zmiany mogą wpłynąć na aplikacji, które używają tych klas do żądań sieci web i odbierania odpowiedzi, gdzie jest używane zintegrowane uwierzytelnianie systemu Windows oparte na NTLM. Ta zmiana może wpłynąć na serwerach sieci web i aplikacji klienckich, które są skonfigurowane do korzystania ze zintegrowanego uwierzytelniania systemu Windows.  
  
## <a name="overview"></a>Omówienie  
 Projekt zintegrowane uwierzytelnianie systemu Windows umożliwia niektóre odpowiedzi poświadczeń jako uniwersalny, czyli może być ponownie używane lub przesyłane dalej. Jeśli ta funkcja konkretnego projektu nie jest niezbędna, protokoły uwierzytelniania powinien mieć określonych informacji o docelowej, a także kanału określone informacje. Usługi mogą udzielić im ochrona rozszerzona, aby upewnić się, że poświadczenia odpowiedzi zawiera usługi określone informacje takie jak nazwy usługi (SPN). Dzięki tym informacjom wymiany poświadczeń usługi będą mogli lepszej ochrony przed złośliwym korzystaniem z odpowiedzi poświadczeń, które może być nieprawidłowo uzyskany.  
  
 Wiele składników w <xref:System.Net> i <xref:System.Net.Security> przestrzenie nazw wykonać zintegrowane uwierzytelnianie systemu Windows w imieniu aplikacji wywołującej. W tej sekcji opisano zmiany System.Net składników, aby dodać ochrona rozszerzona w ich używania zintegrowanego uwierzytelniania systemu Windows.  
  
## <a name="changes"></a>Zmiany  
 Proces uwierzytelniania NTLM, które są używane z zintegrowane uwierzytelnianie systemu Windows zawiera żądanie wystawiony przez komputer docelowy, a następnie wysyłane z powrotem do komputera klienckiego. Gdy komputer odbierze żądanie jego samego wygenerowanych, uwierzytelnianie zakończy się niepowodzeniem, chyba że połączenie jest połączeniem wstecz pętli (adres IPv4 127.0.0.1, na przykład).  
  
 Podczas uzyskiwania dostępu do usługi uruchomionej na wewnętrznym serwerze sieci Web, jest często uzyskać dostęp do usługi przy użyciu adresu URL podobny do http://contoso/service lub https://contoso/service. Nazwa "contoso" nie jest często nazwę komputera komputera, na którym wdrożono usługę. <xref:System.Net> Obsługuje powiązane przestrzenie nazw przy użyciu usługi Active Directory, DNS, protokołu NetBIOS, (zazwyczaj WINDOWS\system32\drivers\etc\hosts, na przykład) pliku hosts na komputerze lokalnym lub (zazwyczaj WINDOWS\system32\ pliku lmhosts komputera lokalnego drivers\etc\lmhosts, na przykład) do rozpoznawania nazw na adresy. Nazwa "contoso" zostanie rozwiązany, dzięki czemu żądania wysyłane na "contoso" są wysyłane do odpowiedniego serwera.  
  
 W przypadku skonfigurowania w przypadku dużych wdrożeń, również jest typowe dla pojedynczego serwera wirtualnego nazwę do wdrożenia z podstawowej nazwy komputerów nigdy używane przez aplikacje klienckie i użytkowników końcowych. Na przykład wywołać www.contoso.com serwera, ale w sieci wewnętrznej po prostu użyć "contoso". Ta nazwa jest wywoływana nagłówek hosta w żądaniu klienta sieci web. Określone przez protokół HTTP pole nagłówka żądania Host Określa numer hosta i portu Internet żądanych zasobów. Te informacje są uzyskiwane z oryginalnego identyfikatora URI podane przez użytkownika lub odwołuje się do innych zasobów (zwykle adres HTTP URL). W środowisku .NET Framework w wersji 4, informacje te można również ustawić przez klienta przy użyciu nowego <xref:System.Net.HttpWebRequest.Host%2A> właściwości.  
  
 <xref:System.Net.AuthenticationManager> Klasa steruje składniki uwierzytelniania zarządzanego ("moduły"), które są używane przez <xref:System.Net.WebRequest> klas pochodnych i <xref:System.Net.WebClient> klasy. <xref:System.Net.AuthenticationManager> Klasa udostępnia właściwości, która przedstawia <xref:System.Net.AuthenticationManager.CustomTargetNameDictionary%2A?displayProperty=nameWithType> obiektu indeksowane według ciągu identyfikatora URI dla aplikacji, aby podać niestandardowy ciąg głównej nazwy usługi, który ma być używany podczas uwierzytelniania.  
  
 W wersji 3.5 z dodatkiem SP1, teraz używane wartości domyślne, aby określić nazwę hosta w adresie URL żądania w SPN w uwierzytelnianiu NTLM (NT LAN Manager) programu exchange, kiedy <xref:System.Net.AuthenticationManager.CustomTargetNameDictionary%2A> nie ustawiono właściwości. Nazwa hosta używaną w adresie URL żądania mogą być inne niż określony w nagłówek hosta <xref:System.Net.HttpRequestHeader?displayProperty=nameWithType> w żądaniu klienta. Nazwa hosta używaną w adresie URL żądania może być inna niż nazwa hosta serwera, nazwa komputera serwera, adres IP komputera lub adres sprzężenia zwrotnego. W takich przypadkach Windows zakończy się niepowodzeniem żądania uwierzytelniania. Aby rozwiązać ten problem, musimy powiadomić systemu Windows, która nazwa hosta używana w adresie URL żądania w kliencie żądania ("contoso", na przykład) jest rzeczywiście alternatywną nazwę komputera lokalnego.  
  
 Istnieje kilka możliwych metod dla aplikacji serwera obejść tę zmianę. Zalecanym podejściem jest mapowanie nazwy hosta używaną w adresie URL żądania do `BackConnectionHostNames` klucza w rejestrze na serwerze. `BackConnectionHostNames` Klucz rejestru zwykle są używane do mapowania nazwy hosta na adres sprzężenia zwrotnego. Poniżej przedstawiono kroki.  
  
 Aby określić nazwy hostów, które są mapowane na adres sprzężenia zwrotnego i mogą łączyć się z witryn sieci Web na komputerze lokalnym, wykonaj następujące kroki:  
  
 1. Kliknij przycisk Start, kliknij przycisk Uruchom, wpisz regedit, a następnie kliknij przycisk OK.  
  
 2. W Edytorze rejestru Znajdź, a następnie kliknij przycisk następujący klucz rejestru:  
  
 `HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Control\Lsa\MSV1_0`  
  
 3. Kliknij prawym przyciskiem myszy MSV1_0, wskaż polecenie Nowy, a następnie kliknij wartość ciągu wielokrotnego.  
  
 4. Typ `BackConnectionHostNames`, a następnie naciśnij klawisz ENTER.  
  
 5. Kliknij prawym przyciskiem myszy `BackConnectionHostNames`, a następnie kliknij polecenie Modyfikuj.  
  
 6. W polu dane wartości wpisz nazwę hosta lub nazwy hosta dla witryny (nazwa hosta używaną w adresie URL żądania), które znajdują się na komputerze lokalnym, a następnie kliknij przycisk OK.  
  
 7. Zamknij Edytor rejestru, a następnie uruchom ponownie usługę usługę i uruchom polecenie IISReset.  
  
 Mniej bezpieczna opcja pracy około jest wyłączenie kontroli wstecz pętli, zgodnie z opisem w [ http://support.microsoft.com/kb/896861 ](http://go.microsoft.com/fwlink/?LinkID=179657). Wyłącza ochronę przed atakami odbicia. Dlatego lepiej jest ograniczyć zestaw alternatywnych nazw wyłącznie do tych oczekiwać maszyny, aby rzeczywiście używane.  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Net.AuthenticationManager.CustomTargetNameDictionary%2A?displayProperty=nameWithType>  
 <xref:System.Net.HttpRequestHeader?displayProperty=nameWithType>  
 <xref:System.Net.HttpWebRequest.Host%2A?displayProperty=nameWithType>
