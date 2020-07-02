---
ms.openlocfilehash: b521f4163bf5bf4a369d0eec12dae503703a976e
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/01/2020
ms.locfileid: "85614646"
---
### <a name="throttle-concurrent-requests-per-session"></a>Ogranicz współbieżne żądania na sesję

#### <a name="details"></a>Szczegóły

W .NET Framework 4.6.2 i starszych ASP.NET wykonuje żądania z tym samym identyfikatorem sesji sekwencyjnie, a ASP.NET zawsze domyślnie wystawia identyfikator sesji za pomocą plików cookie. Jeśli odpowiedź strony zajmuje dużo czasu, znacznie obniży wydajność serwera, naciskając klawisz <kbd>F5</kbd> w przeglądarce. W ramach poprawki dodaliśmy licznik do śledzenia żądań umieszczonych w kolejce i kończy żądania po przekroczeniu określonego limitu. Wartość domyślna to 50. Jeśli limit zostanie osiągnięty, w dzienniku zdarzeń zostanie zarejestrowane ostrzeżenie, a odpowiedź HTTP 500 może zostać zarejestrowana w dzienniku usług IIS.

#### <a name="suggestion"></a>Sugestia

Aby przywrócić stare zachowanie, można dodać następujące ustawienie do pliku web.config, aby zrezygnować z nowego zachowania.

```xml
<appSettings>
    <add key="aspnet:RequestQueueLimitPerSession" value="2147483647"/>
</appSettings>
```

| Nazwa    | Wartość       |
|:--------|:------------|
| Zakres   | Brzeg        |
| Wersja | 4,7         |
| Typ    | Przekierowanie |
