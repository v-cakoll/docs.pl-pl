---
title: "Usługi WCF i platforma ASP.NET"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: b980496a-f0b0-4319-8e55-a0f0fa32da70
caps.latest.revision: "24"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: be497a1b12164fcca66314921e14d22bb96c20b5
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="wcf-services-and-aspnet"></a>Usługi WCF i platforma ASP.NET
W tym temacie omówiono hosting [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] usług side-by-side z platformy ASP.NET i ich obsługi w trybie zgodności ASP.NET.  
  
## <a name="hosting-wcf-side-by-side-with-aspnet"></a>Hosting WCF Side-by-Side ASP.NET  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]usług hostowanych w Internet Information Services (IIS) może znajdować się z. Strony ASPX i usług sieci Web ASMX wewnątrz jednej, wspólnej domeny aplikacji. Program ASP.NET udostępnia typowe usługi infrastruktury, takie jak zarządzanie AppDomain i kompilacji dynamicznej dla obu [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] i środowiska uruchomieniowego HTTP programu ASP.NET. Konfigurację domyślną dla [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] jest side-by-side ASP.NET.  
  
 ![Usługi WCF i ASP .NET: udostępnianie stanu](../../../../docs/framework/wcf/feature-details/media/hostingwcfwithaspnet.gif "HostingWCFwithASPNET")  
  
 Obsługuje żądania ASP.NET środowiska uruchomieniowego HTTP programu ASP.NET, który nie należy do przetworzenia żądania kierowane do [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] usług, nawet jeśli te usługi są obsługiwane w tej samej domenie aplikacji jest zawartości platformy ASP.NET. Zamiast tego [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] modelu usługi przechwytuje komunikaty adresowane do [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] usług i kieruje je za pośrednictwem [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] stosu kanał transportu.  
  
 Wyniki modelu side-by-side są następujące:  
  
-   ASP.NET i [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] usług mogą udostępniać stan elementu AppDomain. Ponieważ dwóch platform mogą współistnieć w tej samej domenie AppDomain [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] mogą również współużytkować stanu elementu AppDomain z platformy ASP.NET (w tym zmienne statyczne, zdarzeń i tak dalej).  
  
-   [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]usługi spójnie działają niezależnie od hostowania środowiska i transportu. Środowisko uruchomieniowe programu ASP.NET HTTP celowo jest sprzężona IIS/ASP.NET hostowania środowiska i komunikacji HTTP. Z drugiej strony [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] ma zachowywać się spójne w środowiskach hostingu ([!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] spójnie działa zarówno wewnątrz i poza nimi usług IIS) i przez transportu (usługi hostowanej w usługach IIS 7.0 i nowszych zachowanie jest spójny we wszystkich punkty końcowe eksponuje, nawet jeśli niektóre z tych punktów końcowych używają protokołów innych niż HTTP).  
  
-   Wewnątrz elementu AppDomain funkcje wdrożone przez program obsługi HTTP można zastosować do zawartości platformy ASP.NET, ale nie do [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]. Wiele funkcji specyficzne dla protokołu HTTP w aplikacji platformy ASP.NET nie dotyczą [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] usługi hostowane wewnątrz elementu AppDomain zawartości ASP.NET. Przykłady te funkcje obejmują:  
  
    -   Element HttpContext: <xref:System.Web.HttpContext.Current%2A> jest zawsze `null` dostępie z poziomu [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] usługi. Użyj <!--zz <xref:System.ServiceModel.OperationContext.Current.RequestContext>--> `RequestContext` zamiast tego.  
  
    -   Autoryzacji opartej na plikach: [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] model zabezpieczeń nie zezwala na listy kontroli dostępu (ACL) zastosowane w pliku svc usługi przy podejmowaniu decyzji, czy żądanie obsługi jest autoryzowany.  
  
    -   Autoryzacja adresów URL na podstawie konfiguracji: Podobnie [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] model zabezpieczeń nie pasuje do żadnych reguł autoryzacji na podstawie adresu URL określonego w jego System.Web \<autoryzacji > element konfiguracji. Te ustawienia są ignorowane w przypadku [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] żądania, jeśli usługa znajduje się w przestrzeni adresów URL zabezpieczone przez ASP. Reguł autoryzacji adresów URL w sieci.  
  
    -   Rozszerzalność HttpModule: [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] hosting przechwytuje infrastruktury [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] żądań kiedy <xref:System.Web.HttpApplication.PostAuthenticateRequest> zdarzenie jest zgłaszane i nie może zwracać przetwarzania potoku HTTP programu ASP.NET. Moduły, które są zakodowane w celu przechwycenia żądań na późniejszym etapie w potoku przechwytuje [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] żądań.  
  
    -   Personifikacji aplikacji ASP.NET: Domyślnie [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] żądań zawsze działa gdy usługi IIS przetwarzają tożsamości, nawet jeśli program ASP.NET ma ustawioną wartość Włącz personifikację za pomocą jego System.Web \<spersonifikować tożsamości = "true" / > opcji konfiguracji.  
  
 Ograniczenia te dotyczą tylko [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] usług hostowanych w aplikacji usług IIS. Zachowanie zawartości ASP.NET nie ma wpływu na obecność [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)].  
  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]aplikacje, które wymagają funkcjonalność tradycyjnie potoku HTTP należy rozważyć użycie [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] ekwiwalenty, hosta i transportu niezależnych:  
  
-   <xref:System.ServiceModel.OperationContext>zamiast <xref:System.Web.HttpContext>.  
  
-   <xref:System.ServiceModel.Description.ServiceAuthorizationBehavior>zamiast ASP. Autoryzacja pliku lub adres URL w sieci.  
  
-   <xref:System.ServiceModel.Dispatcher.IDispatchMessageInspector>lub warstwowego kanałów niestandardowych zamiast moduły HTTP.  
  
-   Personifikacja dla każdej operacji przy użyciu [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] zamiast System.Web personifikacji.  
  
 Alternatywnie można rozważyć Twojej usługi uruchomione w [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]w tryb zgodności ASP.NET.  
  
## <a name="hosting-wcf-services-in-aspnet-compatibility-mode"></a>Hosting usług WCF w trybie zgodności ASP.NET  
 Mimo że [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] modelu zaprojektowano w celu spójnie działają w środowiskach macierzystych i transportów, są często scenariuszy, w którym aplikacja nie wymaga to poziom elastyczności. [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]w tryb zgodności ASP.NET jest odpowiedni dla scenariuszy, które nie wymagają możliwości hosta poza usług IIS lub komunikacji za pośrednictwem protokołów innych niż HTTP, ale wykorzystujące wszystkie funkcje platformy aplikacji sieci Web ASP.NET.  
  
 W odróżnieniu od domyślnej konfiguracji side-by-side, gdzie [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] hosting przechwytuje infrastruktury [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] wiadomości i kieruje je poza potoku HTTP [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] usługi działające w trybie zgodności ASP.NET uczestniczyć w pełni cykl życia żądania HTTP programu ASP.NET. W trybie zgodności [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] usługi używają potoku HTTP za pośrednictwem <xref:System.Web.IHttpHandler> implementacji, podobnie jak żądania sposób dla strony ASPX i usług sieci Web ASMX są obsługiwane. W związku z tym [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] działa tak samo ASMX względem następujące funkcje platformy ASP.NET:  
  
-   <xref:System.Web.HttpContext>: [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] mogą uzyskiwać dostęp do usług działających w trybie zgodności ASP.NET <xref:System.Web.HttpContext.Current%2A> i jego skojarzony stan.  
  
-   Autoryzacji opartej na plikach: [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] usługi działające w trybie zgodności ASP.NET mogą być bezpieczne przez dołączenie pliku system listy kontroli dostępu (ACL) w pliku svc usługi.  
  
-   Można skonfigurować Autoryzacja adresów URL: ASP. Reguł autoryzacji adresów URL w sieci są wymuszane dla [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] żądań kiedy [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] usługa jest uruchomiona w trybie zgodności ASP.NET.  
  
-   <xref:System.Web.HttpModuleCollection>rozszerzalność: ponieważ [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] usługi działające w trybie zgodności ASP.NET w pełni uczestniczyć w cyklu życia żądania HTTP programu ASP.NET, każdy moduł HTTP skonfigurowany w potoku HTTP będzie mógł działać na [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] żądań przed i po wywołania usługi.  
  
-   Personifikacji aplikacji ASP.NET: [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] usług przy użyciu bieżącej tożsamości ASP.NET spersonifikować wątku, który może być inna niż tożsamość procesu usług IIS, jeśli włączono personifikacji aplikacji ASP.NET dla aplikacji. Jeśli personifikacji aplikacji ASP.NET i [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] personifikacji zarówno włączonych dla operacji określonej usługi, implementacji usługi jest ostatecznie wykonywane przy użyciu tożsamości uzyskanych od [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)].  
  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]na poziomie aplikacji przy użyciu następującej konfiguracji (znajdujący się w pliku Web.config aplikacji) jest włączony tryb zgodności ASP.NET:  
  
```xml  
<system.serviceModel>  
    <serviceHostingEnvironment aspNetCompatibilityEnabled="true" />  
</system.serviceModel>  
```  
  
 Wartością domyślną jest "`true`" Jeśli nie zostanie określony. Ustawienie tej wartości na "`false`" oznacza to, że wszystkie [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] usług uruchomionych w aplikacji nie będzie działać w trybie zgodności ASP.NET.  
  
 Ponieważ tryb zgodności ASP.NET oznacza semantyki przetwarzania żądania, które są różni się od [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] domyślnie możliwość kontrolowania, czy są uruchomione wewnątrz aplikacji ASP, które mają implementacje poszczególnych usług. Włączono tryb zgodności z sieci. Usługi mogą używać <xref:System.ServiceModel.Activation.AspNetCompatibilityRequirementsAttribute> wskazująca, czy obsługują one tryb zgodności ASP.NET. Wartość domyślna tego atrybutu to <xref:System.ServiceModel.Activation.AspNetCompatibilityRequirementsMode.Allowed>.  
  
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
>  Usługi IIS 7.0 i WAS umożliwia [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] usługi do komunikacji za pośrednictwem protokołów innych niż HTTP. Jednak [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] usług uruchomionych w aplikacjach, które włączono tryb zgodności ASP.NET nie wolno ekspozycji punktów końcowych protokołu HTTP. Taka konfiguracja generuje wyjątek aktywacji, gdy usługa odbiera jego pierwszego komunikatu.  
  
 Aby uzyskać więcej informacji na temat włączania tryb zgodności ASP.NET dla [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] usługi, zobacz <xref:System.ServiceModel.Activation.AspNetCompatibilityRequirementsMode> i [zgodności z platformą ASP.NET](../../../../docs/framework/wcf/samples/aspnet-compatibility.md) próbki.  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.ServiceModel.Activation.AspNetCompatibilityRequirementsAttribute>  
 [Windows Server AppFabric funkcje hostingu](http://go.microsoft.com/fwlink/?LinkId=201276)
