---
ms.openlocfilehash: bb3d7c1afa9e506ffc7c6d068c48428d1e66ccb6
ms.sourcegitcommit: 4735bb7741555bcb870d7b42964d3774f4897a6e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/30/2019
ms.locfileid: "66379453"
---
### <a name="wpf-pointer-based-touch-stack"></a>WPF Pointer-Based Touch Stack

|   |   |
|---|---|
|Szczegóły|Ta zmiana dodaje możliwość włączenia opcjonalne WM_POINTER oparty na protokole stosu dotyk/pióro WPF.  Deweloperów, którzy nie jawnie włączyć ten powinien zostać wyświetlony bez zmian w zachowaniu dotyk/pióro WPF. Bieżący znane problemy z opcjonalnych WM_POINTER na podstawie dotyk/pióro stosu:<ul><li>Brak obsługi pisma odręcznego w czasie rzeczywistym.</li><li>Podczas pisania odręcznego i stylusplugins — będą nadal działać, zostanie przetworzone w wątku interfejsu użytkownika, co może prowadzić do pogorszenia wydajności.</li><li>Zmiany zachowania z powodu zmian w ramach podwyższenia poziomu dotyk/pióro zdarzeń do zdarzenia myszy</li><li>Manipulowanie może zachowywać się inaczej</li><li>Przeciągnij/upuść będą wyświetlały odpowiednią opinię dotyczącą wprowadzanie dotykowe</li><li>Nie ma to wpływu na wejście pióra</li><li>Już nie można zainicjować przeciągania i upuszczania zdarzeń dotyk/pióra</li><li>Może to teoretycznie spowodować aplikacja przestanie odpowiadać, dopóki nie zostanie wykryte wejście myszy.</li><li>Zamiast tego deweloperów należy zainicjować przeciągnij i upuść z zdarzeń myszy.</li></ul>|
|Sugestia|Deweloperzy, którzy chcą włączyć ten stos można dodać/merge następujące polecenie, aby ich stosowania pliku App.config:<pre><code class="lang-xml">&lt;configuration&gt;&#13;&#10;&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.System.Windows.Input.Stylus.EnablePointerSupport=true&quot;/&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;&lt;/configuration&gt;&#13;&#10;</code></pre>Usunięcie tej lub ustawienie wartości FALSE spowoduje wyłączenie tego stosu opcjonalne. Należy pamiętać, że ten stos jest dostępna tylko w systemie Windows 10 Creators Update i nowszych.|
|Scope|Krawędź|
|Wersja|4.7|
|Typ|Przekierowanie|
