---
ms.openlocfilehash: 47d0aa554d88726caca35fa6bebe4d863fdc0695
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59804747"
---
### <a name="eventsourcewriteevent-impls-must-pass-writeevent-the-same-parameters-that-it-received-plus-id"></a>EventSource.WriteEvent impls należy przekazać WriteEvent tych samych parametrów, które otrzymał (plus identyfikator)

|   |   |
|---|---|
|Szczegóły|Środowisko wykonawcze wymusza teraz kontraktu, który określa następujące czynności: Klasa pochodząca z <xref:System.Diagnostics.Tracing.EventSource?displayProperty=name> definiujący ETW metody zdarzeń należy wywołać klasy bazowej <code>EventSource.WriteEvent</code> metody z Identyfikatorem zdarzenia następuje te same argumenty, które metody zdarzeń ETW został przekazany.|
|Sugestia|<xref:System.IndexOutOfRangeException?displayProperty=name> Wyjątek jest generowany, jeśli <xref:System.Diagnostics.Tracing.EventListener?displayProperty=name> odczytuje <xref:System.Diagnostics.Tracing.EventSource?displayProperty=name> danych w procesie dla źródła zdarzenia, który narusza aktualne niniejszej Umowy.|
|Zakres|Mały|
|Wersja|4.5.1|
|Typ|Środowisko uruchomieniowe|
