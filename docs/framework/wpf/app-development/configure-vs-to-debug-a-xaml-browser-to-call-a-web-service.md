---
title: 'Instrukcje: Konfigurowanie w programie Visual Studio debugowania aplikacji przeglądarki XAML w celu wywoływania usługi internetowej'
ms.date: 03/30/2017
helpviewer_keywords:
- debugging XBAPs that call a Web service [WPF]
- debugging security exceptions for XBAPs [WPF]
- security exception for XBAPs [WPF], debugging
- configuring Visual Studio to debug XAML browser applications [WPF]
- configuring Visual Studio to debug XBAPs [WPF]
ms.assetid: fd1db082-a7bb-4c4b-9331-6ad74a0682d0
ms.openlocfilehash: e41dd46e4ddbdcde6448c68b4f9fb2e073baca43
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69958687"
---
# <a name="how-to-configure-visual-studio-to-debug-a-xaml-browser-application-to-call-a-web-service"></a>Instrukcje: Konfigurowanie w programie Visual Studio debugowania aplikacji przeglądarki XAML w celu wywoływania usługi internetowej
[!INCLUDE[TLA#tla_xbap#plural](../../../../includes/tlasharptla-xbapsharpplural-md.md)]Uruchom w obszarze piaskownicy zabezpieczeń częściowej relacji zaufania ograniczonego do zestawu stref internetowych uprawnień. Ten zestaw uprawnień ogranicza wywołania usługi sieci Web tylko do usług sieci Web, które znajdują [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)] się w lokacji źródłowej aplikacji. [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)] Gdy jest debugowany z programu Visual Studio 2005, chociaż nie jest uważany za taki sam, jak w przypadku usługi sieci Web, do której się odwołuje. Powoduje to, że wyjątki zabezpieczeń zostaną zgłoszone [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)] podczas próby wywołania usługi sieci Web. Jednak projekt programu Visual Studio 2005 [!INCLUDE[TLA#tla_wpfbrowserappproj](../../../../includes/tlasharptla-wpfbrowserappproj-md.md)] można skonfigurować w taki sposób, aby symulacja była taka sama jak usługa sieci Web, która wywołuje podczas debugowania. Pozwala [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)] to na bezpieczne Wywoływanie usługi sieci Web bez powodowania wyjątków zabezpieczeń.

## <a name="configuring-visual-studio"></a>Konfigurowanie programu Visual Studio
 Aby skonfigurować program Visual Studio 2005 do debugowania [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)] , który wywołuje usługę sieci Web:

1. Za pomocą projektu wybranego w **Eksploratora rozwiązań**na **projektu** menu, kliknij przycisk **właściwości**.

2. W **projektancie projektu**kliknij kartę **debugowanie** .

3. W sekcji **Akcja początkowa** wybierz pozycję **Uruchom program zewnętrzny** , a następnie wprowadź następujące polecenie:

     `C:\WINDOWS\System32\PresentationHost.exe`

4. W sekcji **Opcje uruchamiania** wprowadź następujące polecenie w polu tekstowym **argumenty wiersza polecenia** :

     `-debug`  *Nazwa pliku*

     Wartość *filename* parametru **-Debug** to plik. XBAP. na przykład:

     `-debug c:\example.xbap`

> [!NOTE]
> Jest to domyślna konfiguracja dla rozwiązań utworzonych przy użyciu szablonu projektu programu Visual Studio 2005 [!INCLUDE[TLA#tla_wpfbrowserappproj](../../../../includes/tlasharptla-wpfbrowserappproj-md.md)] .

1. Za pomocą projektu wybranego w **Eksploratora rozwiązań**na **projektu** menu, kliknij przycisk **właściwości**.

2. W **projektancie projektu**kliknij kartę **debugowanie** .

3. W sekcji **Opcje uruchamiania** Dodaj następujący parametr wiersza polecenia do pola tekstowego **argumenty wiersza polecenia** :

     `-debugSecurityZoneURL`  *ADRES URL*

     Wartość *adresu URL* dla [!INCLUDE[TLA#tla_url](../../../../includes/tlasharptla-url-md.md)] parametru **-debugSecurityZoneURL** jest dla lokalizacji, która ma zostać symulowana jako witryna źródłowa aplikacji.

 Rozważmy na [!INCLUDE[TLA#tla_xbap](../../../../includes/tlasharptla-xbap-md.md)] przykład, że program korzysta z usługi sieci Web z następującymi [!INCLUDE[TLA2#tla_url](../../../../includes/tla2sharptla-url-md.md)]czynnościami:

 `http://services.msdn.microsoft.com/ContentServices/ContentService.asmx`

 Lokacja pochodzenia [!INCLUDE[TLA2#tla_url](../../../../includes/tla2sharptla-url-md.md)] dla tej usługi sieci Web:

 `http://services.msdn.microsoft.com`

 W związku z tym parametr wiersza polecenia Complete **-debugSecurityZoneURL** ma wartość:

 `-debugSecurityZoneURL http://services.msdn.microsoft.com`

## <a name="see-also"></a>Zobacz także

- [Host WPF (PresentationHost.exe)](wpf-host-presentationhost-exe.md)
