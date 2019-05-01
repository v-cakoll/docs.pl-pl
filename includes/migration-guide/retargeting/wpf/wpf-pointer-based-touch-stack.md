---
ms.openlocfilehash: 3463b6c45952aab0023e40921739e84eb51ca001
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61759515"
---
### <a name="wpf-pointer-based-touch-stack"></a>WPF Pointer-Based Touch Stack

|   |   |
|---|---|
|Szczegóły|Ta zmiana dodaje możliwość włączenia opcjonalne WM_POINTER oparty na protokole stosu dotyk/pióro WPF.  Deweloperów, którzy nie jawnie włączyć ten powinien zostać wyświetlony bez zmian w zachowaniu dotyk/pióro WPF. Bieżący znane problemy z opcjonalnych WM_POINTER na podstawie dotyk/pióro stosu:<ul><li>Brak obsługi pisma odręcznego w czasie rzeczywistym.</li><li>Podczas pisania odręcznego i stylusplugins — będą nadal działać, zostanie przetworzone w wątku interfejsu użytkownika, co może prowadzić do pogorszenia wydajności.</li><li>Zmiany zachowania z powodu zmian w ramach podwyższenia poziomu dotyk/pióro zdarzeń do zdarzenia myszy</li><li>Manipulowanie może zachowywać się inaczej</li><li>Przeciągnij/upuść będą wyświetlały odpowiednią opinię dotyczącą wprowadzanie dotykowe</li><li>Nie ma to wpływu na wejście pióra</li><li>Już nie można zainicjować przeciągania i upuszczania zdarzeń dotyk/pióra</li><li>To potencjalnie zawieszanie aplikacji, dopóki nie zostanie wykryte wejście myszy.</li><li>Zamiast tego deweloperów należy zainicjować przeciągnij i upuść z zdarzeń myszy.</li></ul>|
|Sugestia|Deweloperzy, którzy chcą włączyć ten stos można dodać/merge następujące polecenie, aby ich stosowania pliku App.config:<pre><code class="lang-xml">&lt;configuration&gt;&#13;&#10;&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.System.Windows.Input.Stylus.EnablePointerSupport=true&quot;/&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;&lt;/configuration&gt;&#13;&#10;</code></pre>Usunięcie tej lub ustawienie wartości FALSE spowoduje wyłączenie tego stosu opcjonalne. Należy pamiętać, że ten stos jest dostępna tylko w systemie Windows 10 Creators Update i nowszych.|
|Zakres|Krawędź|
|Wersja|4.7|
|Typ|Przekierowanie|
