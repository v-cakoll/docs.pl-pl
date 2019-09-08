---
title: Środki zaradcze Renderowanie okna WPF
ms.date: 03/30/2017
ms.assetid: 28ed6bf8-141b-4b73-a4e3-44a99fae5084
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 13091c06561da24d2fc03f810fd8b8687b21d9a4
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/07/2019
ms.locfileid: "70789791"
---
# <a name="mitigation-wpf-window-rendering"></a>Środki zaradcze Renderowanie okna WPF

W .NET Framework 4,6 działający w systemie Windows 8 i nowszych całe okno jest renderowane bez przycinania, gdy rozciąga się poza pojedynczym ekranem w scenariuszu z obsługą kilku monitorów.

## <a name="impact"></a>Wpływ

Ogólnie rzecz biorąc, renderowanie całego okna na wielu monitorach bez wycinków jest oczekiwane zachowanie. Jednak w systemie Windows 7 i starszych wersjach Okna WPF są przycinane po przekroczeniu jednego ekranu, ponieważ renderowanie części okna na drugim monitorze ma znaczny wpływ na wydajność.

Dokładny wpływ renderowania systemu Windows WPF na monitory w systemie Windows 8 i nowszych nie jest precyzyjnie wymierny, ponieważ zależy on od dużej liczby czynników. W niektórych przypadkach może to spowodować niepożądane wpływ na wydajność, szczególnie w przypadku użytkowników, którzy uruchamiają aplikacje intensywnie korzystające z grafiki i mają monitory międzystrefowe systemu Windows. W innych przypadkach można po prostu chcieć mieć spójne zachowanie w wersjach .NET Framework.

## <a name="mitigation"></a>Ograniczenie

Tę zmianę można wyłączyć i przywrócić poprzednie zachowanie przycinania okna WPF, gdy wykracza poza pojedynczy ekran. Istnieją dwa sposoby wykonania tej czynności:

- Dodając `<EnableMultiMonitorDisplayClipping>` element `<appSettings>` do sekcji pliku konfiguracyjnego aplikacji, możesz wyłączyć lub włączyć to zachowanie w aplikacjach uruchomionych w systemie Windows 8 lub nowszym. Na przykład następująca sekcja konfiguracyjna wyłącza renderowanie bez przycinania:

  ```xml
  <appSettings>
      <add key="EnableMultiMonitorDisplayClipping" value="true"/>
    </appSettings>
  ```

  Ustawienie `<EnableMultiMonitorDisplayClipping>` konfiguracji może mieć jedną z dwóch wartości:

  - `true`, aby włączyć przycinanie systemu Windows do monitorowania granic podczas renderowania.

  - `false`, aby wyłączyć przycinanie okien do monitorowania granic podczas renderowania.

- Ustawiając <xref:System.Windows.CoreCompatibilityPreferences.EnableMultiMonitorDisplayClipping%2A> właściwość na `true` wartość przy uruchamianiu aplikacji.

## <a name="see-also"></a>Zobacz także

- [Zmiany środowiska uruchomieniowego](runtime-changes-in-the-net-framework-4-6.md)
