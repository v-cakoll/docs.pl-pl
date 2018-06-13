---
title: Ujawnianie informacji
ms.date: 03/30/2017
ms.assetid: 4064c89f-afa6-444a-aa7e-807ef072131c
ms.openlocfilehash: 1f6c33787f920fbe7e795e27ff10d7a0c83db21e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33495986"
---
# <a name="information-disclosure"></a>Ujawnianie informacji
Ujawnienie informacji umożliwia osobie atakującej uzyskanie cennych informacji na temat systemu. W związku z tym zawsze należy wziąć pod uwagę jakie informacje są ujawniania i czy mogą być używane przez złośliwego użytkownika. Poniżej przedstawiono informacje o możliwych ataków ujawnienie i zapewnia środki zaradcze dla każdego.  
  
## <a name="message-security-and-http"></a>Zabezpieczenia komunikatów i HTTP  
 Jeśli używane są zabezpieczenia na poziomie komunikatu za pośrednictwem warstwy transportu HTTP, należy pamiętać, zabezpieczenia na poziomie komunikatu nie chroni nagłówków HTTP. Jedynym sposobem, aby chronić nagłówków HTTP jest używają protokołu HTTPS zamiast protokołu HTTP. HTTPS transport powoduje, że cały komunikat, włącznie z nagłówkami HTTP szyfrowania przy użyciu protokołu Secure Sockets Layer (SSL).  
  
## <a name="policy-information"></a>Informacje o zasadach  
 Dzięki bezpieczna zasad jest ważne, szczególnie w scenariuszach Federacji, gdzie informacje wystawcy tokenu lub poufnych wymagania wystawiony token jest widoczna w zasadach. W takich przypadkach zaleca się bezpieczny punkt końcowy zasad usługi federacyjnej, aby uniemożliwić osobom atakującym uzyskania informacji na temat usługi, takie jak typ oświadczenia, które mają zostać umieszczone w wystawionego tokenu lub przekierowanie klientów do złośliwego wystawcy tokenu. Na przykład osoba atakująca może odnaleźć pary nazwa/hasło użytkownika przez ponowne skonfigurowanie łańcuch zaufania federacyjnego zakończenie w wystawcę wykonywania ataku typu man-in--middle. Zalecane jest również federacyjnych klientów, którzy uzyskać ich powiązania za pośrednictwem pobieranie zasad Sprawdź, zaufanych wystawców w łańcuchu zaufania federacyjnego uzyskany. Aby uzyskać więcej informacji o scenariuszach Federacji, zobacz [federacyjnego](../../../../docs/framework/wcf/feature-details/federation.md).  
  
## <a name="memory-dumps-can-reveal-claim-information"></a>Zrzuty pamięci mogą zawierać informacje o  
 W przypadku awarii aplikacji pliki dzienników, takich jak te utworzone przez odzyskiwania po awarii. Watson, mogą zawierać informacje oświadczeń. Te informacje nie powinny być eksportowany do inne jednostki, na przykład zespoły pomocy technicznej; w przeciwnym razie informacje oświadczenia, które zawiera dane prywatne, również są eksportowane. Można to zagrożenie, wysyłając nie pliki dziennika na nieznany jednostki. Aby uzyskać więcej informacji, zobacz [systemu Windows Server 2003](http://go.microsoft.com/fwlink/?LinkId=89160).  
  
## <a name="endpoint-addresses"></a>Adresy punktów końcowych  
 Adres punktu końcowego zawiera informacje potrzebne do komunikowania się z punktem końcowym. Zabezpieczeń SOAP musi zawierać adres w całości w wiadomości negocjacji zabezpieczeń, które są wymieniane w celu negocjowania klucza symetrycznego między klientem serwerem. Ponieważ proces ładowania początkowego negocjacji zabezpieczeń, nagłówki adresów nie mogą być szyfrowane w trakcie tego procesu. W związku z tym adres nie powinna zawierać żadnych poufnych danych; w przeciwnym razie prowadzi do ataków ujawnienie informacji.  
  
## <a name="certificates-transferred-unencrypted"></a>Niezaszyfrowane przesłanych certyfikatów  
 Korzystając z certyfikatu X.509 do uwierzytelnienia klienta, certyfikat jest przesyłany w zwykłym, wewnątrz nagłówka SOAP. Należy pamiętać o tym jako potencjalne ujawnienie informacji osobistych (dane osobowe). To nie jest problemem w przypadku `TransportWithMessageCredential` tryb, w którym cały komunikat jest zaszyfrowany z zabezpieczeniami na poziomie transportu.  
  
## <a name="service-references"></a>Odwołania do usług  
 Odwołania do usługi jest odwołaniem do innej usługi. Na przykład usługa może przekazywać odwołania do usługi do klienta w trakcie operacji. Odwołanie do usługi jest również używany z *weryfikatora tożsamości zaufania*, wewnętrzny składnik, który gwarantuje tożsamość podmiotu docelowego przed ujawnieniu informacji, takich jak dane aplikacji lub poświadczeń do docelowego. Jeśli tożsamości zaufania zdalnego nie można zweryfikować lub jest nieprawidłowa, nadawca powinien upewnij się, że żadne dane nie została ujawniona, który może naruszyć bezpieczeństwo, aplikacji lub użytkownika.  
  
 Następujące czynniki:  
  
-   Odwołania do usług są uznawane jest godny zaufania. Zajmie się zawsze, gdy transfer wystąpień odwołania usługi, aby upewnić się, że ich nie zostały naruszone.  
  
-   Niektóre aplikacje mogą stanowić środowisko użytkownika, co umożliwia interakcyjne ustanowienia relacji zaufania, na podstawie danych w danych referencyjnych i zaufania usługi sprawdzonych przez hosta zdalnego. Usługi WCF udostępniają punkty rozszerzeń dla takiego obiektu, ale użytkownik musi je zaimplementowana.  
  
## <a name="ntlm"></a>NTLM  
 Domyślnie w środowisku domeny systemu Windows, uwierzytelnianie systemu Windows używa protokołu Kerberos do uwierzytelniania i autoryzacji użytkowników. Jeśli z jakiegoś powodu nie można użyć protokołu Kerberos i usługi NT LAN Manager (NTLM) jest używany jako rezerwowe. To zachowanie można wyłączyć, ustawiając <xref:System.ServiceModel.Security.WindowsClientCredential.AllowNtlm%2A> właściwości `false`. Problemy, aby informacje dotyczące stosowanie uwierzytelniania NTLM obejmują:  
  
-   NTLM przedstawia nazwę użytkownika klienta. Jeśli nazwa użytkownika musi poufne, następnie ustawić `AllowNTLM` właściwość powiązania `false`.  
  
-   Uwierzytelnianie NTLM nie zapewnia uwierzytelniania serwera. W związku z tym klienta nie powiodło się, że jest komunikacji z usługą. prawo podczas używania jako protokół uwierzytelniania NTLM.  
  
### <a name="specifying-client-credentials-or-invalid-identity-forces-ntlm-usage"></a>Określanie poświadczeń klienta lub nieprawidłową tożsamość wymusza użycia uwierzytelniania NTLM  
 Podczas tworzenia klienta, określania poświadczeń klienta bez nazwy domeny lub określanie tożsamości nieprawidłowy serwer powoduje, że uwierzytelnianie NTLM zamiast protokołu Kerberos (Jeśli `AlllowNtlm` właściwość jest ustawiona na `true`). Ponieważ NTLM nie uwierzytelniania serwera, może potencjalnie ujawnić informacji.  
  
 Na przykład jest możliwe określenie poświadczeń klienta systemu Windows bez nazwy domeny, jak pokazano w poniższym kodzie Visual C#.  
  
```  
MyChannelFactory.Credentials.Windows.ClientCredential = new System.Net.NetworkCredential("username", "password");  
```  
  
 Ten kod nie określa nazwy domeny, a w związku z tym będzie można użyć uwierzytelniania NTLM.  
  
 Jeśli zostanie określona domena, ale nieprawidłowa główna nazwa usługi jest określona za pomocą funkcji tożsamość punktu końcowego, uwierzytelnianie NTLM jest używany. Aby uzyskać więcej informacji dotyczących sposobu określono tożsamość punktu końcowego, zobacz [uwierzytelnianie i tożsamość usługi](../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Zagadnienia dotyczące bezpieczeństwa](../../../../docs/framework/wcf/feature-details/security-considerations-in-wcf.md)  
 [Podniesienie uprawnień](../../../../docs/framework/wcf/feature-details/elevation-of-privilege.md)  
 [Odmowa usługi](../../../../docs/framework/wcf/feature-details/denial-of-service.md)  
 [Manipulowanie](../../../../docs/framework/wcf/feature-details/tampering.md)  
 [Nieobsługiwane scenariusze](../../../../docs/framework/wcf/feature-details/unsupported-scenarios.md)  
 [Ataki oparte na metodzie powtórzeń](../../../../docs/framework/wcf/feature-details/replay-attacks.md)
