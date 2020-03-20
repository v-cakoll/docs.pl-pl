---
title: 'Ograniczenie: renderowanie okien WPF'
ms.date: 03/30/2017
ms.assetid: 28ed6bf8-141b-4b73-a4e3-44a99fae5084
ms.openlocfilehash: 42d6abf1ba6ed7c17a5a5604e98b5ee46d0c3ac2
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "73457768"
---
# <a name="mitigation-wpf-window-rendering"></a>Ograniczenie: renderowanie okien WPF

W programie .NET Framework 4.6 działającym w systemie Windows 8 i wyższym całe okno jest renderowane bez przycinania, gdy rozciąga się poza pojedynczym ekranem w scenariuszu z wieloma monitorami.

## <a name="impact"></a>Wpływ

Ogólnie rzecz biorąc renderowanie całego okna na wielu monitorach bez przycinania jest oczekiwanym zachowaniem. Jednak w systemie Windows 7 i wcześniejszych wersjach okna WPF są przycinane, gdy wykraczają poza jeden ekran, ponieważ renderowanie części okna na drugim monitorze ma znaczący wpływ na wydajność.

Dokładny wpływ renderowania okien WPF na monitorach w systemie Windows 8 i powyżej nie jest dokładnie wymierny, ponieważ zależy od dużej liczby czynników. W niektórych przypadkach może nadal powodować niepożądany wpływ na wydajność, szczególnie dla użytkowników, którzy uruchamiają aplikacje wymagające dużej ilości grafiki i mają monitory międzystrefowe systemu Windows. W innych przypadkach może po prostu chcesz spójne zachowanie w wersjach programu .NET Framework.

## <a name="mitigation"></a>Środki zaradcze

Można wyłączyć tę zmianę i przywrócić poprzednie zachowanie przycinania okna WPF, gdy wykracza poza jeden ekran. Istnieją dwa sposoby wykonania tej czynności:

- Dodając `<EnableMultiMonitorDisplayClipping>` element do `<appSettings>` sekcji pliku konfiguracji aplikacji, można wyłączyć lub włączyć to zachowanie w aplikacjach działających w systemie Windows 8 lub nowszym. Na przykład następująca sekcja konfiguracji wyłącza renderowanie bez przycinania:

  ```xml
  <appSettings>
      <add key="EnableMultiMonitorDisplayClipping" value="true"/>
    </appSettings>
  ```

  Ustawienie `<EnableMultiMonitorDisplayClipping>` konfiguracji może mieć jedną z dwóch wartości:

  - `true`, aby umożliwić przycinanie okien w celu monitorowania granic podczas renderowania.

  - `false`, aby wyłączyć przycinanie okien w celu monitorowania granic podczas renderowania.

- Ustawiając <xref:System.Windows.CoreCompatibilityPreferences.EnableMultiMonitorDisplayClipping%2A> właściwość `true` przy uruchamianiu aplikacji.

## <a name="see-also"></a>Zobacz też

- [Zgodność aplikacji](application-compatibility.md)
