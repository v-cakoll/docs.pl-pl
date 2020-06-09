---
title: Ujawnianie informacji
ms.date: 03/30/2017
ms.assetid: 4064c89f-afa6-444a-aa7e-807ef072131c
ms.openlocfilehash: a58ac4dd3715052031c7fb5c1da480c0d01396ea
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/09/2020
ms.locfileid: "84596867"
---
# <a name="information-disclosure"></a>Ujawnianie informacji

Ujawnienie informacji umożliwia osobie atakującej uzyskanie cennych informacji o systemie. W związku z tym zawsze należy rozważyć jakie informacje są ujawniane i czy mogą być używane przez złośliwego użytkownika. Poniżej przedstawiono listę możliwych ataków na ujawnienie informacji i podano środki zaradcze dla każdego z nich.

## <a name="message-security-and-http"></a>Zabezpieczenia komunikatów i HTTP

Jeśli używasz zabezpieczeń na poziomie komunikatów przez warstwę transportu HTTP, pamiętaj, że zabezpieczenia na poziomie wiadomości nie chronią nagłówków HTTP. Jedynym sposobem ochrony nagłówków HTTP jest użycie transportu HTTPS zamiast protokołu HTTP. Transport HTTPS powoduje, że cały komunikat, łącznie z nagłówkami HTTP, będzie szyfrowany przy użyciu protokołu SSL (SSL).

## <a name="policy-information"></a>Informacje o zasadach

Ochrona zasad jest ważna, szczególnie w scenariuszach federacyjnych, w których poufne wymagania dotyczące tokenu wystawione lub informacje o wystawcy tokenu są ujawniane w zasadach. W takich przypadkach zaleca się zabezpieczenie punktu końcowego zasad usługi federacyjnej, aby uniemożliwić osobom atakującym uzyskanie informacji o usłudze, takich jak typ oświadczeń do umieszczenia w wystawionym tokenie, lub przekierowanie klientów do wystawców złośliwych tokenów. Na przykład osoba atakująca może odnaleźć pary nazwa użytkownika/hasło przez ponowne skonfigurowanie federacyjnego łańcucha zaufania do zakończenia w wystawce, która wykonała atak typu man-in-the-middle. Zaleca się również, aby klienci federacyjną, którzy uzyskują swoje powiązania za pomocą pobierania zasad, weryfikują, że ufają wystawcom w uzyskanym federacyjnym łańcuchu zaufania. Aby uzyskać więcej informacji na temat scenariuszy federacyjnych, zobacz [Federacja](federation.md).

## <a name="memory-dumps-can-reveal-claim-information"></a>Zrzuty pamięci mogą ujawniać informacje dotyczące roszczeń

W przypadku niepowodzenia aplikacji pliki dziennika, takie jak utworzone przez program Dr. Watson, mogą zawierać informacje dotyczące roszczeń. Te informacje nie powinny być eksportowane do innych jednostek, takich jak zespoły pomocy technicznej; w przeciwnym razie eksportowane są również informacje dotyczące roszczeń zawierających prywatne dane. Można to ograniczyć, nie wysyłając plików dziennika do nieznanych jednostek.

## <a name="endpoint-addresses"></a>Adresy punktów końcowych

Adres punktu końcowego zawiera informacje konieczne do komunikacji z punktem końcowym. Zabezpieczenia protokołu SOAP muszą zawierać w pełni pełny adres w komunikatach negocjacji zabezpieczeń wymienianych w celu negocjowania klucza symetrycznego między klientem a serwerem. Ponieważ negocjowanie zabezpieczeń jest procesem ładowania początkowego, nagłówki adresów nie mogą być szyfrowane podczas tego procesu. W związku z tym adres nie powinien zawierać żadnych poufnych danych; w przeciwnym razie prowadzi to do ataków na ujawnienie informacji.

## <a name="certificates-transferred-unencrypted"></a>Certyfikaty przeniesione niezaszyfrowane

W przypadku uwierzytelniania klienta przy użyciu certyfikatu X. 509 certyfikat jest przesyłany w postaci jasnej w nagłówku protokołu SOAP. Należy pamiętać o tym jako potencjalne ujawnienie danych osobowych. Nie jest to problem z `TransportWithMessageCredential` trybem, gdzie cała wiadomość jest zaszyfrowana przy użyciu zabezpieczeń na poziomie transportu.

## <a name="service-references"></a>Odwołania do usług

Odwołanie do usługi jest odwołaniem do innej usługi. Na przykład usługa może przekazać odwołanie usługi do klienta w trakcie operacji. Odwołanie do usługi jest również używane z *weryfikatorem tożsamości zaufania*, wewnętrznym składnikiem, który gwarantuje tożsamość podmiotu docelowego przed odpisaniem informacji, takich jak dane aplikacji lub poświadczenia do obiektu docelowego. Jeśli zdalna tożsamość zaufania nie może zostać zweryfikowana lub jest nieprawidłowa, nadawca powinien upewnić się, że nie ujawniły się żadne dane, które mogłyby spowodować naruszenie zabezpieczeń, aplikacji lub użytkownika.

Środki zaradcze obejmują następujące elementy:

- Odwołania do usług założono, że są wiarygodne. Należy zachować ostrożność, gdy transferuje wystąpienia odwołań do usługi, aby upewnić się, że nie zostały naruszone.

- Niektóre aplikacje mogą przedstawić środowisko użytkownika, które umożliwia interaktywne tworzenie zaufania na podstawie danych w odwołaniu do usługi i danych zaufania sprawdzonych dla hosta zdalnego. Środowisko WCF oferuje punkty rozszerzalności dla takich funkcji, ale użytkownik musi je wdrożyć.

## <a name="ntlm"></a>NTLM

Domyślnie w środowisku domeny systemu Windows uwierzytelnianie systemu Windows korzysta z protokołu Kerberos do uwierzytelniania i autoryzowania użytkowników. Jeśli z jakiegoś powodu nie można użyć protokołu Kerberos, NT LAN Manager (NTLM) jest używany jako rezerwowy. To zachowanie można wyłączyć, ustawiając <xref:System.ServiceModel.Security.WindowsClientCredential.AllowNtlm%2A> Właściwość na `false` . Problemy, które należy wziąć pod uwagę podczas zezwalania na uwierzytelnianie NTLM:

- Protokół NTLM ujawnia nazwę użytkownika klienta. Jeśli nazwa użytkownika musi być zachowana poufne, ustaw `AllowNTLM` właściwość powiązania na `false` .

- Uwierzytelnianie NTLM nie zapewnia uwierzytelniania serwera. W związku z tym klient nie może upewnić się, że komunikuje się z odpowiednią usługą w przypadku używania protokołu NTLM jako protokół uwierzytelniania.

### <a name="specifying-client-credentials-or-invalid-identity-forces-ntlm-usage"></a>Określanie poświadczeń klienta lub nieprawidłowa tożsamość wymusza użycie NTLM

W przypadku tworzenia klienta, określania poświadczeń klienta bez nazwy domeny lub określania nieprawidłowej tożsamości serwera, zamiast protokołu Kerberos należy użyć uwierzytelniania NTLM (Jeśli `AllowNtlm` Właściwość jest ustawiona na `true` ). Ponieważ protokół NTLM nie umożliwia uwierzytelniania serwera, może być możliwe ujawnienie informacji.

Można na przykład określić poświadczenia klienta systemu Windows bez nazwy domeny, jak pokazano w poniższym kodzie języka Visual C#.

```csharp
MyChannelFactory.Credentials.Windows.ClientCredential = new System.Net.NetworkCredential("username", "password");
```

Kod nie określa nazwy domeny i w związku z tym zostanie użyty protokół NTLM.

Jeśli określono domenę, ale określono nieprawidłową nazwę główną usługi przy użyciu funkcji tożsamości punktu końcowego, używany jest protokół NTLM. Aby uzyskać więcej informacji o sposobie określenia tożsamości punktu końcowego, zobacz [tożsamość usługi i uwierzytelnianie](service-identity-and-authentication.md).

## <a name="see-also"></a>Zobacz też

- [Zagadnienia dotyczące zabezpieczeń](security-considerations-in-wcf.md)
- [Podniesienie uprawnień](elevation-of-privilege.md)
- [Odmowa usługi](denial-of-service.md)
- [Manipulowanie](tampering.md)
- [Nieobsługiwane scenariusze](unsupported-scenarios.md)
- [Ataki oparte na metodzie powtórzeń](replay-attacks.md)
