---
title: Ujawnianie informacji
ms.date: 03/30/2017
ms.assetid: 4064c89f-afa6-444a-aa7e-807ef072131c
ms.openlocfilehash: b42faeb4043302e5e70379cc4e1de3cb8bd96af4
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59195907"
---
# <a name="information-disclosure"></a>Ujawnianie informacji
Ujawnienie informacji umożliwia osobie atakującej uzyskanie cenne informacje o systemie. W związku z tym zawsze należy wziąć pod uwagę jakie informacje są przedstawiania i czy mogą być używane przez złośliwego użytkownika. Poniżej wymieniono ataków ujawnienie informacji możliwych i zapewnia środki zaradcze dla każdego.  
  
## <a name="message-security-and-http"></a>Zabezpieczenia komunikatów i HTTP  
 Jeśli używane są zabezpieczenia na poziomie komunikatu za pośrednictwem warstwy transportu HTTP, należy pamiętać, zabezpieczenia na poziomie komunikatu nie chroni nagłówków HTTP. Jedynym sposobem, aby chronić nagłówków HTTP jest użyj transportu HTTPS zamiast protokołu HTTP. Transportu HTTPS powoduje, że cały komunikat, włącznie z nagłówkami HTTP, na szyfrowanie przy użyciu protokołu Secure Sockets Layer (SSL).  
  
## <a name="policy-information"></a>Informacje o zasadach  
 Zapewnienie bezpieczeństwa zasad jest ważne, szczególnie w scenariuszach Federacji, gdzie poufnych wymagania tokenu wystawionego lub informacji Wystawca tokenu jest uwidaczniany w zasadach. W takich przypadkach zaleca się bezpieczny punkt końcowy zasad usługi federacyjnej, aby uniemożliwić osobom atakującym uzyskania informacji na temat usługi, takie jak typ oświadczenia, które należy umieścić w wystawiony token lub przekierowywania klientów do złośliwego wystawcy tokenów. Na przykład osoba atakująca można wykryć pary nazwa/hasło użytkownika przez ponowne skonfigurowanie łańcuch zaufania federacyjnego można zakończyć w wystawcę wykonywanego atak typu man-in--middle. Zalecane jest również federacyjnego klienci, którzy uzyskać ich powiązania za pomocą pobierania zasad Sprawdź, zaufanych wystawców w łańcuchu uzyskanej zaufania federacyjnego. Aby uzyskać więcej informacji o scenariuszach Federacji, zobacz [Federacji](../../../../docs/framework/wcf/feature-details/federation.md).  
  
## <a name="memory-dumps-can-reveal-claim-information"></a>Zrzuty pamięci może ujawnić informacje o  
 Gdy aplikacja zakończy się niepowodzeniem, pliki dzienników, takich jak te utworzone przez odzyskiwania po awarii. Watson, mogą zawierać informacje oświadczenia. Te informacje nie powinny być eksportowany do innych jednostek, takich jak zespoły pomocy technicznej; w przeciwnym razie eksportowane są również informacje oświadczenia, które zawiera dane prywatne. Można temu zaradzić przez nie wysyłają pliki dziennika na nieznany jednostki. Aby uzyskać więcej informacji, zobacz [systemu Windows Server 2003](https://go.microsoft.com/fwlink/?LinkId=89160).  
  
## <a name="endpoint-addresses"></a>Adresy punktów końcowych  
 Adres punktu końcowego zawiera informacje potrzebne do komunikowania się z punktem końcowym. Protokołu SOAP zabezpieczeń musi zawierać adres w całości w wiadomości negocjacji zabezpieczeń, które są wymieniane w celu negocjowania klucz symetryczny między klientem a serwerem. Ponieważ negocjowanie zabezpieczeń ładowania początkowego procesu, nagłówki adresów nie mogą być szyfrowane w trakcie tego procesu. Dlatego adres nie powinna zawierać żadnych poufnych danych; w przeciwnym razie prowadzi do ataków ujawnienie informacji.  
  
## <a name="certificates-transferred-unencrypted"></a>Niezaszyfrowane przesłanych certyfikatów  
 Gdy używasz certyfikatu X.509 do uwierzytelnienia klienta, certyfikat jest przesyłany w Wyczyść, wewnątrz nagłówek SOAP. Należy pamiętać o tym jako potencjalne ujawnienie identyfikowalne dane osobowe (PII). To nie jest problemem w przypadku `TransportWithMessageCredential` tryb, w którym cały komunikat jest szyfrowana za pomocą zabezpieczeń na poziomie transportu.  
  
## <a name="service-references"></a>Odwołania do usług  
 Odwołanie do usługi jest odwołaniem do innej usługi. Na przykład usługa może przekazać odwołanie do klienta w trakcie operacji usługi. Odwołanie do usługi jest również używany z *zaufania weryfikatora tożsamości*, wewnętrznych składników, które gwarantuje, że tożsamość docelowego podmiotu zabezpieczeń przed ujawnieniu informacji takich jak dane aplikacji lub poświadczeń do docelowego. Jeśli tożsamość zdalnego zaufania nie można zweryfikować lub jest nieprawidłowa, nadawca należy upewnić się, że żadne dane nie została ujawniona, które mogą negatywnie wpłynąć na, aplikacji lub użytkownika.  
  
 Środki zaradcze są następujące:  
  
-   Odwołania do usług są rozpatrywane godne zaufania. Zajmujemy się zawsze wtedy, gdy transfer wystąpień odwołanie do usługi, aby upewnić się, że ich nie zostały naruszone.  
  
-   Niektóre aplikacje mogą prezentować interfejs użytkownika, który umożliwia interakcyjne ustanowienia relacji zaufania, na podstawie danych z danych referencyjnych i zaufania usługi sprawdzone przez hosta zdalnego. Usługi WCF udostępniają punkty rozszerzeń dla takiego obiektu, ale użytkownik musi zaimplementować je.  
  
## <a name="ntlm"></a>NTLM  
 Domyślnie w środowisku domeny Windows uwierzytelniania Windows używa protokołu Kerberos do uwierzytelniania i autoryzacji użytkowników. Jeśli nie można użyć protokołu Kerberos jakiegoś powodu, NT LAN Manager (NTLM) jest używany jako rezerwowe. To zachowanie można wyłączyć, ustawiając <xref:System.ServiceModel.Security.WindowsClientCredential.AllowNtlm%2A> właściwość `false`. Problemy, które należy wiedzieć podczas umożliwiając NTLM obejmują:  
  
-   NTLM przedstawia nazwę użytkownika klienta. Jeśli nazwa użytkownika musi być poufny, wartość `AllowNTLM` właściwość wiązania `false`.  
  
-   Uwierzytelnianie NTLM nie zapewnia uwierzytelniania serwera. W związku z tym klient nie upewnij się, że jego komunikuje się z odpowiednią usługę podczas uwierzytelniania NTLM jest używany jako protokół uwierzytelniania.  
  
### <a name="specifying-client-credentials-or-invalid-identity-forces-ntlm-usage"></a>Określanie poświadczeń klienta lub nieprawidłową tożsamość wymusza użycia uwierzytelniania NTLM  
 Podczas tworzenia klienta, określając poświadczeń klienta bez nazwy domeny lub określanie tożsamości nieprawidłowy serwer, powoduje, że NTLM, ma być używana zamiast protokołu Kerberos (Jeśli `AlllowNtlm` właściwość jest ustawiona na `true`). Ponieważ NTLM nie wykonuje uwierzytelniania serwera, informacji o potencjalnie może ujawnić.  
  
 Na przykład jest możliwe określenie poświadczeń klienta Windows bez nazwy domeny, jak pokazano w poniższym kodzie języka Visual C#.  
  
```  
MyChannelFactory.Credentials.Windows.ClientCredential = new System.Net.NetworkCredential("username", "password");  
```  
  
 Kod nie określa nazwy domeny, a zatem będą używane uwierzytelnianie NTLM.  
  
 Jeśli określono domenę, ale nieprawidłowa główna nazwa usługi jest określony za pomocą funkcji tożsamości punktu końcowego, NTLM jest używany. Aby uzyskać więcej informacji na temat sposobu tożsamość punktu końcowego jest określona, zobacz [uwierzytelnianie i tożsamość usług](../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md).  
  
## <a name="see-also"></a>Zobacz także

- [Zagadnienia dotyczące zabezpieczeń](../../../../docs/framework/wcf/feature-details/security-considerations-in-wcf.md)
- [Podniesienie uprawnień](../../../../docs/framework/wcf/feature-details/elevation-of-privilege.md)
- [Odmowa usługi](../../../../docs/framework/wcf/feature-details/denial-of-service.md)
- [Manipulowanie](../../../../docs/framework/wcf/feature-details/tampering.md)
- [Nieobsługiwane scenariusze](../../../../docs/framework/wcf/feature-details/unsupported-scenarios.md)
- [Ataki oparte na metodzie powtórzeń](../../../../docs/framework/wcf/feature-details/replay-attacks.md)
