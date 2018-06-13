---
title: Zarządzanie sesjami WIF
ms.date: 03/30/2017
ms.assetid: 98bce126-18a9-401b-b20d-67ee462a5f8a
author: BrucePerlerMS
manager: mbaldwin
ms.openlocfilehash: f97406ccf826bfa5b7c3ed87bdb58478b272a216
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33399116"
---
# <a name="wif-session-management"></a>Zarządzanie sesjami WIF
Gdy pierwszy klient próbuje uzyskać dostępu do chronionego zasobu, która jest obsługiwana przez jednostkę uzależnioną, klient muszą najpierw uwierzytelnić się z usługą tokenu zabezpieczeń (STS), który jest uznawany za zaufany przez jednostkę uzależnioną. Usługa tokenu Zabezpieczającego następnie wystawia token zabezpieczający do klienta. Klient przedstawia ten token do jednostki uzależnionej, co powoduje przyznanie dostępu klientów do chronionego zasobu. Jednak nie chcesz umożliwić klientowi ponownego uwierzytelnienia do serwera STS dla każdego żądania, szczególnie, ponieważ może nie nawet być w tym samym komputerze lub w tej samej domenie co jednostki uzależnionej. Zamiast tego Windows Identity Foundation (WIF) ma klienta i ustanowienia sesji, w którym klient używa tokenu zabezpieczającego sesji do samodzielnego uwierzytelnienia do jednostki uzależnionej dla wszystkich żądań, po pierwszym żądaniu jednostki uzależnionej. Jednostki uzależnionej można użyć tego tokenu zabezpieczającego sesji, który jest przechowywany w pliku cookie, aby odtworzyć klienta <xref:System.Security.Claims.ClaimsPrincipal?displayProperty=nameWithType>.  
  
 Usługa tokenu Zabezpieczającego definiuje rodzaju uwierzytelniania klient musi dostarczyć. Jednak klient może mieć wiele poświadczeń, z którymi uwierzytelniania się do serwera STS. Na przykład może mieć tokenu z usługi Windows Live, nazwę użytkownika i hasło, certyfikatu i smartkey. W takim przypadku Usługa tokenu Zabezpieczającego przyznaje klienta kilka tożsamości z każda tożsamość odpowiadającego poświadczeń, który klient przedstawia. Jednostki uzależnionej można użyć co najmniej jednego z tych tożsamości, podczas jej decyduje o tym, jakiego poziomu dostępu klienta.  
  
 <xref:System.IdentityModel.Tokens.SessionSecurityToken?displayProperty=nameWithType> Służy do rekonstrukcji klienta <xref:System.Security.Claims.ClaimsPrincipal?displayProperty=nameWithType>, który zawiera wszystkie tożsamości klienta w <xref:System.Security.Claims.ClaimsPrincipal.Identities%2A>. Każdy <xref:System.Security.Claims.ClaimsIdentity?displayProperty=nameWithType> w kolekcji zawiera tokeny ładowania początkowego, które są skojarzone z tą tożsamością.  
  
 Jeśli wystawiony token nowej sesji o identyfikatorze sesji oryginalnego tokenu sesji, <xref:System.IdentityModel.Tokens.SessionSecurityTokenHandler?displayProperty=nameWithType> nie aktualizuje tokenu sesji w pamięci podręcznej tokenu. Należy zawsze utworzyć wystąpienia tokenu sesji z unikalny identyfikator sesji.  
  
> [!NOTE]
>  Zgłasza Session.SecurityTokenHandler.ReadToken <xref:System.Xml.XmlException> wyjątek, jeśli otrzymuje nieprawidłowe dane wejściowe; na przykład, jeśli plik cookie zawierający tokenu sesji jest uszkodzony. Zalecamy przechwycić tego wyjątku, a następnie podaj zachowanie specyficzne dla aplikacji.  
  
 Jeśli chroniony strony sieci Web zawiera wiele zasobów (takich jak mała grafiki), które również znajdują się w domenie chronionych, klient musi zostać ponownie uwierzytelnione się do jednostki uzależnionej, aby pobrać każdego z tych zasobów. Użyj tokenu uwierzytelniania sesji uniknąć konieczności uwierzytelnienia do serwera STS dla każdego żądania, ale nadal oznacza, że pakiety są wysyłane za pośrednictwem wielu plików cookie. Można skonfigurować strony sieci Web, tak aby ważnych danych i zasobów są przechowywane w domenie chronionych, podczas gdy pomocnicza elementy są przechowywane w domenie niechronione i połączone z głównym strony sieci Web. Ponadto należy ustawić ścieżkę pliku cookie, aby odwołać domenę chronioną.  
  
 Do pracy w trybie odwołania, firma Microsoft zaleca zapewnienie obsługi dla <xref:System.IdentityModel.Services.WSFederationAuthenticationModule.SessionSecurityTokenCreated> zdarzenia w **global.asax.cs** plików i ustawienie **IsReferenceMode** przekazana właściwość w tokenie <xref:System.IdentityModel.Services.SessionSecurityTokenCreatedEventArgs.SessionToken%2A> właściwości. Te aktualizacje zapewnia, że tokenu sesji działa w trybie odwołań dla każdego żądania i jest ich drużyna jest faworytem za pośrednictwem jedynie ustawienia <xref:System.IdentityModel.Services.SessionAuthenticationModule.IsReferenceMode%2A> właściwości w Module sesji uwierzytelniania.  
  
## <a name="extensibility"></a>Rozszerzalność  
 Można rozszerzyć mechanizm zarządzania sesji. Powodem tego jest poprawić wydajność. Na przykład można utworzyć niestandardowego pliku cookie programu obsługi, który przekształca lub optymalizuje tokenu zabezpieczającego sesji od jego stan w pamięci i co przechodzi w stan pliku cookie. Aby to zrobić, można skonfigurować <xref:System.IdentityModel.Services.SessionAuthenticationModule.CookieHandler%2A?displayProperty=nameWithType> właściwość <xref:System.IdentityModel.Services.SessionAuthenticationModule?displayProperty=nameWithType> do używania obsługi niestandardowego pliku cookie, pochodzącą z <xref:System.IdentityModel.Services.CookieHandler?displayProperty=nameWithType>. <xref:System.IdentityModel.Services.ChunkedCookieHandler?displayProperty=nameWithType> jest domyślny program obsługi plików cookie, ponieważ pliki cookie przekracza dozwolony rozmiar dla protokołu HTTP (Hypertext Transfer); Jeśli zamiast tego użyj obsługi niestandardowego pliku cookie musi implementować podziału.  
  
 Aby uzyskać więcej informacji, zobacz [ClaimsAwareWebFarm](http://go.microsoft.com/fwlink/?LinkID=248408) (http://go.microsoft.com/fwlink/?LinkID=248408) próbki. W tym przykładzie pokazano pamięci podręcznej sesji gotowy farmy (w przeciwieństwie do tokenreplycache), dzięki czemu można użyć sesji przez odwołanie, zamiast wymiana dużych plików cookie. w tym przykładzie przedstawiono również prostszy sposób ochrony plików cookie w farmie. Pamięci podręcznej sesji jest oparte na WCF. W odniesieniu do zabezpieczania sesji w przykładzie pokazano nową funkcję w wersji WIF 4.5 transformacji pliku cookie oparte na MachineKey, który może być uruchomiony po prostu wklejając odpowiedni fragment kodu w pliku web.config. Próbka sam jest nie "przez człowieka", ale pokazuje, co jest potrzebne do tworzenia aplikacji gotowych farmy.
