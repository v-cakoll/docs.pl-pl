---
ms.openlocfilehash: 3463b6c45952aab0023e40921739e84eb51ca001
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "67859150"
---
### <a name="wpf-pointer-based-touch-stack"></a>Stos dotykowy oparty na wskaźniku WPF

|   |   |
|---|---|
|Szczegóły|Ta zmiana dodaje możliwość włączenia opcjonalnego WM_POINTER oparty na WPF touch/pisaka stosu.  Deweloperzy, którzy nie jawnie włączyć to powinno zobaczyć żadnych zmian w WPF touch/pisak zachowanie. Bieżące znane problemy z opcjonalnym WM_POINTER stosem dotykowym/rysikowym:<ul><li>Brak obsługi pisma oduniającego w czasie rzeczywistym.</li><li>Podczas odkowania i stylusPlugins będzie nadal działać, będą one przetwarzane w wątku interfejsu użytkownika, co może prowadzić do niskiej wydajności.</li><li>Zmiany w zachowaniu spowodowane zmianami w promocji ze zdarzeń dotykowych/pisaka na zdarzenia myszy</li><li>Manipulacja może zachowywać się inaczej</li><li>Przeciąganie/upuszczanie nie będzie wyświetlane odpowiednie informacje zwrotne dla wprowadzania dotykowego</li><li>Nie ma to wpływu na wprowadzanie rysika</li><li>Przeciągania/Upuszczania nie można już inicjować podczas zdarzeń dotykowych/pisaka</li><li>Może to potencjalnie zawiesić aplikację do momentu wykrycia danych wejściowych myszy.</li><li>Zamiast tego deweloperzy powinni zainicjować przeciąganie i upuszczanie ze zdarzeń myszy.</li></ul>|
|Sugestia|Deweloperzy, którzy chcą włączyć ten stos, mogą dodawać/scalać następujące elementy do pliku App.config aplikacji:<pre><code class="lang-xml">&lt;configuration&gt;&#13;&#10;&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.System.Windows.Input.Stylus.EnablePointerSupport=true&quot;/&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;&lt;/configuration&gt;&#13;&#10;</code></pre>Usunięcie tej wartości lub ustawienie wartości false spowoduje wyłączenie tego opcjonalnego stosu. Należy pamiętać, że ten stos jest dostępny tylko w systemie Windows 10 Creators Update i powyżej.|
|Zakres|Brzeg|
|Wersja|4.7|
|Typ|Przekierowanie|
