---
title: Usługi WCF i ASP.NET
ms.date: 03/30/2017
ms.assetid: b980496a-f0b0-4319-8e55-a0f0fa32da70
ms.openlocfilehash: 0a64e277d3465b77a2553d6b9c3901f09a6e1a52
ms.sourcegitcommit: 8c99457955fc31785b36b3330c4ab6ce7984a7ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/29/2019
ms.locfileid: "75544738"
---
# <a name="wcf-services-and-aspnet"></a>Usługi WCF i ASP.NET

W tym temacie omówiono hosting usług Windows Communication Foundation (WCF) obok ASP.NET i hostowanie ich w trybie zgodności ASP.NET.

## <a name="hosting-wcf-side-by-side-with-aspnet"></a>Hosting programu WCF obok ASP.NET

Usługi WCF hostowane w Internet Information Services (IIS) mogą być zlokalizowane przy użyciu programu. Strony ASPX i usługi sieci Web ASMX w jednej, wspólnej domenie aplikacji. Usługa ASP.NET udostępnia typowe usługi infrastruktury, takie jak zarządzanie domeną aplikacji i Dynamiczna kompilacja dla środowiska uruchomieniowego w programie WCF i ASP.NET. Konfiguracja domyślna dla programu WCF działa równolegle z ASP.NET.

![Zrzut ekranu przedstawiający usługi WCF i ASP .NET: stan udostępniania.](./media/wcf-services-and-aspnet/windows-communication-foundation-services-asp-dotnet-configuration.gif)

Środowisko uruchomieniowe HTTP ASP.NET obsługuje żądania ASP.NET, ale nie uczestniczy w przetwarzaniu żądań przeznaczonych dla usług WCF, mimo że te usługi są hostowane w tej samej domenie aplikacji, w której znajduje się zawartość ASP.NET. Zamiast tego model usługi WCF przechwytuje komunikaty rozkierowane do usług WCF i przekierowuje je za pośrednictwem stosu transportu/kanału WCF.

Wyniki modelu side-by-Side są następujące:

- Usługi ASP.NET i WCF mogą współużytkować stan domeny aplikacji. Ponieważ dwie struktury mogą współistnieć w tej samej domenie aplikacji, usługa WCF może również udostępniać stan AppDomain przy użyciu ASP.NET (w tym zmiennych statycznych, zdarzeń itd.).

- Usługi WCF działają spójnie, niezależnie od środowiska hostingu i transportu. Środowisko uruchomieniowe HTTP ASP.NET jest celowo powiązane ze środowiskiem hostingu usług IIS/ASP. NET i komunikacją protokołu HTTP. Natomiast WCF jest zaprojektowana tak, aby zachować spójność między środowiskami hostingu (WCF zachowuje się zarówno wewnątrz, jak i na zewnątrz usług IIS) i między transportami (usługa hostowana w usługach IIS 7,0 i nowszych ma spójne zachowanie dla wszystkich punktów końcowych, które ujawnia, nawet jeśli Niektóre z tych punktów końcowych używają protokołów innych niż HTTP).

- W ramach elementu AppDomain funkcje zaimplementowane przez środowisko uruchomieniowe protokołu HTTP mają zastosowanie do zawartości ASP.NET, ale nie do usługi WCF. Wiele funkcji specyficznych dla protokołu HTTP platformy aplikacji ASP.NET nie ma zastosowania do usług WCF hostowanych w ramach elementu AppDomain, który zawiera zawartość ASP.NET. Poniżej wymieniono następujące funkcje:

  - HttpContext: <xref:System.Web.HttpContext.Current%2A> jest zawsze `null` w przypadku dostępu z poziomu usługi WCF. Zamiast nich należy używać słów kluczowych <xref:System.ServiceModel.Channels.RequestContext>.

  - Autoryzacja na podstawie plików: model zabezpieczeń WCF nie zezwala na użycie listy kontroli dostępu (ACL) zastosowanej do pliku SVC usługi podczas decydowania, czy żądanie obsługi jest autoryzowane.

  - Autoryzacja adresu URL opartego na konfiguracji: analogicznie model zabezpieczeń WCF nie jest zgodny z żadną regułą autoryzacji opartą na adresie URL określoną w elemencie konfiguracji > autoryzacji w sieci Web \<. Te ustawienia są ignorowane w przypadku żądań programu WCF, jeśli usługa znajduje się w przestrzeni adresów URL zabezpieczonej przez ASP. Reguły autoryzacji adresów URL w sieci.

  - Rozszerzalność modułu HttpModule: infrastruktura hostingu WCF przechwytuje żądania programu WCF w przypadku zgłoszenia zdarzenia <xref:System.Web.HttpApplication.PostAuthenticateRequest> i nie zwraca przetwarzania do potoku HTTP ASP.NET. Moduły kodowane do przechwytywania żądań na późniejszych etapach potoku nie przechwytuje żądań WCF.

  - Personifikacja ASP.NET: Domyślnie żądania WCF są zawsze uruchamiane jako tożsamość procesu usług IIS, nawet jeśli ASP.NET jest ustawiona na włączenie personifikacji przy użyciu opcji system. Web \<Identity Impersonate = "true"/> Configuration.

Te ograniczenia dotyczą tylko usług WCF hostowanych w aplikacji usług IIS. Obecność programu WCF nie ma wpływ na zachowanie zawartości ASP.NET.

Aplikacje WCF, które wymagają funkcjonalności tradycyjnie zapewnianej przez potok HTTP, powinny być brane pod uwagę przy użyciu odpowiedników WCF, które są niezależne od hosta i transportu:

- <xref:System.ServiceModel.OperationContext>, a nie <xref:System.Web.HttpContext>.

- <xref:System.ServiceModel.Description.ServiceAuthorizationBehavior> zamiast ASP. Autoryzacja plików/adresów URL w sieci.

- <xref:System.ServiceModel.Dispatcher.IDispatchMessageInspector> lub niestandardowych kanałów warstwowych zamiast modułów HTTP.

- Personifikacja dla każdej operacji przy użyciu platformy WCF zamiast personifikacji system. Web.

Alternatywnie możesz rozważyć uruchomienie usług w trybie zgodności ASP.NET programu WCF.

## <a name="hosting-wcf-services-in-aspnet-compatibility-mode"></a>Hostowanie usług WCF w trybie zgodności ASP.NET

Mimo że model WCF został zaprojektowany tak, aby zachować spójność między środowiskami hostingu i transportami, często istnieją sytuacje, w których aplikacja nie wymaga tego stopnia elastyczności. Tryb zgodności ASP.NET WCF jest odpowiedni dla scenariuszy, które nie wymagają możliwości hostowania poza programem IIS ani do komunikowania się za pośrednictwem protokołów innych niż HTTP, ale które korzystają ze wszystkich funkcji platformy aplikacji sieci Web ASP.NET.

W przeciwieństwie do domyślnej konfiguracji równoległej, w której infrastruktura hostingu WCF przechwytuje komunikaty programu WCF i przekierowuje je z potoku HTTP, usługi WCF działające w trybie zgodności ASP.NET uczestniczą w pełni w cyklu ASP.NET żądania HTTP. W trybie zgodności usługi WCF używają potoku HTTP za pośrednictwem implementacji <xref:System.Web.IHttpHandler>, podobnie jak żądania stron ASPX i usług sieci Web ASMX. W związku z tym WCF zachowuje się identycznie z usługą ASMX w odniesieniu do następujących funkcji ASP.NET:

- <xref:System.Web.HttpContext>: usługi WCF działające w trybie zgodności ASP.NET mogą uzyskać dostęp do <xref:System.Web.HttpContext.Current%2A> i skojarzonego z nim stanu.

- Autoryzacja na podstawie plików: usługi WCF działające w trybie zgodności ASP.NET można zabezpieczyć przez dołączenie list kontroli dostępu (ACL) systemu plików do pliku SVC usługi.

- Konfigurowalne Autoryzacja adresów URL: ASP. Reguły autoryzacji adresów URL sieci są wymuszane w przypadku żądań WCF, gdy usługa WCF jest uruchomiona w trybie zgodności ASP.NET.

- <xref:System.Web.HttpModuleCollection> rozszerzalność: ponieważ usługi WCF działające w trybie zgodności ASP.NET uczestniczą w pełni w cyklu życia żądań HTTP ASP.NET, każdy moduł HTTP skonfigurowany w potoku HTTP może działać na żądaniach WCF zarówno przed, jak i po wywołaniu usługi.

- Personifikacja ASP.NET: usługi WCF działają przy użyciu bieżącej tożsamości wątku personifikowanego ASP.NET, który może być inny niż tożsamość procesu usług IIS, jeśli włączono personifikację ASP.NET dla aplikacji. Jeśli dla określonej operacji usługi jest włączona personifikacja ASP.NET i personifikacja WCF, implementacja usługi ostatecznie zostanie uruchomiona przy użyciu tożsamości uzyskanej z WCF.

Tryb zgodności ASP.NET WCF jest włączony na poziomie aplikacji za pomocą następującej konfiguracji (znajdującej się w pliku Web. config aplikacji):

```xml
<system.serviceModel>
    <serviceHostingEnvironment aspNetCompatibilityEnabled="true" />
</system.serviceModel>
```

Ta wartość jest domyślnie `false`, jeśli nie zostanie określona. Wartość `false` wskazuje, że wszystkie usługi WCF uruchomione w aplikacji nie będą działać w trybie zgodności ASP.NET.

Ponieważ tryb zgodności ASP.NET sugeruje semantykę przetwarzania żądań, które różnią się od domyślnych ustawień programu WCF, poszczególne implementacje usług mają możliwość kontrolowania, czy działają w aplikacji, dla której ASP.NET Włączono tryb zgodności. Usługi mogą używać <xref:System.ServiceModel.Activation.AspNetCompatibilityRequirementsAttribute>, aby wskazać, czy obsługują tryb zgodności ASP.NET. Wartość domyślna tego atrybutu to <xref:System.ServiceModel.Activation.AspNetCompatibilityRequirementsMode.Allowed>.

```csharp
[AspNetCompatibilityRequirements(RequirementsMode = AspNetCompatibilityRequirementsMode.Allowed)]
public class CalculatorService : ICalculatorSession
{//Implement calculator service methods.}
```

W poniższej tabeli przedstawiono sposób, w jaki ustawienia trybu zgodności w całej aplikacji współdziałają z określonym poziomem wsparcia dla poszczególnych usług:

|Ustawienie trybu zgodności dla całej aplikacji|[AspNetCompatibilityRequirementsMode]<br /><br /> Ustawienie|Obserwowany wynik|
|--------------------------------------------------|---------------------------------------------------------|---------------------|
|aspNetCompatibilityEnabled = "`true`"|<xref:System.ServiceModel.Activation.AspNetCompatibilityRequirementsMode.Required>|Usługa została aktywowana pomyślnie.|
|aspNetCompatibilityEnabled = "`true`"|<xref:System.ServiceModel.Activation.AspNetCompatibilityRequirementsMode.Allowed>|Usługa została aktywowana pomyślnie.|
|aspNetCompatibilityEnabled = "`true`"|<xref:System.ServiceModel.Activation.AspNetCompatibilityRequirementsMode.NotAllowed>|Gdy usługa otrzymuje komunikat, występuje błąd aktywacji.|
|aspNetCompatibilityEnabled = "`false`"|<xref:System.ServiceModel.Activation.AspNetCompatibilityRequirementsMode.Required>|Gdy usługa otrzymuje komunikat, występuje błąd aktywacji.|
|aspNetCompatibilityEnabled = "`false`"|<xref:System.ServiceModel.Activation.AspNetCompatibilityRequirementsMode.Allowed>|Usługa została aktywowana pomyślnie.|
|aspNetCompatibilityEnabled = "`false`"|<xref:System.ServiceModel.Activation.AspNetCompatibilityRequirementsMode.NotAllowed>|Usługa została aktywowana pomyślnie.|

> [!NOTE]
> Usługi IIS 7,0 i umożliwiają usługom WCF komunikowanie się za pośrednictwem protokołów innych niż HTTP. Jednak usługi WCF działające w aplikacjach z włączonym trybem zgodności ASP.NET nie mogą uwidaczniać punktów końcowych innych niż HTTP. Taka konfiguracja generuje wyjątek aktywacji, gdy usługa otrzymuje swój pierwszy komunikat.

Aby uzyskać więcej informacji na temat włączania trybu zgodności ASP.NET dla usług WCF, zobacz <xref:System.ServiceModel.Activation.AspNetCompatibilityRequirementsMode> i przykład [zgodności ASP.NET](../samples/aspnet-compatibility.md) .

## <a name="see-also"></a>Zobacz także

- <xref:System.ServiceModel.Activation.AspNetCompatibilityRequirementsAttribute>
- [Funkcje hostingu sieci szkieletowej aplikacji systemu Windows Server](https://docs.microsoft.com/previous-versions/appfabric/ee677189(v=azure.10))
