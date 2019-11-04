---
title: Jak konfigurować Visual Studio, aby debugować aplikację przeglądarki XAML i wywołać usługę sieci Web
ms.date: 03/30/2017
helpviewer_keywords:
- debugging XBAPs that call a Web service [WPF]
- debugging security exceptions for XBAPs [WPF]
- security exception for XBAPs [WPF], debugging
- configuring Visual Studio to debug XAML browser applications [WPF]
- configuring Visual Studio to debug XBAPs [WPF]
ms.assetid: fd1db082-a7bb-4c4b-9331-6ad74a0682d0
ms.openlocfilehash: d8cfae2fb47876d578c51e5f4acdfe0c31e752fe
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/03/2019
ms.locfileid: "73460903"
---
# <a name="how-to-configure-visual-studio-to-debug-a-xaml-browser-application-to-call-a-web-service"></a>Jak konfigurować Visual Studio, aby debugować aplikację przeglądarki XAML i wywołać usługę sieci Web
Aplikacje przeglądarki XAML (XBAP) działają w obszarze piaskownicy zabezpieczeń częściowej relacji zaufania ograniczonego do zestawu stref internetowych uprawnień. Ten zestaw uprawnień ogranicza wywołania usługi sieci Web tylko do usług sieci Web, które znajdują się w lokacji aplikacji XBAP. Gdy XBAP jest debugowany z programu Visual Studio 2005, chociaż nie jest uważany za taki sam, jak w przypadku usługi sieci Web, do której się odwołuje. Powoduje to, że wyjątki zabezpieczeń mają być zgłaszane, gdy usługa XBAP próbuje wywołać usługę sieci Web. Jednak projekt aplikacji przeglądarki XAML programu Visual Studio 2005 (WPF) można skonfigurować w taki sposób, aby symulowanie posiadania tego samego miejsca pochodzenia jako usługi sieci Web, która wywołuje podczas debugowania. Umożliwia to aplikacji XBAP bezpieczne Wywoływanie usługi sieci Web bez powodowania wyjątków zabezpieczeń.

## <a name="configuring-visual-studio"></a>Konfigurowanie programu Visual Studio
 Aby skonfigurować program Visual Studio 2005 do debugowania aplikacji XBAP wywołującej usługę sieci Web:

1. Po wybraniu projektu w **Eksplorator rozwiązań**, w menu **projekt** kliknij polecenie **Właściwości**.

2. W **projektancie projektu**kliknij kartę **debugowanie** .

3. W sekcji **Akcja początkowa** wybierz pozycję **Uruchom program zewnętrzny** , a następnie wprowadź następujące polecenie:

     `C:\WINDOWS\System32\PresentationHost.exe`

4. W sekcji **Opcje uruchamiania** wprowadź następujące polecenie w polu tekstowym **argumenty wiersza polecenia** :

     *Nazwa pliku* `-debug`

     Wartość *filename* parametru **-Debug** to plik. XBAP. na przykład:

     `-debug c:\example.xbap`

> [!NOTE]
> Jest to konfiguracja domyślna dla rozwiązań utworzonych za pomocą szablonu projektu programu Visual Studio 2005 XAML Browser (WPF).

1. Po wybraniu projektu w **Eksplorator rozwiązań**, w menu **projekt** kliknij polecenie **Właściwości**.

2. W **projektancie projektu**kliknij kartę **debugowanie** .

3. W sekcji **Opcje uruchamiania** Dodaj następujący parametr wiersza polecenia do pola tekstowego **argumenty wiersza polecenia** :

     *adres URL* `-debugSecurityZoneURL`

     Wartość *adresu URL* dla parametru **-debugSecurityZoneURL** jest adresem URL lokalizacji, która ma być symulowana jako witryna pochodzenia aplikacji.

 Przykładowo Rozważmy aplikację przeglądarki XAML (XBAP), która używa usługi sieci Web z następującym adresem URL:

 `http://services.msdn.microsoft.com/ContentServices/ContentService.asmx`

 Witryna adresu URL źródła dla tej usługi sieci Web:

 `http://services.msdn.microsoft.com`

 W związku z tym parametr wiersza polecenia Complete **-debugSecurityZoneURL** ma wartość:

 `-debugSecurityZoneURL http://services.msdn.microsoft.com`

## <a name="see-also"></a>Zobacz także

- [Host WPF (PresentationHost.exe)](wpf-host-presentationhost-exe.md)
