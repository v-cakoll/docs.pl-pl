---
title: Wdrażanie aplikacji
ms.date: 03/30/2017
helpviewer_keywords:
- WPF applications [WPF], deployment
- deployment [WPF], applications
ms.assetid: 12cadca0-b32c-4064-9a56-e6a306dcc76d
ms.openlocfilehash: 54d14503a0f65bb50f2dfb14d40af3b47d51589c
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79186311"
---
# <a name="deploy-a-wpf-application"></a>Wdrażanie aplikacji WPF

Po windows presentation foundation (WPF) aplikacje są tworzone, muszą być wdrożone. Systemy Windows i .NET Framework zawierają kilka technologii wdrażania. Technologia wdrażania, który jest używany do wdrażania aplikacji WPF zależy od typu aplikacji. W tym temacie przedstawiono krótkie omówienie każdej technologii wdrażania i jak są one używane w połączeniu z wymaganiami dotyczącymi wdrażania każdego typu aplikacji WPF.

<a name="Deployment_Technologies"></a>
## <a name="deployment-technologies"></a>Technologie wdrażania  
 Systemy Windows i program .NET Framework obejmują kilka technologii wdrażania, w tym:  
  
- XCopy wdrożenia.  
  
- Wdrożenie Instalatora Windows.  
  
- Kliknij pozycjęWładne wdrożenie.  
  
<a name="XCopy_Deployment"></a>
### <a name="xcopy-deployment"></a>Wdrożenie XCopy  
 Wdrożenie XCopy odnosi się do używania programu wiersza polecenia XCopy do kopiowania plików z jednej lokalizacji do drugiej. Wdrożenie XCopy jest odpowiednie w następujących okolicznościach:  
  
- Aplikacja jest niezależna. Nie trzeba aktualizować klienta, aby uruchomić.  
  
- Pliki aplikacji muszą zostać przeniesione z jednej lokalizacji do innej, na przykład z lokalizacji kompilacji (dysk lokalny, udział plików UNC itd.) do lokalizacji publikowania (witryny sieci Web, udziału plików UNC itd.).  
  
- Aplikacja nie wymaga integracji powłoki (skrót menu Start, ikona pulpitu i tak dalej).  
  
 Mimo że XCopy nadaje się do prostych scenariuszy wdrażania, jest ograniczona, gdy wymagane są bardziej złożone możliwości wdrażania. W szczególności przy użyciu XCopy często ponosi obciążenie dla tworzenia, wykonywania i obsługi skryptów do zarządzania wdrożeniem w niezawodny sposób. Ponadto XCopy nie obsługuje przechowywania wersji, dezinstalacji ani wycofywania.  
  
<a name="Windows_Installer"></a>
### <a name="windows-installer"></a>Instalator Windows  
 Instalator Windows umożliwia pakowanie aplikacji jako samodzielnych plików wykonywalnych, które można łatwo dystrybuować do klientów i uruchamiać. Ponadto Instalator Windows jest zainstalowany z systemem Windows i umożliwia integrację z pulpitem, menu Start i panelem sterowania Programy.  
  
 Instalator Windows upraszcza instalację i dezinstalację aplikacji, ale nie zapewnia urządzeń zapewniających, że zainstalowane aplikacje są aktualizowane z punktu widzenia przechowywania wersji.  
  
 Aby uzyskać więcej informacji na temat Instalatora Windows, zobacz [Wdrażanie Instalatora Windows](/visualstudio/deployment/deploying-applications-services-and-components#create-an-installer-package-windows-desktop).
  
<a name="ClickOnce_Deployment"></a>
### <a name="clickonce-deployment"></a>Wdrożenie clickonce  
 ClickOnce umożliwia wdrażanie aplikacji w stylu sieci Web dla aplikacji innych niż sieci Web. Aplikacje są publikowane i wdrażane z serwerów sieci Web lub plików. Mimo że ClickOnce nie obsługuje pełnego zakresu funkcji klienta, które robią aplikacje zainstalowane przez Instalatora Windows, obsługuje podzbiór, który zawiera następujące elementy:  
  
- Integracja z menu Start i panelem sterowania Programy.  
  
- Przechowywanie wersji, wycofywanie i dezinstalacja.  
  
- Tryb instalacji online, który zawsze uruchamia aplikację z lokalizacji wdrażania.  
  
- Automatyczne aktualizowanie po wydaniu nowych wersji.  
  
- Rejestracja rozszerzeń plików.  
  
 Aby uzyskać więcej informacji na temat ClickOnce, zobacz [ClickOnce Security and Deployment](/visualstudio/deployment/clickonce-security-and-deployment).  
  
<a name="Deploying_WPF_Applications"></a>
## <a name="deploying-wpf-applications"></a>Wdrażanie aplikacji WPF  
 Opcje wdrażania aplikacji WPF zależą od typu aplikacji. Z punktu widzenia wdrożenia WPF WPF ma trzy istotne typy aplikacji:  
  
- Aplikacje autonomiczne.  
  
- Aplikacje tylko [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] do znaczników.  
  
- aplikacje przeglądarki XAML (XBAPs).  
  
<a name="Deploying_Standalone_Applications"></a>
### <a name="deploying-standalone-applications"></a>Wdrażanie aplikacji autonomicznych  
 Aplikacje autonomiczne są wdrażane przy użyciu funkcji ClickOnce lub Instalatora Windows. Tak czy inaczej, autonomiczne aplikacje wymagają pełnego zaufania do uruchomienia. Pełne zaufanie jest automatycznie przyznawane autonomicznym aplikacjom, które są wdrażane przy użyciu Instalatora Windows. Autonomiczne aplikacje, które są wdrażane przy użyciu ClickOnce nie są automatycznie przyznane pełne zaufanie. Zamiast tego ClickOnce wyświetla okno dialogowe z ostrzeżeniem o zabezpieczeniach, które użytkownicy muszą zaakceptować przed zainstalowaniem aplikacji autonomicznej. Jeśli zostanie zaakceptowana, aplikacja autonomiczna jest zainstalowana i obdarowana pełnym zaufaniem. Jeśli nie, aplikacja autonomiczna nie jest zainstalowana.  
  
<a name="Deploying_Markup_Only_XAML_Applications"></a>
### <a name="deploying-markup-only-xaml-applications"></a>Wdrażanie aplikacji XAML tylko do znaczników  
 Strony tylko [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] do oznaczania są zwykle publikowane na serwerach sieci Web, takich jak strony HTML, i mogą być przeglądane za pomocą programu Internet Explorer. Strony tylko [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] do oznaczania są uruchamiane w obszarze izolowanym z częściowym zabezpieczeniem z ograniczeniami zdefiniowanymi przez ustawiony zestaw uprawnień strefy internetowej. Zapewnia to równoważne zabezpieczenia izolowania do aplikacji sieci Web opartych na języku HTML.  
  
 Aby uzyskać więcej informacji na temat zabezpieczeń aplikacji WPF, zobacz [Zabezpieczenia](../security-wpf.md).  
  
 Strony tylko [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] do oznaczania można zainstalować w lokalnym systemie plików za pomocą xcopy lub Instalatora Windows. Te strony można przeglądać za pomocą programu Internet Explorer lub Eksploratora Windows.  
  
 Aby uzyskać więcej informacji na temat xaml, zobacz [Omówienie XAML (WPF)](../../../desktop-wpf/fundamentals/xaml.md).  
  
<a name="Deploying_XAML_Browser_Applications"></a>
### <a name="deploying-xaml-browser-applications"></a>Wdrażanie aplikacji przeglądarki XAML  
 XBAPs są skompilowane aplikacje, które wymagają następujących trzech plików do wdrożenia:  
  
- *Nazwa aplikacji*.exe: Plik aplikacji zestawu wykonywalnego.  
  
- *Nazwa aplikacji*.xbap: Manifest wdrożenia.  
  
- *Nazwa aplikacji*.exe.manifest: Manifest aplikacji.  
  
> [!NOTE]
> Aby uzyskać więcej informacji na temat manifestów wdrażania i aplikacji, zobacz [Tworzenie aplikacji WPF](building-a-wpf-application-wpf.md).  
  
 Pliki te są produkowane, gdy XBAP jest zbudowany. Aby uzyskać więcej informacji, zobacz [Jak: Tworzenie nowego projektu aplikacji przeglądarki WPF](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/bb628663(v=vs.100)). Podobnie jak strony [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] tylko do znaczników, XBAPs są zazwyczaj publikowane na serwerze sieci Web i wyświetlane przy użyciu programu Internet Explorer.  
  
 XBAPs można wdrożyć na klientach przy użyciu dowolnej z technik wdrażania. Jednak ClickOnce jest zalecane, ponieważ zapewnia następujące możliwości:  
  
1. Automatyczne aktualizacje po opublikowaniu nowej wersji.  
  
2. Uprawnienia podniesienia uprawnień dla XBAP działającego z pełnym zaufaniem.  
  
 Domyślnie ClickOnce publikuje pliki aplikacji z rozszerzeniem .deploy. Może to być problematyczne, ale można je wyłączyć. Aby uzyskać więcej informacji, zobacz [Problemy z konfiguracją serwera i klienta w przypadku wdrożeń ClickOnce](/visualstudio/deployment/server-and-client-configuration-issues-in-clickonce-deployments).  
  
 Aby uzyskać więcej informacji na temat wdrażania aplikacji przeglądarki XAML (XBAPs), zobacz [Omówienie aplikacji przeglądarki WPF XAML](wpf-xaml-browser-applications-overview.md).  
  
<a name="Installing__NET_Framework_3_0"></a>
## <a name="installing-the-net-framework"></a>Instalowanie programu .NET Framework  
 Aby uruchomić aplikację WPF, program Microsoft .NET Framework musi być zainstalowany na kliencie. Program Internet Explorer automatycznie wykrywa, czy klienci są instalowani z programem .NET Framework podczas wyświetlania aplikacji hostowanych przez przeglądarkę WPF. Jeśli program .NET Framework nie jest zainstalowany, program Internet Explorer monituje użytkowników o jej zainstalowanie.  
  
 Aby wykryć, czy program .NET Framework jest zainstalowany, program Internet Explorer zawiera aplikację programu inipulacyjnego zarejestrowaną jako program obsługi zbiorczych wielozadaniowych rozszerzeń poczty internetowej (MIME) dla plików zawartości z następującymi rozszerzeniami: .xaml, xps, .xbap i .application. Jeśli przejdziesz do tych typów plików, a program .NET Framework nie zostanie zainstalowany na kliencie, aplikacja programu inichowania żąda uprawnień do jej zainstalowania. Jeśli uprawnienie nie zostanie udzielone, nie jest zainstalowany program .NET Framework ani aplikacja.  
  
 Jeśli uprawnienie zostanie udzielone, program Internet Explorer pobierze i zainstaluje program .NET Framework przy użyciu usługi inteligentnego transferu w tle firmy Microsoft (BITS). Po pomyślnej instalacji programu .NET Framework pierwotnie żądany plik jest otwierany w nowym oknie przeglądarki.  
  
 Aby uzyskać więcej informacji, zobacz [Wdrażanie programu .NET Framework i aplikacji](../../deployment/index.md).  
  
## <a name="see-also"></a>Zobacz też

- [Kompilowanie aplikacji WPF](building-a-wpf-application-wpf.md)
- [Zabezpieczenia](../security-wpf.md)
