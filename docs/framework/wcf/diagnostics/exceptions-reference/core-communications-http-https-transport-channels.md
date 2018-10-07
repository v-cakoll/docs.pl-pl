---
title: 'Komunikacja podstawowa: Kanały transportu HTTP i HTTPS'
ms.date: 03/30/2017
ms.assetid: 6c0a23c9-a663-461c-bdab-58b4d3e23642
ms.openlocfilehash: 4c4a2537ae615943ffac299a8c8cd00c67094360
ms.sourcegitcommit: 8c28ab17c26bf08abbd004cc37651985c68841b8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/06/2018
ms.locfileid: "48844192"
---
# <a name="core-communications-httphttps-transport-channels"></a>Komunikacja podstawowa: Kanały transportu HTTP/HTTPS
Ten temat zawiera listę wszystkich wyjątków generowanych przez kanały programu Windows Communication Foundation (WCF) transportu HTTP/HTTPS.  
  
## <a name="exception-list"></a>Lista wyjątków  
  
|Kod zasobu|Ciąg zasobu|  
|-------------------|---------------------|  
|DigestExplicitCredsImpersonationLevel|Określono poziom personifikacji określony. Uwierzytelnianie szyfrowane HTTP obsługuje tylko poziom "Personifikacji", gdy jest używane z jawne poświadczenia.|  
|FramingContentTypeMismatch|Określony typ zawartości nie była obsługiwana przez określonej usługi. Powiązania klienta i usługi mogą być niezgodne.|  
|Hosting_SslSettingsMisconfigured|Ustawienia protokołu Secure Sockets Layer określonej usługi nie są zgodne z udostępnianych przez Internetowe usługi informacyjne.|  
|HttpAuthSchemeAndClientCert|Fabryka odbiornika protokołu HTTPS została skonfigurowana wymaga certyfikatu klienta i określony schemat uwierzytelniania. Jednak tylko jednej formy uwierzytelniania klienta mogą być wymagane w tym samym czasie.|  
|HttpReceiveFailure|Wystąpił błąd podczas odbierania odpowiedzi HTTP do określonego. Powiązanie punktu końcowego usługi nie może być używany protokół HTTP. Inną możliwością jest, że kontekstu żądania HTTP został zakończony przez serwer ze względu na zamknięcie usługi. Zobacz dzienniki serwera, aby uzyskać więcej informacji.|  
|HttpRegistrationAccessDenied|HTTP nie można zarejestrować określonego adresu URL. Proces nie ma praw dostępu do tej przestrzeni nazw (zobacz [rezerwacje Namespace, rejestracji i Routing](/windows/desktop/http/namespace-reservations-registrations-and-routing) Aby uzyskać szczegółowe informacje).|  
|HttpRegistrationAlreadyExists|HTTP nie można zarejestrować określonego adresu URL. Inna aplikacja już zarejestrowany ten adres URL za pośrednictwem protokołu HTTP. SYS.|  
|HttpRegistrationPortInUse|HTTP nie można zarejestrować określonego adresu URL, ponieważ określony port TCP jest używany przez inną aplikację.|  
|HttpSendFailure|Wystąpił błąd podczas wykonywania żądania HTTP do określonego. Upewnij się, że przyczyna nie jest niezgodność powiązania zabezpieczeń. Upewnij się również, że usługa nie jest skonfigurowana dla protokołu Secure Sockets Layer.|  
|MessageXmlProtocolError|Wystąpił problem z plikiem XML odebranym z sieci. Zobacz wyjątek wewnętrzny, aby uzyskać więcej informacji.|  
|MissingContentType|Odbiorca zwrócił błąd wskazujący, że brak typu zawartości na żądanie do określonego. Zobacz wyjątek wewnętrzny, aby uzyskać więcej informacji.|  
|ProxyAuthenticationLevelMismatch|Poświadczenia uwierzytelniania serwera proxy HTTP określony wymogu wzajemnego uwierzytelniania, który jest bardziej restrykcyjny niż wymagane do uwierzytelniania serwera docelowego.|  
|ProxyImpersonationLevelMismatch|Poświadczenia uwierzytelniania serwera proxy HTTP określone ograniczenia poziomu personifikacji, który jest bardziej restrykcyjny niż ograniczeń do uwierzytelniania serwera docelowego.|  
|SecureChannelFailure|Bezpieczny kanał nie można ustanowić dla Secure Socket Layer/Transport Layer Security przy użyciu określonego urzędu.|  
|TrustFailure|Nie można ustanowić relacji zaufania dla Secure Sockets Layer / Transport Layer Security należy zabezpieczyć kanał z określonego urzędu.|  
|UseDefaultWebProxyCantBeUsedWithExplicitProxyAddress|Nie można określić adresu jawne serwera proxy, a także UseDefaultWebProxy = true w elemencie swoje HttpTransportBinding.|
