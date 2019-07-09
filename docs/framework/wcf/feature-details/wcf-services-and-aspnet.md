---
title: Usługi WCF i platforma ASP.NET
ms.date: 03/30/2017
ms.assetid: b980496a-f0b0-4319-8e55-a0f0fa32da70
ms.openlocfilehash: d42787492b00b8e0a5a732d641947fec61b5ff96
ms.sourcegitcommit: d6e27023aeaffc4b5a3cb4b88685018d6284ada4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/09/2019
ms.locfileid: "67663679"
---
# <a name="wcf-services-and-aspnet"></a>Usługi WCF i platforma ASP.NET

W tym temacie omówiono hostingu usług Windows Communication Foundation (WCF) usług side-by-side z platformą ASP.NET i hosting je w tryb zgodności ASP.NET.

## <a name="hosting-wcf-side-by-side-with-aspnet"></a>Hostowanie usługi WCF side-by-side za pomocą platformy ASP.NET

Usługi WCF hostowanej w Internet Information Services (IIS) może znajdować się za pomocą. Strony ASPX i usług sieci Web ASMX wewnątrz jednej, wspólnej domeny aplikacji. ASP.NET udostępnia wspólne usługi infrastruktury, takie jak zarządzanie AppDomain i kompilacji dynamicznej dla środowiska uruchomieniowego HTTP platformy ASP.NET i WCF. W domyślnej konfiguracji programu WCF jest side-by-side za pomocą platformy ASP.NET.

![Zrzut ekranu przedstawiający usług WCF i ASP .NET: udostępnianie stanu.](./media/wcf-services-and-aspnet/windows-communication-foundation-services-asp-dotnet-configuration.gif)

Środowisko uruchomieniowe ASP.NET HTTP obsługuje żądania programu ASP.NET, ale nie uczestniczy w przetwarzanie żądania kierowane do usługi WCF, nawet jeśli te usługi znajdują się w tej samej domenie aplikacji, ponieważ jest zawartości platformy ASP.NET. Zamiast tego modelu usług WCF przechwytuje komunikaty adresowane do usług WCF i kieruje je za pomocą stosu transportu/kanału WCF.

Wyniki modelu side-by-side są następujące:

- Usługi ASP.NET i WCF można udostępniać stanu obiektu AppDomain. Ponieważ dwie struktury mogą współistnieć w tej samej domenie aplikacji, usługi WCF można także udostępnić stan elementu AppDomain za pomocą platformy ASP.NET (w tym zmiennych statycznych, zdarzenia i tak dalej).

- Usługi WCF spójnie działają niezależnie od hostowania środowiska i mechanizm transportu. Środowisko uruchomieniowe ASP.NET HTTP jest sprzężona celowo IIS/ASP.NET hostowania środowiska i komunikacji HTTP. Z drugiej strony, WCF jest przeznaczona do spójnego zachowują się w różnych środowiskach hostingu (WCF zachowuje się stale zarówno wewnątrz lub na zewnątrz usług IIS) i między nimi transportu (usługi hostowane w usługach IIS 7.0 i nowszych ma spójne zachowanie we wszystkich punktach zewnętrznych udostępnia ona nawet wtedy, gdy Niektóre z tych punktów końcowych używają protokołów innych niż HTTP).

- Wewnątrz elementu AppDomain funkcje implementowane przez środowisko wykonawcze protokołu HTTP można zastosować do zawartości platformy ASP.NET, ale nie do programu WCF. Wiele funkcji specyficzne dla protokołu HTTP w aplikacji platformy ASP.NET nie dotyczą usług WCF hostowanych w domenie aplikacji, która zawiera zawartości ASP.NET. Przykłady te funkcje są następujące:

  - HttpContext: <xref:System.Web.HttpContext.Current%2A> jest zawsze `null` podczas uzyskiwania dostępu do z, w ramach usługi WCF. Zamiast nich należy używać słów kluczowych <xref:System.ServiceModel.Channels.RequestContext>.

  - Autoryzacja oparta na pliku: Model zabezpieczeń usługi WCF nie zezwala na listy kontroli dostępu (ACL) zastosowane do pliku .svc usługi przy podejmowaniu decyzji, czy żądanie obsługi jest autoryzowany.

  - Autoryzacja oparta na konfiguracji adresu URL: Podobnie, model zabezpieczeń usługi WCF nie pasuje do żadnych reguł autoryzacji opartej na adres URL określony w firmy System.Web \<autoryzacji > element konfiguracji. Te ustawienia są ignorowane w przypadku żądań usług WCF, jeśli usługa znajduje się w obszarze adres URL zabezpieczony przez ASP. Reguły autoryzacji adresów URL w sieci.

  - Rozszerzalność HttpModule: Infrastruktury hostingu WCF przechwytuje WCF podczas żądania <xref:System.Web.HttpApplication.PostAuthenticateRequest> zdarzenie jest zgłaszane i nie zwraca przetwarzania w potoku HTTP programu ASP.NET. Moduły, które są kodowane w celu przechwycenia żądań na późniejszym etapie w potoku przechwytuje żądania usługi WCF.

  - Personifikacja w programie ASP.NET: Domyślnie WCF żądań zawsze działa zgodnie z IIS przetwarzanie tożsamości, nawet wtedy, gdy program ASP.NET jest ustawiona na Włączanie personifikacji przy użyciu System.Web firmy \<Personifikuj tożsamość = "true" / > opcja konfiguracji.

Te ograniczenia mają zastosowanie tylko do usług WCF hostowanych w aplikacji usług IIS. Zachowanie zawartości ASP.NET nie występuje w obecności WCF.

Aplikacji WCF, które wymagają funkcji tradycyjnie zapewnianych przez potok HTTP należy wziąć pod uwagę odpowiedniki WCF, które hosta i transportu, niezależnie od:

- <xref:System.ServiceModel.OperationContext> zamiast <xref:System.Web.HttpContext>.

- <xref:System.ServiceModel.Description.ServiceAuthorizationBehavior> zamiast ASP. NET w pliku/Autoryzacja adresów URL.

- <xref:System.ServiceModel.Dispatcher.IDispatchMessageInspector> lub niestandardowe kanały warstwowej zamiast moduły HTTP.

- Personifikacji dla każdej operacji przy użyciu usługi WCF zamiast personifikacji System.Web.

Alternatywnie można rozważyć uruchamiania usług w trybie zgodności ASP.NET dla usługi WCF.

## <a name="hosting-wcf-services-in-aspnet-compatibility-mode"></a>Hostowanie usługi WCF w tryb zgodności ASP.NET

Chociaż WCF model jest przeznaczony do spójnego zachowują się w różnych środowiskach macierzystych i transportu, istnieją często scenariusze, w których aplikacja nie wymaga to stopień elastyczności. Tryb zgodności ASP.NET dla usługi WCF jest odpowiednia dla scenariuszy, które nie wymagają możliwości hosta poza usług IIS lub do komunikacji za pośrednictwem protokołów innych niż HTTP, ale które korzystają z wszystkich funkcji platforma aplikacji sieci Web platformy ASP.NET.

W przeciwieństwie do domyślnej konfiguracji side-by-side, gdzie infrastruktury hostingu WCF przechwytuje komunikatów WCF i kieruje je poza potok HTTP, usługi WCF, uruchomiony w trybie zgodności ASP.NET uczestniczą w pełni cyklu życia żądania HTTP programu ASP.NET. W trybie zgodności usług WCF korzystanie z potoku HTTP za pośrednictwem <xref:System.Web.IHttpHandler> implementacji podobne żądania sposób dla stron ASPX i usług sieci Web ASMX są obsługiwane. W rezultacie WCF działa identycznie do ASMX w odniesieniu do następujących funkcji programu ASP.NET:

- <xref:System.Web.HttpContext>: Usługi WCF, uruchomiony w trybie zgodności ASP.NET mogą uzyskiwać dostęp do <xref:System.Web.HttpContext.Current%2A> i jego skojarzony stan.

- Autoryzacja oparta na pliku: Usługi WCF, uruchomiony w trybie zgodności ASP.NET może być bezpieczne, dołączając plik system listy kontroli dostępu (ACL) do pliku svc usługi.

- Autoryzacja adresów URL można skonfigurować: ASP. Reguły autoryzacji adresów URL w sieci odnosi się do żądania usługi WCF, kiedy usługa WCF jest uruchomiona w trybie zgodności w programie ASP.NET.

- <xref:System.Web.HttpModuleCollection> rozszerzalność: Ponieważ usługi WCF, uruchomiony w trybie zgodności ASP.NET uczestniczą w pełni cyklu życia żądania HTTP programu ASP.NET, każdy moduł HTTP skonfigurowane w potoku HTTP jest w stanie działać w odpowiedzi na żądania usługi WCF, przed i po wywołania usługi.

- Personifikacja w programie ASP.NET: Usługi WCF przy użyciu bieżącej tożsamości ASP.NET personifikacji wątku, który może być inny niż tożsamość procesu usług IIS, jeśli włączono personifikacji aplikacji ASP.NET w aplikacji. Jeśli personifikacji aplikacji ASP.NET i WCF personifikacja są włączone dla operacji określonej usługi, implementacji usługi ostatecznie jest uruchamiana przy użyciu tożsamości uzyskane z usługi WCF.

Tryb zgodności ASP.NET dla usługi WCF jest włączone na poziomie aplikacji przy użyciu następującej konfiguracji (znajdujące się w pliku Web.config aplikacji):

```xml
<system.serviceModel>
    <serviceHostingEnvironment aspNetCompatibilityEnabled="true" />
</system.serviceModel>
```

Wartością domyślną jest "`true`" Jeśli nie zostanie określony. Ustawienie wartości "`false`" oznacza, że wszystkie usługi WCF w aplikacji nie będą uruchamiane w trybie zgodności w programie ASP.NET.

Ponieważ tryb zgodności ASP.NET wskazuje semantykę przetwarzania żądania, która różni się od domyślnej usługi WCF, implementacji poszczególnych usług mają możliwość kontrolowania, czy działają w aplikacji ASP.NET, które Włączono tryb zgodności. Usługi mogą używać <xref:System.ServiceModel.Activation.AspNetCompatibilityRequirementsAttribute> do wskazania, czy obsługują one tryb zgodności ASP.NET. Wartość domyślna tego atrybutu to <xref:System.ServiceModel.Activation.AspNetCompatibilityRequirementsMode.Allowed>.

```csharp
[AspNetCompatibilityRequirements(RequirementsMode = AspNetCompatibilityRequirementsMode.Allowed)]
public class CalculatorService : ICalculatorSession
{//Implement calculator service methods.}
```

W poniższej tabeli przedstawiono, jak ustawienie trybu zgodności całej aplikacji współdziała z konkretną usługę określonego poziomu wsparcia:

|Ustawienie trybu zgodności całej aplikacji|[AspNetCompatibilityRequirementsMode]<br /><br /> Ustawienie|Wynik obserwowanych|
|--------------------------------------------------|---------------------------------------------------------|---------------------|
|aspNetCompatibilityEnabled = "`true`"|<xref:System.ServiceModel.Activation.AspNetCompatibilityRequirementsMode.Required>|Usługa aktywuje się pomyślnie.|
|aspNetCompatibilityEnabled = "`true`"|<xref:System.ServiceModel.Activation.AspNetCompatibilityRequirementsMode.Allowed>|Usługa aktywuje się pomyślnie.|
|aspNetCompatibilityEnabled = "`true`"|<xref:System.ServiceModel.Activation.AspNetCompatibilityRequirementsMode.NotAllowed>|Błąd aktywacji występuje, gdy usługa odbiera komunikat.|
|aspNetCompatibilityEnabled = "`false`"|<xref:System.ServiceModel.Activation.AspNetCompatibilityRequirementsMode.Required>|Błąd aktywacji występuje, gdy usługa odbiera komunikat.|
|aspNetCompatibilityEnabled = "`false`"|<xref:System.ServiceModel.Activation.AspNetCompatibilityRequirementsMode.Allowed>|Usługa aktywuje się pomyślnie.|
|aspNetCompatibilityEnabled = "`false`"|<xref:System.ServiceModel.Activation.AspNetCompatibilityRequirementsMode.NotAllowed>|Usługa aktywuje się pomyślnie.|

> [!NOTE]
> Usługi IIS 7.0 i WAS umożliwia usługi WCF do komunikowania się za pośrednictwem protokołów innych niż HTTP. Usługi WCF w aplikacji, które mają włączony tryb zgodności ASP.NET nie są dozwolone do uwidaczniają punkty końcowe protokołu HTTP. Taka konfiguracja generuje wyjątek aktywacji, gdy usługa odbiera jej pierwszego komunikatu.

Aby uzyskać więcej informacji na temat włączania tryb zgodności ASP.NET dla usługi WCF, zobacz <xref:System.ServiceModel.Activation.AspNetCompatibilityRequirementsMode> i [zgodność platformy ASP.NET](../samples/aspnet-compatibility.md) próbki.

## <a name="see-also"></a>Zobacz także

- <xref:System.ServiceModel.Activation.AspNetCompatibilityRequirementsAttribute>
- [Windows Server AppFabric funkcje hostingu](https://docs.microsoft.com/previous-versions/appfabric/ee677189(v=azure.10))
