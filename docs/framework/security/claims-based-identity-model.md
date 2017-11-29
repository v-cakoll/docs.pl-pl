---
title: "Modelu tożsamości opartego na oświadczeniach"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 4a96a9af-d980-43be-bf91-341a23401431
caps.latest.revision: "7"
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.openlocfilehash: 7219e982f755542a35a33dddf74ee24f4b67e8e6
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="claims-based-identity-model"></a>Modelu tożsamości opartego na oświadczeniach
W przypadku tworzenia aplikacji obsługujących oświadczenia tożsamość użytkownika jest reprezentowana w aplikacji jako zestaw oświadczeń. Jednym oświadczeniem może być nazwa użytkownika, a innym adres e-mail. Chodzi o to, że zewnętrzny system tożsamości jest skonfigurowany do podawania aplikacji wszystkiego, co musi wiedzieć o użytkowniku przy każdym wysyłanym przez niego żądaniu, a przy tym o kryptograficzne zapewnianie, że dane o tożsamości, które otrzymujesz, pochodzą z zaufanego źródła.  
  
 W ramach tego modelu logowanie jednokrotne jest znacznie łatwiejsze do osiągnięcia, a aplikacja przestaje być odpowiedzialna za następujące zadania:  
  
-   uwierzytelnianie użytkowników;  
  
-   przechowywanie kont użytkowników i haseł;  
  
-   wywoływanie katalogów przedsiębiorstwa w celu wyszukania szczegółów dotyczących tożsamości użytkownika;  
  
-   integracja z systemami tożsamości z innych platform lub firm.  
  
 W tym modelu aplikacja podejmuje decyzje dotyczące tożsamości na podstawie oświadczeń dostarczonych przez system, który uwierzytelnił użytkownika. Może to być cokolwiek — od prostej personalizacji aplikacji za pomocą imienia użytkownika do autoryzacji użytkownika w celu umożliwienia mu dostępu do ważniejszych funkcji i zasobów aplikacji.  
  
 Ten temat zawiera następujące informacje:  
  
-   [Wprowadzenie do tożsamości opartego na oświadczeniach](../../../docs/framework/security/claims-based-identity-model.md#BKMK_1)  
  
-   [Podstawowy scenariusz modelu tożsamości opartego na oświadczeniach](../../../docs/framework/security/claims-based-identity-model.md#BKMK_2)  
  
<a name="BKMK_1"></a>   
## <a name="introduction-to-claims-based-identity"></a>Wprowadzenie do tożsamości opartej na oświadczeniach  
 Poniższe terminy i pojęcia mogą ułatwić zrozumienie tej nowej architektury tożsamości.  
  
### <a name="identity"></a>Tożsamość  
 Zgodnie z opisem modelu programowania w systemie Windows Identity Foundation (WIF) zostanie wykorzystany do reprezentują zestaw atrybutów, które opisują użytkownika lub pewne inne jednostki w systemie, w którym chcesz zabezpieczyć termin "identity".  
  
### <a name="claim"></a>Oświadczenie  
 Oświadczenie to pewien fragment informacji o tożsamości, taki jak nazwa, adres e-mail, wiek, członkostwo w roli Sprzedaż. Im więcej oświadczeń odbiera aplikacja, tym więcej będziesz wiedzieć o użytkowniku. Możesz się zastanawiać, dlaczego są one nazywane "oświadczenia," zamiast "attributes", jak często jest używany do opisywania katalogów enterprise. Przyczyna wiąże się z metodą dostarczania. W tym modelu aplikacja nie wyszukuje atrybutów użytkownika w katalogu. W zamian użytkownik dostarcza oświadczenia do aplikacji, a aplikacja je bada. Każde oświadczenie jest tworzone przez wystawcę i ufasz oświadczeniu tylko na tyle, na ile ufasz wystawcy. Na przykład oświadczeniu przesłanemu przez kontroler domeny w Twojej firmie ufasz bardziej niż oświadczeniu przesłanemu przez samego użytkownika. WIF reprezentuje oświadczeń z <xref:System.Security.Claims.Claim> typu, który ma <xref:System.Security.Claims.Claim.Issuer%2A> właściwość, która pozwala sprawdzić, który wystawił oświadczenie.  
  
### <a name="security-token"></a>Token zabezpieczający  
 Użytkownik dostarcza do aplikacji zestaw oświadczeń wraz z żądaniem. W usłudze sieci Web te oświadczenia są przenoszone w nagłówku zabezpieczeń koperty protokołu SOAP. W aplikacji sieci Web opartej na przeglądarce oświadczenia docierają za pośrednictwem metody POST protokołu HTTP z przeglądarki użytkownika, a później mogą być buforowane w pliku cookie, jeśli jest pożądane ustanowienie sesji. Bez względu na to, jak docierają te oświadczenia, muszą być serializowane i z tej serializacji biorą się tokeny zabezpieczające. Token zabezpieczający to zserializowany zestaw oświadczeń podpisany cyfrowo przez urząd wystawiający. Podpis ma istotne znaczenie: zapewnia, że to nie sam użytkownik po prostu utworzył pakiet oświadczeń i przesłał go do Ciebie. W sytuacjach, które nie wymagają wysokiego poziomu zabezpieczeń, gdy kryptografia nie jest konieczna lub pożądana, możesz używać tokenów niepodpisanych, ale tego scenariusza nie opisano w tym temacie.  
  
 Jedną z podstawowych funkcji w programie WIF jest zdolność do tworzenia i odczytywania tokenów zabezpieczających. Programy WIF i .NET Framework wykonują całą pracę związaną z kryptografią i przedstawiają aplikacji zestaw oświadczeń, które możesz odczytać.  
  
### <a name="issuing-authority"></a>Urząd wystawiający  
 Istnieje wiele różnych typów urzędów wystawiających, od kontrolerów domeny, które wystawiają bilety protokołu Kerberos, do urzędów certyfikacji, które wystawiają certyfikaty X.509, ale konkretny typ urzędu omówiony w tym temacie wystawia tokeny zabezpieczające, które zawierają oświadczenia. Ten urząd wystawiający to aplikacja sieci Web lub usługa sieci Web, która umie wystawiać tokeny zabezpieczające. Musi mieć wystarczającą wiedzę, aby wystawiać oświadczenia właściwe dla jednostki uzależnionej i użytkownika zgłaszającego żądanie, i może być odpowiedzialna za interakcję z magazynami użytkowników potrzebną do wyszukiwania oświadczeń i uwierzytelniania samych użytkowników.  
  
 Niezależnie od tego, jaki urząd wystawiający wybierzesz, odgrywa on główną rolę w danym rozwiązaniu tożsamości. Gdy funkcję uwierzytelniania przenosisz poza aplikację, opierając się na oświadczeniach, przekazujesz odpowiedzialność temu urzędowi i prosisz go o uwierzytelnianie użytkowników w Twoim imieniu.  
  
### <a name="security-token-service-sts"></a>Usługa tokenu zabezpieczającego (STS)  
 Usługa tokenu zabezpieczającego (STS) to składnik, który tworzy, podpisuje i wystawia tokeny zabezpieczające zgodnie z protokołami WS-Trust i WS-Federation. Z implementacją tych protokołów wiąże się dużo pracy, ale program WIF wykonuje całą tę pracę za Ciebie, więc nie musisz być ekspertem od tych protokołów, aby szybko i przy niewielkim nakładzie pracy uruchomić usługę STS. Można użyć wbudowanych STS, takich jak [Active Directory® Federation Services (AD FS) 2.0](http://go.microsoft.com/fwlink/?LinkID=247516), chmury STS takich jak [usługi kontroli dostępu (ACS) systemu Windows Azure](http://go.microsoft.com/fwlink/?LinkID=247517), lub, jeśli chcesz wystawiać tokeny niestandardowe lub podaj niestandardowe uwierzytelniania i autoryzacji, można tworzyć własne niestandardowe STS przy użyciu WIF. Program WIF ułatwia tworzenie własnych usług STS.  
  
### <a name="relying-party-application"></a>Aplikacja jednostki uzależnionej  
 Gdy tworzysz aplikację, która opiera się na oświadczeniach, tworzysz aplikację jednostki uzależnionej. Synonimy dla planu odzyskiwania obejmują "aplikacji obsługującej oświadczenia" i "opartej na oświadczeniach aplikacji". Zarówno aplikacje sieci Web, jak i usługi sieci Web mogą być aplikacjami jednostki uzależnionej. Aplikacja jednostki uzależnionej wykorzystuje tokeny wystawione przez usługę STS i wyodrębnia z nich oświadczenia w celu użycia ich do zadań związanych z tożsamością. Program WIF oferuje funkcje ułatwiające tworzenie aplikacji jednostki uzależnionej.  
  
### <a name="standards"></a>Standardy  
 Aby wszystkie te elementy mogły współdziałać, w poprzednim scenariuszu zastosowano kilka standardów WS-*. Zasady są pobierane przy użyciu standardu WS-MetadataExchange i są skonstruowane zgodnie ze specyfikacją WS-Policy. Usługa STS uwidacznia punkty końcowe, które implementują specyfikację WS-Trust opisującą sposób żądania i odbierania tokenów zabezpieczających. Większość dzisiejszych usług STS wystawia tokeny sformatowane przy użyciu języka Security Assertion Markup Langauge (SAML). SAML to uznawany przez całą branżę słownik XML, który może służyć do reprezentowania oświadczeń w sposób interoperacyjny. Ewentualnie, w sytuacji wielu platform, pozwala to na komunikowanie się z usługą STS na całkowicie różnej platformie i osiągnięcie rejestracji jednokrotnej dla wszystkich aplikacji, niezależnie od platformy.  
  
### <a name="browser-based-applications"></a>Aplikacje oparte na przeglądarce  
 Inteligentne aplikacje klienckie to nie jedyne aplikacje, które mogą używać modelu tożsamości opartej na oświadczeniach. Mogą go również używać aplikacje oparte na przeglądarce (zwane także klientami pasywnymi). W poniższym scenariuszu opisano, jak to działa.  
  
 Najpierw użytkownik wskazuje przeglądarkę w aplikacji sieci Web obsługującej oświadczenia (aplikacji jednostki uzależnionej). Aplikacja sieci Web przekierowuje przeglądarkę do usługi STS, więc użytkownik może zostać uwierzytelniony. Usługa STS jest hostowana w prostej aplikacji sieci Web, która odczytuje przychodzące żądanie, uwierzytelnia użytkownika przy użyciu standardowych mechanizmów HTTP, a następnie tworzy token SAML i odpowiada fragmentem kodu JavaScript, który powoduje, że przeglądarka inicjuje metodę POST protokołu HTTP, która z kolei wysyła token SAML z powrotem do jednostki uzależnionej. Treść tej metody POST zawiera oświadczenia, których żądała jednostka uzależniona. W tym momencie jednostka uzależniona zazwyczaj pakuje oświadczenia w plik cookie, dzięki czemu użytkownik nie musi być przekierowywany przy każdym żądaniu.  
  
<a name="BKMK_2"></a>   
## <a name="basic-scenario-for-a-claims-based-identity-model"></a>Podstawowy scenariusz dla modelu tożsamości opartej na oświadczeniach  
 Poniżej przedstawiono przykład systemu opartego na oświadczeniach.  
  
 ![Przepływ uwierzytelniania jednostki uzależnionej w partnera](../../../docs/framework/security/media/conc-relying-partner-processc.png "conc_relying_partner_processc")  
  
 Diagram przedstawia witrynę sieci Web (aplikację jednostki uzależnionej, jednostkę uzależnioną), która jest skonfigurowana do używania programu WIF do uwierzytelniania, oraz klienta, przeglądarkę sieci Web, który chce użyć tej witryny.  
  
1.  Gdy nieuwierzytelniony użytkownik zgłasza żądanie strony, jego przeglądarka jest przekierowywana na strony dostawcy tożsamości.  
  
2.  Dostawca tożsamości wymaga od użytkownika przedstawienia poświadczeń, np. nazwy użytkownika/hasła, biletu protokołu Kerberos itp.  
  
3.  Dostawca tożsamości wystawia token, który jest zwracany z powrotem do przeglądarki.  
  
4.  Przeglądarka zostaje teraz przekierowana z powrotem na pierwotnie żądaną stronę, gdzie program WIF określa, czy token spełnia wymagania niezbędne do uzyskania dostępu do strony. Jeśli tak, wystawiany jest plik cookie w celu ustanowienia sesji, więc wystarczy jednokrotne przeprowadzenie uwierzytelnienia i sterowanie jest przekazywane do aplikacji.
