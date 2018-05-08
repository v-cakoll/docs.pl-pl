---
title: Usługi WCF i platforma ASP.NET
ms.date: 03/30/2017
ms.assetid: b980496a-f0b0-4319-8e55-a0f0fa32da70
ms.openlocfilehash: 6cfd4f8a5dc2a7835cba409a37b09166e49e8df3
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="wcf-services-and-aspnet"></a>Usługi WCF i platforma ASP.NET
W tym temacie omówiono hostingu usług Windows Communication Foundation (WCF) usług po stronie by-side z platformy ASP.NET i ich obsługi w trybie zgodności ASP.NET.  
  
## <a name="hosting-wcf-side-by-side-with-aspnet"></a>Hosting WCF Side-by-Side ASP.NET  
 Usługi WCF hostowanej w Internet Information Services (IIS) może znajdować się z. Strony ASPX i usług sieci Web ASMX wewnątrz jednej, wspólnej domeny aplikacji. Program ASP.NET udostępnia typowe usługi infrastruktury, takie jak zarządzanie elementu AppDomain i kompilacji dynamicznej WCF i środowiska uruchomieniowego HTTP programu ASP.NET. Domyślna konfiguracja usług WCF jest side-by-side ASP.NET.  
  
 ![Usługi WCF i ASP .NET: udostępnianie stanu](../../../../docs/framework/wcf/feature-details/media/hostingwcfwithaspnet.gif "HostingWCFwithASPNET")  
  
 Środowiska uruchomieniowego HTTP platformy ASP.NET obsługuje żądania ASP.NET, który nie należy do przetworzenia żądania kierowane do usługi WCF, nawet jeśli te usługi są obsługiwane w tej samej domenie aplikacji jest zawartości platformy ASP.NET. Zamiast tego modelu usług WCF przechwytuje komunikaty adresowane do usług WCF i kieruje je do stosu kanał transportu WCF.  
  
 Wyniki modelu side-by-side są następujące:  
  
-   Usługi ASP.NET i WCF można udostępniać stan elementu AppDomain. Ponieważ dwóch platform mogą współistnieć w tej samej domenie aplikacji, usługi WCF mogą również współużytkować stanu elementu AppDomain ASP.NET (w tym zmienne statyczne, zdarzeń i tak dalej).  
  
-   Usługi WCF spójnie działają niezależnie od hostowania środowiska i transportu. Środowisko uruchomieniowe programu ASP.NET HTTP celowo jest sprzężona IIS/ASP.NET hostowania środowiska i komunikacji HTTP. Z drugiej strony, WCF zaprojektowano w celu zachowania stale w środowiskach hostingu (WCF spójnie działa zarówno wewnątrz i poza nimi usług IIS) i przez transportu (usługi hostowanej w usługach IIS 7.0 i nowszych zachowanie jest spójny we wszystkich punktów końcowych ujawnia on nawet wtedy, gdy Niektóre z tych punktów końcowych używają protokołów innych niż HTTP).  
  
-   Wewnątrz elementu AppDomain funkcje wdrożone przez program obsługi HTTP mają zastosowanie do zawartości platformy ASP.NET, ale nie do usługi WCF. Wiele funkcji specyficzne dla protokołu HTTP w aplikacji platformy ASP.NET nie dotyczą usług WCF hostowanych wewnątrz elementu AppDomain zawartości ASP.NET. Przykłady te funkcje obejmują:  
  
    -   Element HttpContext: <xref:System.Web.HttpContext.Current%2A> jest zawsze `null` podczas uzyskiwania dostępu do z, w ramach usługi WCF. Użyj <!--zz <xref:System.ServiceModel.OperationContext.Current.RequestContext>--> `RequestContext` zamiast tego.  
  
    -   Autoryzacji opartej na plikach: model zabezpieczeń usługi WCF nie zezwala na listy kontroli dostępu (ACL) zastosowane w pliku svc usługi przy podejmowaniu decyzji, czy żądanie obsługi jest autoryzowany.  
  
    -   Autoryzacja adresów URL na podstawie konfiguracji: Podobnie modelu zabezpieczeń WCF nie pasuje do żadnych reguł autoryzacji na podstawie adresu URL określonego w jego System.Web \<autoryzacji > element konfiguracji. Te ustawienia są ignorowane dla żądań WCF, jeśli usługa znajduje się w przestrzeni adresów URL zabezpieczone przez ASP. Reguł autoryzacji adresów URL w sieci.  
  
    -   Rozszerzalność HttpModule: hostingu infrastruktura WCF przechwytuje WCF podczas żądania <xref:System.Web.HttpApplication.PostAuthenticateRequest> zdarzenie jest zgłaszane i nie może zwracać przetwarzania potoku HTTP programu ASP.NET. Moduły, które są zakodowane w celu przechwycenia żądań na późniejszym etapie w potoku przechwytuje żądania WCF.  
  
    -   Personifikacji aplikacji ASP.NET: domyślnie WCF żądań zawsze działa gdy usługi IIS przetwarzają tożsamości, nawet jeśli program ASP.NET ma ustawioną wartość Włącz personifikację za pomocą jego System.Web \<spersonifikować tożsamości = "true" / > opcji konfiguracji.  
  
 Ograniczenia te dotyczą tylko usług WCF hostowanych w aplikacji usług IIS. Zachowanie zawartości ASP.NET nie ma wpływu na obecność WCF.  
  
 Aplikacji WCF, które wymagają funkcjonalność tradycyjnie potoku HTTP należy wziąć pod uwagę odpowiedniki WCF, hosta i transportu niezależnych:  
  
-   <xref:System.ServiceModel.OperationContext> zamiast <xref:System.Web.HttpContext>.  
  
-   <xref:System.ServiceModel.Description.ServiceAuthorizationBehavior> zamiast ASP. Autoryzacja pliku lub adres URL w sieci.  
  
-   <xref:System.ServiceModel.Dispatcher.IDispatchMessageInspector> lub warstwowego kanałów niestandardowych zamiast moduły HTTP.  
  
-   Personifikacja dla każdej operacji za pomocą usługi WCF zamiast System.Web personifikacji.  
  
 Alternatywnie można rozważyć uruchamianie usług w trybie zgodności ASP.NET dla usługi WCF.  
  
## <a name="hosting-wcf-services-in-aspnet-compatibility-mode"></a>Hosting usług WCF w trybie zgodności ASP.NET  
 Mimo że modelu WCF jest przeznaczony do spójnie działają w środowiskach macierzystych i transportów, istnieją często scenariuszy, w którym aplikacja nie wymaga to poziom elastyczności. Tryb zgodności ASP.NET dla usługi WCF jest odpowiednia dla scenariuszy, które nie wymagają możliwości hosta poza usług IIS lub do komunikacji za pośrednictwem protokołów innych niż HTTP, ale wykorzystujące wszystkie funkcje platformy aplikacji sieci Web ASP.NET.  
  
 W odróżnieniu od domyślnej konfiguracji side-by-side, gdy infrastruktura hostingu WCF przechwytuje wiadomości WCF i kieruje je poza potoku HTTP, usługi WCF w trybie zgodności ASP.NET pełni uczestniczyć w cyklu życia żądania HTTP programu ASP.NET. W trybie zgodności, usługi WCF użyć potoku HTTP za pośrednictwem <xref:System.Web.IHttpHandler> implementacji, podobnie jak żądania sposób dla strony ASPX i usług sieci Web ASMX są obsługiwane. W związku z tym WCF działa tak samo ASMX względem następujące funkcje platformy ASP.NET:  
  
-   <xref:System.Web.HttpContext>: Usługi WCF działające w trybie zgodności ASP.NET mogą uzyskiwać dostęp do <xref:System.Web.HttpContext.Current%2A> i jego skojarzony stan.  
  
-   Autoryzacji opartej na plikach: usługi WCF w trybie zgodności ASP.NET mogą być bezpieczne przez dołączenie pliku system listy kontroli dostępu (ACL) w pliku svc usługi.  
  
-   Można skonfigurować Autoryzacja adresów URL: ASP. Reguł autoryzacji adresów URL w sieci są wymuszane dla żądań WCF, gdy usługa WCF jest uruchomiona w trybie zgodności ASP.NET.  
  
-   <xref:System.Web.HttpModuleCollection> rozszerzalność: usługi WCF ponieważ uruchomiony w trybie zgodności ASP.NET w pełni uczestniczyć w cyklu życia żądania HTTP programu ASP.NET, każdy moduł HTTP skonfigurowany w potoku HTTP będzie mógł działać na żądania WCF przed i po wywołania usługi.  
  
-   Personifikacji aplikacji ASP.NET: Usługi WCF uruchomić przy użyciu bieżącej tożsamości ASP.NET spersonifikować wątku, który może być inna niż tożsamość procesu usług IIS, jeśli włączono personifikacji aplikacji ASP.NET dla aplikacji. Jeśli personifikacji aplikacji ASP.NET i WCF personifikacji zarówno włączonych dla operacji określonej usługi implementacji usługi ostatecznie jest wykonywane przy użyciu tożsamości uzyskane z usługi WCF.  
  
 Tryb zgodności ASP.NET dla usługi WCF jest włączone na poziomie aplikacji przy użyciu następującej konfiguracji (znajdujący się w pliku Web.config aplikacji):  
  
```xml  
<system.serviceModel>  
    <serviceHostingEnvironment aspNetCompatibilityEnabled="true" />  
</system.serviceModel>  
```  
  
 Wartością domyślną jest "`true`" Jeśli nie zostanie określony. Ustawienie wartości "`false`" wskazuje, że wszystkie usługi WCF w aplikacji nie zostaną uruchomione w trybie zgodności ASP.NET.  
  
 Ponieważ tryb zgodności ASP.NET oznacza semantyki przetwarzania żądania są różni się od domyślnego WCF, implementacji usługi poszczególnych ma możliwość kontrolowania, czy działają wewnątrz aplikacji ASP.NET, które Włączono tryb zgodności. Usługi mogą używać <xref:System.ServiceModel.Activation.AspNetCompatibilityRequirementsAttribute> wskazująca, czy obsługują one tryb zgodności ASP.NET. Wartość domyślna tego atrybutu to <xref:System.ServiceModel.Activation.AspNetCompatibilityRequirementsMode.Allowed>.  
  
 `[AspNetCompatibilityRequirements(RequirementsMode = AspNetCompatibilityRequirementsMode.Allowed)]`  
  
 `public class CalculatorService : ICalculatorSession`  
  
 `{//Implement calculator service methods.}`  
  
 W poniższej tabeli przedstawiono, jak ustawienie trybu zgodności całej aplikacji współdziała z pojedynczej usługi podane poziom obsługi:  
  
|Ustawienie trybu zgodności całej aplikacji|[AspNetCompatibilityRequirementsMode]<br /><br /> Ustawienie|Wynik obserwowanych|  
|--------------------------------------------------|---------------------------------------------------------|---------------------|  
|aspNetCompatibilityEnabled = "`true`"|<xref:System.ServiceModel.Activation.AspNetCompatibilityRequirementsMode.Required>|Usługa zostanie aktywowany pomyślnie.|  
|aspNetCompatibilityEnabled = "`true`"|<xref:System.ServiceModel.Activation.AspNetCompatibilityRequirementsMode.Allowed>|Usługa zostanie aktywowany pomyślnie.|  
|aspNetCompatibilityEnabled = "`true`"|<xref:System.ServiceModel.Activation.AspNetCompatibilityRequirementsMode.NotAllowed>|Wystąpi błąd aktywacji, gdy usługa odbiera komunikat.|  
|aspNetCompatibilityEnabled = "`false`"|<xref:System.ServiceModel.Activation.AspNetCompatibilityRequirementsMode.Required>|Wystąpi błąd aktywacji, gdy usługa odbiera komunikat.|  
|aspNetCompatibilityEnabled = "`false`"|<xref:System.ServiceModel.Activation.AspNetCompatibilityRequirementsMode.Allowed>|Usługa zostanie aktywowany pomyślnie.|  
|aspNetCompatibilityEnabled = "`false`"|<xref:System.ServiceModel.Activation.AspNetCompatibilityRequirementsMode.NotAllowed>|Usługa zostanie aktywowany pomyślnie.|  
  
> [!NOTE]
>  Usługi IIS 7.0 i WAS umożliwia usługi WCF do komunikacji za pośrednictwem protokołów innych niż HTTP. Usługi WCF działające w aplikacjach, które włączono tryb zgodności ASP.NET nie są dozwolone na ekspozycji punktów końcowych protokołu HTTP. Taka konfiguracja generuje wyjątek aktywacji, gdy usługa odbiera jego pierwszego komunikatu.  
  
 Aby uzyskać więcej informacji na temat włączania tryb zgodności ASP.NET dla usługi WCF, zobacz <xref:System.ServiceModel.Activation.AspNetCompatibilityRequirementsMode> i [zgodności z platformą ASP.NET](../../../../docs/framework/wcf/samples/aspnet-compatibility.md) próbki.  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.ServiceModel.Activation.AspNetCompatibilityRequirementsAttribute>  
 [Windows Server AppFabric funkcje hostingu](http://go.microsoft.com/fwlink/?LinkId=201276)
