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
ms.openlocfilehash: dcaabf9ecd47bc88095e92aa8ed28ad5f13fd1dc
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61757053"
---
# <a name="how-to-configure-visual-studio-to-debug-a-xaml-browser-application-to-call-a-web-service"></a>Instrukcje: Konfigurowanie w programie Visual Studio debugowania aplikacji przeglądarki XAML w celu wywoływania usługi internetowej
[!INCLUDE[TLA#tla_xbap#plural](../../../../includes/tlasharptla-xbapsharpplural-md.md)] są uruchamiane w piaskownicy zabezpieczeń częściowego zaufania, który jest ograniczony do zestaw uprawnień strefy Internet. Ten zestaw uprawnień ogranicza wywołania usługi sieci Web, aby tylko usług, które znajdują się w sieci Web [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)] aplikacji witryny pochodzenia. Gdy [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)] debugowania z programu Visual Studio 2005, jednak nie wydaje się mieć tej samej lokacji, z którego pochodzą, sieci Web obsługi odwołań. Wyjątki zabezpieczeń powoduje, że wywoływane, gdy [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)] próbuje wywołać usługę sieci Web. Jednak program Visual Studio 2005 [!INCLUDE[TLA#tla_wpfbrowserappproj](../../../../includes/tlasharptla-wpfbrowserappproj-md.md)] projektu można skonfigurować w celu symulowania o tej samej lokacji źródła jako usługę sieci Web wywoływanych przez nią podczas debugowania. Dzięki temu [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)] bezpiecznie wywołać usługę sieci Web bez powodowania wyjątki zabezpieczeń.

## <a name="configuring-visual-studio"></a>Konfigurowanie programu Visual Studio
 Aby skonfigurować program Visual Studio 2005 do debugowania [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)] który wywołuje usługę sieci Web:

1. Za pomocą projektu wybranego w **Eksploratora rozwiązań**na **projektu** menu, kliknij przycisk **właściwości**.

2. W **projektanta projektu**, kliknij przycisk **debugowania** kartę.

3. W **Akcja uruchamiania** zaznacz **uruchomienia programu zewnętrznego** i wprowadź następujące czynności:

     `C:\WINDOWS\System32\PresentationHost.exe`

4. W **opcje uruchamiania** sekcji, wprowadź następujące informacje w **argumenty wiersza polecenia** pola tekstowego:

     `-debug`  *Nazwa pliku*

     *Filename* wartość **-debug** parametru jest nazwą pliku XBAP; na przykład:

     `-debug c:\example.xbap`

> [!NOTE]
>  Jest to domyślna konfiguracja dla rozwiązania, które są tworzone za pomocą programu Visual Studio 2005 [!INCLUDE[TLA#tla_wpfbrowserappproj](../../../../includes/tlasharptla-wpfbrowserappproj-md.md)] szablonu projektu.

1. Za pomocą projektu wybranego w **Eksploratora rozwiązań**na **projektu** menu, kliknij przycisk **właściwości**.

2. W **projektanta projektu**, kliknij przycisk **debugowania** kartę.

3. W **opcje uruchamiania** sekcji, Dodaj następujący parametr wiersza polecenia, aby **argumenty wiersza polecenia** pola tekstowego:

     `-debugSecurityZoneURL`  *ADRES URL*

     *Adresu URL* wartość **- debugSecurityZoneURL** parametr [!INCLUDE[TLA#tla_url](../../../../includes/tlasharptla-url-md.md)] lokalizacji, z którym chcesz przeprowadzić symulację jako witryna pochodzenia aplikacji.

 Na przykład należy wziąć pod uwagę [!INCLUDE[TLA#tla_xbap](../../../../includes/tlasharptla-xbap-md.md)] używający usługi sieci Web z następującymi [!INCLUDE[TLA2#tla_url](../../../../includes/tla2sharptla-url-md.md)]:

 `http://services.msdn.microsoft.com/ContentServices/ContentService.asmx`

 Witryna pochodzenia [!INCLUDE[TLA2#tla_url](../../../../includes/tla2sharptla-url-md.md)] dla tej sieci Web service to:

 `http://services.msdn.microsoft.com`

 W związku z tym, pełne **- debugSecurityZoneURL** parametru wiersza polecenia, a wartość to:

 `-debugSecurityZoneURL http://services.msdn.microsoft.com`

## <a name="see-also"></a>Zobacz także

- [Host WPF (PresentationHost.exe)](wpf-host-presentationhost-exe.md)
